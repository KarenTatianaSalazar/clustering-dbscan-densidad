# Agrupamiento de Geometrías Complejas: Un Enfoque Basado en Densidad con DBSCAN

Este repositorio contiene un caso de estudio sobre el agrupamiento no supervisado de un conjunto de datos bidimensional con estructuras de formas arbitrarias (anillos concéntricos, franjas alargadas y un aglomerado denso). El objetivo es aplicar e interpretar el algoritmo DBSCAN, evaluando la sensibilidad de sus hiperparámetros y su capacidad para aislar observaciones atípicas como ruido, frente a las limitaciones de los métodos basados en centroides como K-Means.

## Ejecutar en Google Colab

Puedes abrir, revisar y ejecutar todo el código de este análisis de forma interactiva haciendo clic en el siguiente botón:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/KarenTatianaSalazar/clustering-dbscan-densidad/blob/main/dbscan_multiforma.ipynb)

## Resumen del Proyecto

El objetivo principal de esta investigación es identificar las estructuras presentes en el conjunto de datos `multiforma.csv` mediante DBSCAN, seleccionar la combinación de hiperparámetros (`eps` y `min_samples`) que las separe adecuadamente y validar el resultado a partir del análisis visual, las características geométricas de los grupos y el índice Silhouette.

* **Datos utilizados:** `multiforma.csv`, con 1100 observaciones y dos variables continuas (`x`, `y`) que corresponden a coordenadas en un plano. No presenta valores nulos ni filas duplicadas. El archivo se carga directamente desde el repositorio [adiacla/bigdata](https://github.com/adiacla/bigdata).
* **Técnica:** DBSCAN (Density-Based Spatial Clustering of Applications with Noise), con estandarización previa (`StandardScaler`) y evaluación mediante el coeficiente de Silhouette.
* **Contexto:** Desarrollado para el curso *Fundamentos y Aplicaciones de la Inteligencia Artificial*.

## Metodología

1. **Análisis exploratorio:** revisión de la estructura de los datos, diagramas de caja y gráfico de dispersión, que revelan la presencia de estructuras no esféricas y de observaciones aisladas.
2. **Preprocesamiento:** estandarización de las variables con `StandardScaler`.
3. **Experimentación:** grilla de hiperparámetros con `eps` entre 0.2 y 0.7 y `min_samples` entre 3 y 6, complementada con una verificación de valores de `eps` menores (0.10 a 0.25) y el gráfico de distancias al k-ésimo vecino más cercano.
4. **Modelo final y validación:** entrenamiento con la configuración seleccionada y análisis del Silhouette global, por clúster y por observación, junto con las distancias entre centroides y entre clústeres.

## Principales Resultados

* **Configuración óptima:** `eps = 0.2` y `min_samples = 5`.
* **Estructuras identificadas:** cinco clústeres (anillo exterior con 410 observaciones, anillo interior con 407, dos franjas horizontales con 106 y 101, y un aglomerado denso inferior derecho con 51), más 25 puntos clasificados como ruido (2.3 % del total).
* **Sensibilidad de `eps`:** con valores menores (0.15) las estructuras se fragmentan en 7 clústeres, y con valores mayores (0.25) los dos anillos concéntricos se fusionan. La configuración elegida se ubica en una ventana estrecha entre ambos comportamientos.
* **Índice Silhouette:** 0.2233 (excluyendo el ruido). Este valor es bajo y no demuestra por sí solo una separación clara, ya que el índice se basa en distancias medias y penaliza geometrías no convexas como los anillos concéntricos y las franjas alargadas. La validación del modelo se apoya, por tanto, en el análisis visual y en las características geométricas de cada estructura.

## Contenido del Repositorio

* `dbscan_multiforma.ipynb`: notebook con el análisis completo, desde el EDA hasta las conclusiones.
* `README.md`: descripción del proyecto.

## Tecnologías

Python, pandas, NumPy, scikit-learn, SciPy, Matplotlib y Seaborn.

## Autora

Karen Tatiana Salazar Sepúlveda
