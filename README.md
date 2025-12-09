# Proyecto Final: Recomendación Grupal de Juegos de Mesa
## IIC3633 - Sistemas Recomendadores (2025-2)

Este repositorio contiene la implementación, análisis y evaluación de diferentes modelos de recomendación (Baselines, Factorización Matricial y Deep Learning) aplicados a un contexto grupal utilizando el dataset de **BoardGameGeek**.

El proyecto explora estrategias de agregación de predicciones (*Average, Least Misery, Most Pleasure*) y compara arquitecturas de modelado (*Aggregated Predictions* vs. *Aggregated Models*).

---

### 👥 Integrantes - Grupo 11

* **Vicente Correa** - vicente.correa@uc.cl
* **Alberto Maturana** - alberto.maturana@uc.cl
* **Mariela Zambrano** - mariela.zambrano@uc.cl

---

### 📂 Estructura del Proyecto

El proyecto se divide en 7 notebooks principales (uno por modelo + análisis de datos) y los informes de entrega.

#### 1. Preprocesamiento y Análisis
* `data_analysis.ipynb`: Contiene la carga del dataset crudo, el análisis exploratorio (distribuciones, long-tail), el filtrado de usuarios/items (k-core) y la **separación de los conjuntos de datos** (Training, Validation, Testing).

#### 2. Modelos (Notebooks independientes)
* `MF.ipynb`: Implementación de Matrix Factorization con agregación de predicciones.
* `MF_for_groups.ipynb`: Implementación de la arquitectura **Aggregated Models** (perfiles grupales pre-entrenamiento).
* `SVD++.ipynb`: Implementación del algoritmo SVD++ (feedback implícito).
* `DeepFM.ipynb`: Implementación del modelo híbrido utilizando DeepCTR-Torch.
* `Random.ipynb`: Baseline aleatorio.
* `Most_Popular.ipynb`: Baseline de popularidad.

---

### ⚙️ Requisitos y Dependencias

El código está diseñado para ejecutarse en **Google Colab**. Las librerías principales utilizadas son:
* `numpy==1.26` (Crítico para compatibilidad con Surprise)
* `scikit-surprise` (Para modelos de factorización)
* `deepctr-torch` (Para DeepFM)
* `gdown` (Para descarga automática de datos)

> **Nota:** Todas las instalaciones necesarias se encuentran en la primera celda de cada notebook.

---

### 🚀 Instrucciones de Ejecución

#### 1. Obtención de los Datos
No es necesario descargar manualmente el dataset. Todos los notebooks incluyen un bloque de código que utiliza `gdown` para descargar automáticamente el archivo `.zip` con los datos procesados (train/val/test) directamente desde Google Drive al entorno de Colab.

#### 2. Ejecución de Modelos (MF, SVD++, Random, Most Popular, MF for Groups)
Estos notebooks requieren una versión específica de Numpy para funcionar con la librería Surprise:

1.  Abrir el notebook en Google Colab.
2.  Ejecutar la **primera celda** (instalación de librerías y `numpy==1.26`) y esperar.
3.  **REINICIAR LA SESIÓN (RUNTIME)**
4.  Ejecutar el resto de las celdas secuencialmente (`Run All` después del reinicio).

#### 3. Ejecución de DeepFM (`DeepFM.ipynb`)
Este notebook no requiere el reinicio por Numpy. Simplemente abra el archivo y ejecute todas las celdas en orden.

---

### ⚠️ Consideraciones de Tiempo y Hardware

* **Hardware:** Se recomienda utilizar el entorno estándar de Colab. Para `DeepFM`, el uso de GPU (T4) acelerará el entrenamiento, aunque no es estrictamente obligatorio.
* **Tiempo de Ejecución:** Tenga en cuenta que algunos modelos son computacionalmente costosos:
    * *Most Popular* y *MF* pueden tardar **aprox. 1 hora** en completar todas las evaluaciones y métricas grupales.
    * Se recomienda no cerrar la pestaña del navegador durante la ejecución.

---

### 📄 Referencias
El proyecto utiliza el dataset *Board Games Database* de BoardGameGeek (Kaggle): https://www.kaggle.com/datasets/threnjen/board-games-database-from-boardgamegeek. Para detalles sobre la metodología y resultados, referirse al informe final adjunto en la entrega.
