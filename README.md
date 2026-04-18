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
