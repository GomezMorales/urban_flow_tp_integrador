
# Conclusiones — Sprint 2

## Relación entre imágenes y datos

El sistema analiza multas de Vaalserberg cruzando registros
administrativos con evidencia visual obtenida por OCR sobre
imágenes procesadas con filtro Canny.

No todas las multas cuentan con imagen asociada, lo que
refleja que no cada radar captura evidencia fotográfica
utilizable en cada evento de infracción.

La tasa de match del OCR sobre imágenes Canny es parcial:
el preprocesamiento resalta bordes pero puede distorsionar
caracteres (confusión entre 'O' y '0', 'I' y '1'), lo que
limita la precisión del reconocimiento automático.

De las multas en estado IMPAGA, solo una fracción cuenta
con evidencia visual validada, lo que representa un desafío
para su resolución administrativa o judicial.

Una mejora futura consiste en aplicar cierre morfológico
previo al OCR para fusionar regiones de texto en la patente,
y filtrar contornos por relación de aspecto (ancho/alto
entre 2 y 5), reduciendo el ruido antes del reconocimiento.

# Conclusiones — Sprint 2

## Relación entre imágenes y datos

El sistema analiza multas de Vaalserberg cruzando registros
administrativos con evidencia visual obtenida por OCR sobre
imágenes procesadas con filtro Canny.

No todas las multas cuentan con imagen asociada, lo que
refleja que no cada radar captura evidencia fotográfica
utilizable en cada evento de infracción.

La tasa de match del OCR sobre imágenes Canny es parcial:
el preprocesamiento resalta bordes pero puede distorsionar
caracteres (confusión entre 'O' y '0', 'I' y '1'), lo que
limita la precisión del reconocimiento automático.

De las multas en estado IMPAGA, solo una fracción cuenta
con evidencia visual validada, lo que representa un desafío
para su resolución administrativa o judicial.

Una mejora futura consiste en aplicar cierre morfológico
previo al OCR para fusionar regiones de texto en la patente,
y filtrar contornos por relación de aspecto (ancho/alto
entre 2 y 5), reduciendo el ruido antes del reconocimiento.

# Conclusiones — Sprint 2

## Relación entre imágenes y datos

El sistema analiza multas de Vaalserberg cruzando registros
administrativos con evidencia visual obtenida por OCR sobre
imágenes procesadas con filtro Canny.

No todas las multas cuentan con imagen asociada, lo que
refleja que no cada radar captura evidencia fotográfica
utilizable en cada evento de infracción.

La tasa de match del OCR sobre imágenes Canny es parcial:
el preprocesamiento resalta bordes pero puede distorsionar
caracteres (confusión entre 'O' y '0', 'I' y '1'), lo que
limita la precisión del reconocimiento automático.

De las multas en estado IMPAGA, solo una fracción cuenta
con evidencia visual validada, lo que representa un desafío
para su resolución administrativa o judicial.

Una mejora futura consiste en aplicar cierre morfológico
previo al OCR para fusionar regiones de texto en la patente,
y filtrar contornos por relación de aspecto (ancho/alto
entre 2 y 5), reduciendo el ruido antes del reconocimiento.

# Conclusiones — Sprint 2

## Relación entre imágenes y datos

El sistema analiza multas de Vaalserberg cruzando registros
administrativos con evidencia visual obtenida por OCR sobre
imágenes procesadas con filtro Canny.

No todas las multas cuentan con imagen asociada, lo que
refleja que no cada radar captura evidencia fotográfica
utilizable en cada evento de infracción.

La tasa de match del OCR sobre imágenes Canny es parcial:
el preprocesamiento resalta bordes pero puede distorsionar
caracteres (confusión entre 'O' y '0', 'I' y '1'), lo que
limita la precisión del reconocimiento automático.

De las multas en estado IMPAGA, solo una fracción cuenta
con evidencia visual validada, lo que representa un desafío
para su resolución administrativa o judicial.

