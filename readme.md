<p align="center">
  <img src="ISPC_portada.png" alt="Portada institucional del ISPC" width="100%">
</p>

# Análisis de Burnout en Desarrolladores de Software

**Institución:** Instituto Superior Politécnico Córdoba (ISPC)

**Materia:** Desarrollo de Inteligencia Artificial - TSDS - 2026

## Equipo ProCoders

* Daniel Nicolás Paez
* Juan Pablo Sánchez Brandán
* Juan Ignacio Gioda
* Francisco Toro
* Nahuel Argandoña

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458.svg)](https://pandas.pydata.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Regression-F7931E.svg)](https://scikit-learn.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1L1bdAY86OOELi_P0ItoSu4UZ919DrGqZ?usp=sharing)
Análisis integral de factores de estrés y burnout en desarrolladores de software. El proyecto aborda la **comprensión de los datos y el Análisis Exploratorio de Datos (EDA)** y el **modelado predictivo mediante regresión lineal**.

---

##  Tabla de Contenidos
1. [Resumen del Proyecto](#-resumen-del-proyecto)
2. [Dataset & Estructura](#-dataset--estructura)
3. [Fase 1: Comprensión de los datos y EDA](#-fase-1-comprensión-de-los-datos-y-eda)
4. [Fase 2: Modelado y evaluación](#-fase-2-modelado-y-evaluación)
5. [Principales Hallazgos](#-principales-hallazgos)
6. [Instalación y Uso](#-instalación-y-uso)
7. [Equipo ProCoders](#equipo-procoders)

---

##  Resumen del Proyecto

Este repositorio contiene un Jupyter Notebook detallado que investiga cómo los hábitos diarios, el contexto laboral y las variables demográficas impactan en el **nivel de estrés** (`stress_level`, escala continua de 0 a 100) y la **categoría de burnout** (`burnout_level`: Low, Medium, High) de los ingenieros de software.

---

##  Dataset & Estructura

* **Nombre del archivo:** `developer_burnout_dataset_7000.csv`
* **Dimensiones:** 7,000 registros x 12 variables (11 numéricas y 1 categórica).
* **Calidad de datos:** El dataset presenta un 2% de valores faltantes (140 registros incompletos distribuidos uniformemente), los cuales se gestionan de manera específica según la fase (conservados para visualización descriptiva, filtrados mediante `dropna()` para el modelado).

### Diccionario de Variables

| Variable | Tipo | Descripción |
| :--- | :--- | :--- |
| `age` | Numérica continua | Edad del desarrollador (años) |
| `experience_years` | Numérica continua | Años de experiencia en desarrollo de software |
| `daily_work_hours` | Numérica continua | Horas trabajadas por día |
| `sleep_hours` | Numérica continua | Horas de sueño promedio por noche |
| `caffeine_intake` | Numérica continua | Consumo diario de cafeína (tazas/unidades) |
| `bugs_per_day` | Numérica continua | Promedio de bugs encontrados/corregidos por día |
| `commits_per_day` | Numérica continua | Promedio de commits realizados por día |
| `meetings_per_day` | Numérica continua | Cantidad de reuniones diarias |
| `screen_time` | Numérica continua | Tiempo total frente a pantallas (horas diarias) |
| `exercise_hours` | Numérica continua | Horas de ejercicio físico diario |
| `stress_level` | Numérica continua (**Target Regresión**) | Nivel de estrés reportado (0 – 100) |
| `burnout_level` | Categórica ordinal (**Target Clasificación**) | Nivel de burnout (`Low`, `Medium`, `High`) |

---

##  Fase 1: Comprensión de los datos y EDA

En esta fase se comprende la estructura del dataset, se revisa la calidad de los datos y se exploran las distribuciones y relaciones entre variables. La identificación inicial de tipos queda organizada así:

* **Variables numéricas (11):** `age`, `experience_years`, `daily_work_hours`, `sleep_hours`, `caffeine_intake`, `bugs_per_day`, `commits_per_day`, `meetings_per_day`, `screen_time`, `exercise_hours` y `stress_level`.
* **Variable categórica ordinal (1):** `burnout_level`, con las categorías `Low`, `Medium` y `High`.
* **Variables objetivo posibles:** `stress_level` para regresión y `burnout_level` para clasificación.

El EDA incluye estadísticas descriptivas, histogramas con curvas de densidad para explorar las variables numéricas, un análisis de frecuencias para `burnout_level` y una matriz de correlación visualizada con un mapa de calor. Estas visualizaciones ayudan a detectar distribuciones, desequilibrios entre categorías y asociaciones iniciales entre hábitos, carga laboral, estrés y burnout; son hallazgos exploratorios y no implican causalidad.

* **Estadísticas Descriptivas Clave:**
  * **Edad promedio:** ~32.1 años (Rango: 20 – 44).
  * **Experiencia:** Media de 9.58 años.
  * **Jornada laboral:** Media de 9.0 horas diarias (con picos de hasta 14 horas).
  * **Sueño:** Media de 6.48 horas (descanso por debajo de los óptimos recomendados en perfiles con alto estrés).
  * **Nivel de Estrés:** Media global de 53.65 (desviación estándar de 23.45).
* **Distribución de la Variable Objetivo Categórica (`burnout_level`):**
  * `Medium`: 3,485 registros (≈ 50.8%)
  * `High`: 1,782 registros (≈ 26.0%)
  * `Low`: 1,593 registros (≈ 23.2%)

---

##  Fase 2: Modelado y evaluación

La consigna propone que equipos de **2 a 6 integrantes** implementen un modelo de regresión o clasificación que responda al problema definido y a las conclusiones del EDA. En este proyecto se trabaja con **regresión lineal** para predecir la variable continua `stress_level` a partir de las variables de hábitos y contexto laboral.

### Modelado y entrenamiento

* Se separan los datos en conjuntos de entrenamiento (`train`) y prueba (`test`); el notebook reserva el 20 % para prueba.
* El algoritmo se ajusta utilizando únicamente el conjunto de entrenamiento.
* Para el modelado se filtran los registros incompletos con `dropna()`.

### Evaluación de desempeño

Se generan predicciones sobre el conjunto de prueba para estimar cómo responde el modelo ante datos no usados durante el entrenamiento. Para la regresión se calculan e interpretan:

* **MAE:** error absoluto medio.
* **MSE/RMSE:** error cuadrático medio y su raíz.
* **R²:** proporción de variabilidad de la variable objetivo explicada por el modelo.

Si se opta por un problema de clasificación usando `burnout_level` como objetivo, las métricas correspondientes son la **matriz de confusión, Accuracy, Precision, Recall y F1-score**.

> **Alcance de esta evidencia:** la optimización final del modelo, el ajuste fino de parámetros y los detalles que queden pendientes se abordarán en la **Tercera Evidencia**.

---

## 💡Principales Hallazgos

1. **Impacto del Descanso:** Existe una correlación inversa notable entre las horas de sueño (`sleep_hours`) y el nivel de estrés (`stress_level`). Menos horas de descanso incrementan de manera exponencial la propensión al burnout.
2. **Carga Laboral y Reuniones:** Un alto volumen de `meetings_per_day` combinando con jornadas de `daily_work_hours` superiores a 9 horas se alinea fuertemente con los niveles de estrés clasificados como `High`.
3. **Equilibrio Vida-Trabajo:** El tiempo de ejercicio físico (`exercise_hours`) actúa como un factor atenuante del estrés reportado.

---

##  Instalación y Uso

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/tu-usuario/analisis-burnout-desarrolladores.git
   cd analisis-burnout-desarrolladores
   ```

2. **Crear un entorno virtual e instalar dependencias:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # En Windows: venv\Scripts\activate
   pip install pandas numpy matplotlib seaborn scipy scikit-learn
   ```

3. **Ejecutar el Jupyter Notebook:**
   ```bash
   jupyter notebook analisis_burnout.ipynb
   ```

---
