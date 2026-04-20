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
- **Diagnóstico:** Identificación de valores nulos y registros inconsistentes en fechas y horas.

### Infraestructura y Reproducibilidad
- **Dependencias:** Creación de `requirements.txt` para asegurar la instalación de librerías (`pandas`, `requests`, `seaborn`, etc.) en cualquier entorno.
- **Compatibilidad:** Implementación de celda de configuración dinámica para detectar y configurar automáticamente el entorno en **Google Colab** o **GitHub Codespaces**.