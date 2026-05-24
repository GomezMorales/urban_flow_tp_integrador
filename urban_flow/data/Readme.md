
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
