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