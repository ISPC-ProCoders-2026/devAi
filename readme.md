#  Análisis de Burnout en Desarrolladores de Software

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458.svg)](https://pandas.pydata.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Regression-F7931E.svg)](https://scikit-learn.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1L1bdAY86OOELi_P0ItoSu4UZ919DrGqZ?usp=sharing)
Análisis integral de factores de estrés y burnout en desarrolladores de software, estructurado en dos fases clave: **Comprensión de Datos (EDA)** y **Modelado Predictivo (Regresión Lineal)**.

---

##  Tabla de Contenidos
1. [Resumen del Proyecto](#-resumen-del-proyecto)
2. [Dataset & Estructura](#-dataset--estructura)
3. [Fase 1: Análisis Exploratorio de Datos (EDA)](#-fase-1-análisis-exploratorio-de-datos-eda)
4. [Fase 2: Regresión Lineal (Predicción de Estrés)](#-fase-2-regresión-lineal-predicción-de-estrés)
5. [Principales Hallazgos](#-principales-hallazgos)
6. [Instalación y Uso](#-instalación-y-uso)
7. [Autor / Contribución](#-autor--contribución)

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

##  Fase 1: Análisis Exploratorio de Datos (EDA)

En esta fase se examinan las distribuciones univariadas, las estadísticas descriptivas y la integridad de los datos.

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

##  Fase 2: Regresión Lineal (Predicción de Estrés)

El objetivo central de la regresión es modelar la variable continua `stress_level` en función de las métricas de hábitos de vida y carga laboral. 

* **Preprocesamiento:** Limpieza de registros nulos con `dropna()` para garantizar la estabilidad de la matriz de diseño.
* **Evaluación de Métricas:** (Incorpora coeficientes de regresión, $R^2$ y error cuadrático medio para cuantificar la influencia de variables como horas de sueño, carga horaria y reuniones diarias sobre el estrés).

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

## 👥 Autor / Contribución

Desarrollado como parte del proyecto de análisis de datos de salud ocupacional en tecnología. ¡Las contribuciones, issues y pull requests son bienvenidos!

---
*Licencia MIT © 2026*