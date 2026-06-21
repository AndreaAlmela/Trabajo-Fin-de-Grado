# Trabajo Fin de Grado

**Autora:** Andrea
**Título:** Inferencia y análisis de redes de regulación génica dinámicas en leucemia linfocítica crónica
**Grado:** Ciencia de Datos
**Universidad:** Universitat Politècnica de València

## Descripción

Este repositorio contiene el código, figuras y resultados generados como parte del Trabajo Fin de Grado, cuyo objetivo ha sido analizar redes de regulación génica dinámicas en leucemia linfocítica crónica a partir de datos transcriptómicos longitudinales.

El análisis se centra en la comparación de dos condiciones experimentales, *autologous* y *monoculture*, empleando datos de expresión génica, actividades de factores de transcripción estimadas mediante VIPER/msVIPER y redes reguladoras de referencia procedentes de CollecTRI. A partir de estos datos se han aplicado distintos enfoques de inferencia y modelado, incluyendo MORE, dynGENIE3 y modelos lineales mixtos, con el fin de estudiar relaciones reguladoras relevantes y posibles diferencias dinámicas entre condiciones.

Por motivos de confidencialidad y restricciones de distribución, los datos originales no se incluyen en este repositorio.

## Contenido del proyecto

* `Scripts/`: Scripts principales del análisis en R.

  * Preparación y exploración de datos.
  * Análisis PCA.
  * Construcción de matrices para MORE.
  * Inferencia de redes con MORE naive y MORE dynamic.
  * Comparación con dynGENIE3.
  * Modelos lineales mixtos y análisis de trayectorias temporales.


* `figures/`: Figuras generadas durante el análisis.

  * PCA global.
  * PCA por paciente.
  * Heatmaps y gráficos exploratorios.
  * Redes reguladoras.
  * Gráficos temporales de relaciones seleccionadas.

* `results/`: Resultados intermedios y tablas generadas.

  * Relaciones reguladoras inferidas.
  * Comparaciones entre métodos.
  * Tablas resumen por condición.
  * Resultados de modelos y métricas.

* `report/`: Documento final del Trabajo Fin de Grado en LaTeX.

## Objetivos principales

* Analizar la estructura global de los datos transcriptómicos longitudinales mediante técnicas exploratorias.
* Estudiar la variabilidad asociada al paciente, al tiempo y a la condición experimental.
* Inferir redes de regulación génica en las condiciones *autologous* y *monoculture*.
* Comparar los resultados obtenidos mediante distintas aproximaciones de inferencia, incluyendo MORE y dynGENIE3.
* Identificar relaciones reguladoras relevantes asociadas a factores de transcripción de interés biológico.
* Evaluar diferencias dinámicas entre condiciones experimentales.
* Generar visualizaciones interpretables que faciliten la discusión biológica de los resultados.

## Métodos empleados

* **Análisis exploratorio de datos:** revisión de dimensiones, distribución de expresión y correlación entre muestras.
* **Análisis de Componentes Principales (PCA):** exploración de la variabilidad global, por condición, tiempo y paciente.
* **CollecTRI:** red reguladora de referencia utilizada para restringir las asociaciones TF-target.
* **MORE naive:** inferencia de relaciones reguladoras a partir de matrices de actividad reguladora y datos de expresión.
* **MORE dynamic:** construcción de matrices dinámicas basadas en diferencias temporales para aproximar cambios en la actividad de los genes/TFs.
* **Modelos lineales mixtos:** análisis de trayectorias temporales considerando la variabilidad entre pacientes y réplicas.
* **Comparación de redes:** análisis de relaciones compartidas y específicas entre métodos y condiciones.
* **Visualización de redes y relaciones temporales:** representación de subredes y relaciones reguladoras seleccionadas.

## Requisitos

El análisis se ha desarrollado principalmente en **R**. Algunas de las principales dependencias utilizadas son:

* `MORE`
* `decoupleR`
* `dplyr`
* `tidyr`
* `tibble`
* `stringr`
* `ggplot2`
* `pheatmap`
* `PLSandO`
* `lme4`
* `lmerTest`
* `ropls`
* `furrr`
* `purrr`
* `igraph`
* `glmnet`
* `car`
* `MASS`
* `psych`

Para instalar los paquetes principales:

```r
install.packages(c(
  "dplyr",
  "tidyr",
  "tibble",
  "stringr",
  "ggplot2",
  "pheatmap",
  "lme4",
  "lmerTest",
  "furrr",
  "purrr",
  "igraph",
  "glmnet",
  "car",
  "MASS",
  "psych"
))
```

Algunos paquetes pueden requerir instalación desde Bioconductor o GitHub, dependiendo de la versión de R utilizada:

```r
# Bioconductor
if (!requireNamespace("BiocManager", quietly = TRUE)) {
  install.packages("BiocManager")
}

BiocManager::install(c("decoupleR", "ropls"))

# GitHub
install.packages("devtools")
devtools::install_github("BiostatOmics/PLSandO")
```



## Organización general del análisis

El flujo de trabajo seguido en el proyecto puede resumirse en las siguientes etapas:

1. Carga y preparación de matrices de expresión y actividad de factores de transcripción.
2. Análisis exploratorio y PCA.
3. Selección de factores de transcripción diferencialmente activos.
4. Construcción de matrices de entrada para MORE naive y MORE dynamic.
5. Inferencia de redes reguladoras por condición experimental.
6. Comparación de resultados con dynGENIE3.
7. Análisis mediante modelos lineales mixtos.
8. Selección e interpretación de relaciones reguladoras de interés.
9. Generación de figuras y tablas para la memoria final.

## Licencia

Este repositorio se ha desarrollado con fines académicos en el contexto de un Trabajo Fin de Grado. El uso del código debe citar adecuadamente este trabajo y respetar las restricciones asociadas a los datos originales.