Una mejora futura consiste en aplicar cierre morfológico
previo al OCR para fusionar regiones de texto en la patente,
y filtrar contornos por relación de aspecto (ancho/alto
entre 2 y 5), reduciendo el ruido antes del reconocimiento.

# Conclusiones — Sprint 3

## Resumen del trabajo desarrollado

En este sprint se consolidó el pipeline de datos de Urban Flow,
pasando de un manejo basado en archivos a una arquitectura con
versionado, persistencia relacional y búsqueda vectorial.

El versionado se separó en dos planos: Git para el código y los
punteros livianos, y DVC para los binarios pesados (imágenes), con
un remote local como respaldo. Esta separación evita inflar el
repositorio con archivos grandes y permite reconstruir cualquier
estado de los datos.

Sobre el modelo de dominio se definió un modelo relacional con
SQLAlchemy (Vehiculo, Radar, Multa y Evidencia) y se pobló la base
`transito` a partir del CSV procesado. Luego se implementaron
consultas analíticas (reincidencia, radares más activos, multas sin
evidencia, confirmación visual) que demuestran el valor de tener los
datos normalizados en un motor relacional.

Finalmente se incorporó una capa de búsqueda por similitud visual:
los embeddings de las patentes se generaron con OpenCLIP y se
almacenaron en ChromaDB, vinculando cada vector a su vehículo. La
función `buscar_patente_imagen` combina ambos mundos: recupera la
patente más cercana en la base vectorial y completa los datos desde
la base relacional.

## Análisis crítico

El sistema funciona de extremo a extremo, pero el análisis dejó al
descubierto una limitación que se origina en etapas previas. El OCR
del Sprint 2 se ejecutó sobre las imágenes de patentes y solo
el 23% superó el umbral de match del 80%. El reconocimiento de
caracteres tuvo una tasa de acierto baja, con lecturas que agregaban
o perdían caracteres respecto de la patente real. Como consecuencia,
la base de datos quedó con apenas 20 evidencias, y la base vectorial
heredó ese volumen reducido.

Esa decisión temprana se propagó hasta la búsqueda vectorial. Al
validar `buscar_patente_imagen` con las imágenes originales a color,
las distancias resultaron altas (cercanas a 1.0), porque la colección
fue poblada con imágenes Canny y los embeddings de una imagen a color
y su versión Canny no son comparables. Al repetir la validación con
imágenes Canny —el mismo dominio que se almacenó— las distancias
bajaron a 0.0 con la patente correcta, confirmando que la lógica de
búsqueda es correcta y que la limitación está en el tipo de imagen.

## Mejoras propuestas

El punto más claro que dejaron las pruebas es la importancia de la
consistencia: la base vectorial debe poblarse y consultarse siempre
con el mismo tipo de imagen. En la validación, las consultas con
imágenes del mismo dominio que el almacenado dieron coincidencia
exacta, mientras que mezclar dominios distintos produjo distancias
altas. Garantizar esa coherencia entre lo que se almacena y lo que
se consulta es la condición mínima para que la búsqueda por
similitud sea confiable. Una forma de lograrlo, sin alterar lo ya
almacenado, sería aplicar a la imagen de consulta el mismo
preprocesamiento que atravesaron las imágenes de la base (escala de
grises, blur y Canny) antes de generar su embedding, de modo que
ambas queden en el mismo dominio.

Más allá de eso, sería valioso revisar la estrategia de
preprocesamiento de imágenes (escala de grises, blur, Canny) usada en
etapas previas. La baja tasa de reconocimiento del OCR sugiere que
vale la pena experimentar con distintas combinaciones de filtros y
comparar sus resultados, en lugar de asumir que la cadena actual es la
óptima. No se midió cuál preprocesamiento rinde mejor ni para el OCR
ni para los embeddings, de modo que esto queda como una línea de
trabajo a evaluar empíricamente en futuras iteraciones.
