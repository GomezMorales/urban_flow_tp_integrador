# Urban Flow - Sistema de Gestión de Infracciones

## Sprint 1

### Integrantes del Grupo

* Mariano Tejerina
* Emiliano Quiroga
* Leandro Bonifacio
* Luis Gomez Morales

---

## Objetivo

El objetivo principal de este proyecto es aplicar conocimientos técnicos para el versionado de código, la organización y limpieza de datos, y la utilización avanzada de la librería pandas. Se busca transformar registros inconsistentes en información valiosa para el control de tráfico.

## Introducción y Contexto

La localidad de **Vaalserberg (Bélgica)**, situada en la zona fronteriza con los Países Bajos y Alemania, cuenta con un sistema de radares urbanos para detectar excesos de velocidad.

Actualmente, el sistema debe procesar registros históricos provenientes de **sistemas heredados**, los cuales presentan errores de formato, datos faltantes y registros inconsistentes. Este proyecto se enfoca en analizar y depurar estos datos para que puedan ser integrados al nuevo sistema de la ciudad sin inconsistencias.

## Estructura de Directorios

El proyecto mantiene la siguiente organización de archivos:

* `urban_flow/data/raw/`: Almacena los datasets en crudo, sin procesar.
* `urban_flow/data/interim/`: Almacena datasets procesados de pasos intermedios y gráficos.
* `urban_flow/data/processed/`: Almacena el dataset final depurado listo para su uso.

## Requerimientos Técnicos

* **Indentación:** 2 espacios según estándar solicitado.
* **Formato:** PEP8 y Type Hints obligatorio.
* **Versionado:** Uso de ramas (Sprint_1) y prohibición de `git add .`.

## Conclusiones del dataset — Sprint 1

El dataset de multas por exceso de velocidad de Vaalserberg presentó
inconsistencias significativas heredadas del sistema anterior.

Tras el proceso de limpieza y normalización se identificaron los
siguientes hallazgos:

- **Datos con fecha inválida (1932-01-01):** un porcentaje de los
  registros no poseía una fecha válida. Esto indica fallas en el
  sistema de registro del radar o en la exportación del sistema
  heredado.

- **Datos con hora inválida (00:00):** de manera similar, una
  proporción de registros carecía de hora válida, lo que impide
  analizar con precisión los horarios de mayor incidencia para
  esos casos.

- **Patentes inválidas:** se detectaron registros sin patente
  identificable, los cuales fueron descartados por no aportar
  valor al análisis ni al nuevo sistema.

- **Reincidencia:** el análisis de las 10 patentes más multadas
  evidencia vehículos con alta frecuencia de infracciones, lo que
  sugiere conductores habituales de las vías monitoreadas.

- **Distribución horaria:** la mayoría de las infracciones se
  concentra en determinadas franjas horarias, lo que permite
  orientar los controles hacia esos momentos de mayor riesgo.

- **Distribución mensual:** tras filtrar los registros con fechas inválidas que sesgaban el análisis inicial, se identificaron picos de infracciones que pueden correlacionarse con una mayor circulación vehicular en períodos específicos.

En síntesis, el dataset requirió un tratamiento exhaustivo antes
de poder ser utilizado de forma confiable. Los datos depurados
constituyen una base sólida para incorporar al nuevo sistema y
para futuras etapas de análisis del comportamiento vial.
