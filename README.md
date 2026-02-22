# 🧬 RNASEQ_2026_NOTAS

**Notas del curso — Intro RNA-seq (LCG-UNAM, 2026)**

---

## Descripción general y contexto académico

Este repositorio constituye el espacio central de documentación de mis notas, implementaciones técnicas y ejercicios reproducibles desarrollados durante el curso **“Intro RNA-seq LCG-UNAM 2026”**.

Los materiales aquí contenidos representan la evidencia principal del componente de **Trabajo Público** dentro de la evaluación formal del curso.

El repositorio sigue principios alineados con la metodología de **Team Data Science**, enfatizando:

* Investigación versionada
* Reproducibilidad computacional
* Organización estructurada de proyectos
* Transparencia en el entorno de ejecución

Más allá de documentar ejercicios, este repositorio consolida una base reproducible para futuros análisis de RNA-seq y proyectos de genómica regulatoria.

---

## Metadatos del curso

* **Instructor:** Leonardo Collado-Torres
* **Asistente:** María José Palma Martínez
* **Ponentes invitados:**
  Melissa Mayén Quiroz
  Maria Gutiérrez-Arcelus
  Gabriel Ramírez-Vilchis
  Daianna González Padilla
* **Fechas:** 10–13 de febrero de 2026
* **Sede:** CCG-UNAM, Cuernavaca, México
* **Coordinación académica:** Heladia Salgado y Julio Collado Vides

---

## Entorno técnico de cómputo

Para garantizar reproducibilidad estricta, los análisis se realizaron bajo la siguiente configuración:

* **R:** 4.5.2
* **Bioconductor:** 3.22 (publicado el 30 de octubre de 2025)
* **Entorno de desarrollo (IDE):**

  * Positron (entorno moderno recomendado)
  * RStudio ≥ 2026.01.0

### Estándares de desarrollo

* **Formateo de código:** Air (formateador automático)
* **Desarrollo asistido por IA:** GitHub Copilot Pro (Education Pack)
* **Control de versiones:** Autenticación SSH/PAT para integración segura con GitHub

Esta configuración permite mantener consistencia y reproducibilidad entre entornos de trabajo.

---

## Programa documentado y contenidos trabajados

### Día 1 — Orquestación del flujo de trabajo y fundamentos

Introducción a:

* R como entorno de análisis
* Positron como IDE
* Gestión estructurada de proyectos con `usethis` y `here`
* Configuración de autenticación segura con GitHub
* Integración de herramientas de asistencia inteligente

Enfoque principal: establecer infraestructura reproducible antes del análisis.

---

### Día 2 — Fundamentos de Bioconductor y exploración interactiva

Estudio detallado de la clase **SummarizedExperiment**, contenedor fundamental para datos de expresión:

* Assays
* `rowData` y `colData`
* Metadatos
* Sistema S4 y funciones accesoras

Demostración invitada del paquete **iSEE** para exploración interactiva de datos transcriptómicos.

---

### Día 3 — Presencia académica y adquisición de datos a gran escala

* Construcción de presencia profesional mediante `postcards`
* Adquisición y manejo de datos públicos con `recount3`
* Integración de metadatos
* Prácticas de reproducibilidad en datos públicos de RNA-seq

---

### Día 4 — Modelado estadístico y expresión diferencial

* Construcción e interpretación de matrices de diseño con `ExploreModelMatrix`
* Introducción a flujos de trabajo con `limma` y `edgeR`
* Discusión sobre interpretación de modelos lineales
* Integración conceptual del análisis de RNA-seq dentro del paradigma Team Data Science

Este día sintetizó teoría estadística y práctica computacional.

---

## Contenido del repositorio

### Carpeta `/R/`

Scripts que implementan:

* Manipulación de objetos `SummarizedExperiment`
* Visualización interactiva con `iSEE`
* Recuperación de datos con `recount3`
* Fundamentos de modelado lineal
* Reducción de dimensionalidad (PCA)
* Interpretación de diseños experimentales

---

### Carpeta `/figuras/`

Contiene resultados gráficos generados durante los análisis, incluyendo:

* Visualizaciones PCA
* Gráficos de expresión a nivel de features
* Representaciones de reducción de dimensionalidad

Estos archivos constituyen evidencia directa de la ejecución reproducible de los flujos de trabajo.

---

### Archivo `05-BioConductorHighlights.md`

Análisis crítico de paquetes seleccionados de **Bioconductor 3.22**:

* **iModMix** — Integración multiómica basada en redes
* **ComplexHeatmap** — Visualización avanzada de mapas de calor
* **cellmig** — Modelado jerárquico bayesiano

Se enfatizan criterios de rigor estadístico, mantenimiento activo y estándares de reproducibilidad.

---

## Paquetes requeridos

Inicialización del entorno del curso:

```r
if (!requireNamespace("BiocManager", quietly = TRUE)) {
    install.packages("BiocManager")
}

BiocManager::install(c(
    "usethis", "here", "biocthis", "lobstr", "postcards", "sessioninfo",
    "SummarizedExperiment", "iSEE",
    "edgeR", "ExploreModelMatrix", "limma", "recount3",
    "pheatmap", "ggplot2", "patchwork", "RColorBrewer", "ComplexHeatmap",
    "spatialLIBD"
))
```

---

## Reflexión conceptual y aprendizajes clave

Más allá de la implementación técnica, este curso permitió consolidar varios principios fundamentales del análisis transcriptómico reproducible:

### 1. La estructura precede al análisis

El uso de clases formales como `SummarizedExperiment` enfatiza que el análisis no comienza con gráficos ni pruebas estadísticas, sino con una correcta representación estructurada de los datos:

* Separación explícita entre assays, anotaciones y metadatos.
* Encapsulamiento de información experimental.
* Acceso controlado mediante funciones accesoras.

Esta arquitectura reduce ambigüedades y facilita la reproducibilidad.

---

### 2. El modelado estadístico es una declaración formal de hipótesis

La construcción de matrices de diseño (`model.matrix`, `ExploreModelMatrix`) mostró que:

* Cada modelo estadístico codifica explícitamente una pregunta biológica.
* La interpretación de coeficientes depende del diseño experimental.
* La claridad en el diseño es tan importante como el ajuste del modelo.

El análisis de expresión diferencial no es una “función automática”, sino la formalización matemática de una comparación biológica.

---

### 3. Reproducibilidad como principio estructural

La reproducibilidad no consiste únicamente en compartir código, sino en:

* Fijar versiones de R y Bioconductor.
* Documentar dependencias.
* Mantener una organización clara del repositorio.
* Separar datos procesados de scripts.

El uso de control de versiones y estándares de proyecto garantiza trazabilidad.

---

### 4. Exploración interactiva como herramienta crítica

Herramientas como `iSEE` permiten:

* Detectar patrones antes de modelar.
* Validar supuestos.
* Identificar posibles efectos de confusión.

La visualización interactiva no sustituye al análisis estadístico, pero mejora la interpretación crítica de los datos.

---

### 5. Integración dentro del paradigma Team Data Science

El curso enmarcó el análisis de RNA-seq dentro de una metodología que prioriza:

* Organización del proyecto.
* Automatización razonable.
* Colaboración estructurada.
* Transparencia en la toma de decisiones analíticas.

Este enfoque convierte el análisis transcriptómico en un proceso replicable y escalable.

---

