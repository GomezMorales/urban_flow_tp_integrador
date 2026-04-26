# CHANGELOG - Urban Flow

## [2026-04-18] - Día 1 de Trabajo

### Ejercicio 01: Configuración del Entorno y Versionado
- **Inicialización:** Creación del repositorio y rama de trabajo `Sprint_1`.
- **Estructura:** Implementación de la jerarquía de directorios `urban_flow/data/` (raw, interim, processed).
- **Documentación:** Redacción de `README.md` con contexto histórico y `CHANGELOG.md` para traceo de cambios.
- **Configuración:** Ajuste del Notebook base con los nombres de los integrantes y configuración de sangría a 2 espacios.

---

## [2026-04-20] - Día 2 de Trabajo

### Ejercicio 02: Gestión de Datos Raw
- **Descarga:** Implementación de lógica de descarga automática y verificación de existencia de `speeding_fines.csv`.
- **Análisis Inicial:** Carga del dataset, visualización de primeras filas y diagnóstico de tipos de datos.

### Infraestructura y Portabilidad
- **Gestión de Dependencias:** Se optó por la instalación directa de librerías mediante `%pip` en la celda inicial del Notebook para garantizar la ejecución "out-of-the-box" en Google Colab sin depender de archivos externos.
- **Compatibilidad:** Implementación de configuración dinámica para detección de entornos (Colab/Codespaces) y clonación automática del repositorio.

### Ejercicio 03: Normalización y limpieza del dataset en fase RAW
- **Normalización de columnas:** Se analizaron y procesaron las distintas columnas, se normalizaron los caracteres especiales. Aquellos valores nulos en fechas y horas fueron reemplazados por valores 'default' para mejor manipulación.
- **Columnas calculadas:** Se agregaron dos columnas calculadas a partir de 'velocidad_maxima' y 'velocidad_registrada', se trata de 'exceso_velocidad' y 'exceso_velocidad_real'.
- **Limpieza del dataset:** Aquellas filas cuyos valores no aportan valor informativo (por ej. un valor nulo en la patente) fueron filtradas del dataset y luego se guardo en '/data/interim'.

---

## [2026-04-23] - Día 3 de Trabajo

### Ejercicio 04: Refactorización y Análisis Avanzado
- **Programación Orientada a Objetos:** Creación de la clase `FineAnalyzer` para encapsular la lógica de procesamiento y análisis de multas.
- **Modularización:** Implementación de métodos específicos dentro de la clase para la carga, limpieza y generación de estadísticas del dataset.
- **Ejecución:** Ejecución secuencial de cada uno de los métodos de la clase para validar el flujo completo de análisis.

### Ejercicio 05: Visualizaciones
- **Gráfico de barras:** Top 10 patentes más reincidentes ordenadas de mayor a menor.
- **Gráfico de torta:** Porcentaje de infracciones por hora agrupadas sin minutos.
- **Gráfico de barras horizontal:** Cantidad de infracciones por mes ordenadas de mayor a menor.
- **Gráfico de líneas:** Excesos de velocidad de infracciones con hora 00:00.
- **Gráfico de líneas:** Excesos de velocidad de infracciones con fecha 1932-01-01.
- **Exportación:** Todos los gráficos guardados en `urban_flow/data/interim/plots/`.

---

## [2026-04-24] - Día 4 de Trabajo

### Ejercicio 06: Análisis de Integridad (Valores Centinela)
- **Cuantificación de Errores:** Cálculo porcentual de infracciones afectadas por valores por defecto (`1932-01-01` y `00:00`).
- **Diagnóstico:** Identificación del impacto de fallos en el sistema de registro heredado sobre la calidad total del dataset.

### Ejercicio 07: Conclusiones y Documentación de Cierre
- **Automatización de Reportes:** Uso de `%%writefile` para la actualización dinámica de las conclusiones en `README.md`.
- **Análisis de Hallazgos:** Redacción de la síntesis final sobre inconsistencias del sistema, patrones de reincidencia y distribución de infracciones para el cierre del **Sprint 1**.

### Refactorización y Control de Calidad (QA)
- **Corrección de Lógica de Datos:** Implementación de filtros para evitar el sesgo de "fechas centinela" en el análisis mensual de infracciones.
- **Ajuste de Requisitos:** Ordenamiento explícito (alfabético) en el reporte de ubicaciones según especificaciones del enunciado.
- **Optimización de Código:** - Eliminación de comentarios inline innecesarios para cumplir con las normas de estilo del proyecto.
## 2026-04-26 - Ejercicio 01
- Creación de la estructura de carpetas (raw, interim, processed)

## 2026-04-26 - Ejercicio 02
Descarga del dataset raw y analisis inicial de nulos

## 2026-04-26 - Ejercicio 03
- Normalización de fechas y patentes
- Tratamiento de outliers
- Generación de archivo interim

## 2026-04-26 - Ejercicio 04
- Implementación de la clase FineAnalyzer
- Creación de métodos de ranking y promedios

## 2026-04-26 - Ejercicio 05
- Generación de visualizaciones de distribución por ubicación
- Exportación de gráficos a la carpeta plots

## 2026-04-26 - Ejercicio 06
- Cálculo de métricas de calidad de datos
- Análisis de impacto de valores nulos normalizados
