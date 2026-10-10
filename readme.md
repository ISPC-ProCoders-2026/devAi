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

---

* [Link Colab del Proyecto](https://colab.research.google.com/drive/1YymcGoV2PEVJPE0hnplOqUVwzwjEbHqb?usp=sharing)
* [Link del Modelo ABP - Pendiente]()


## ¿De qué trata el proyecto?

El burnout, o agotamiento profesional, es un problema cada vez más común entre quienes trabajan en desarrollo de software: jornadas largas, muchas reuniones, presión por entregar y poco descanso.

Con este proyecto quisimos responder una pregunta concreta:

> ¿Qué tan bien podemos estimar el nivel de estrés de una persona a partir de sus hábitos de trabajo y de descanso, y qué factores pesan más?

Trabajamos con un conjunto de datos de 7 000 registros sobre desarrolladores. A partir de ellos analizamos los datos, construimos modelos que estiman el estrés y comparamos cuál funciona mejor.

## Técnicas utilizadas

- **Limpieza de datos:** revisión de valores faltantes y duplicados.
- **Análisis exploratorio:** distribuciones, valores atípicos y relaciones entre variables.
- **Regresión lineal:** modelo base para estimar el nivel de estrés, con interpretación de su peso por variable.
- **Árbol de decisión y Random Forest:** modelos no lineales para comprobar si la regresión lineal era suficiente.
- **Validación cruzada y ajuste de parámetros:** para asegurar que los resultados son estables.
- **Regularización y multicolinealidad:** para simplificar el modelo y detectar variables redundantes.
- **Verificación de supuestos:** pruebas estadísticas para confirmar que las conclusiones son confiables.

## Qué encontramos

- **Los hábitos de trabajo y descanso explican bien el estrés.** El modelo final logra explicar cerca del 83 % de las diferencias de estrés entre personas, y su error típico es de unos 10 puntos en una escala de 0 a 100.
- **Más horas de trabajo, reuniones, errores y cafeína se asocian con más estrés.** Dormir más y hacer ejercicio se asocian con menos estrés.
- **Un modelo simple fue el mejor.** Las alternativas más complejas no mejoraron el resultado, lo que indica que la relación entre las variables es mayormente lineal.
- **Son asociaciones, no causas.** El análisis muestra qué factores van juntos con el estrés, pero no prueba que uno cause al otro.

## Limitaciones

- Una parte de los datos tenía valores faltantes, y eliminar esas filas dejó alrededor del 78 % de los registros.
- Los datos parecen simulados, por lo que habría que volver a evaluar el modelo con datos reales antes de usarlo en la práctica.
- El modelo sirve para orientar, no para diagnosticar a una persona en particular.

## Librerías utilizadas

| Librería | Para qué la usamos |
|---|---|
| pandas | Cargar y manipular los datos en tablas |
| numpy | Cálculos numéricos |
| matplotlib | Gráficos base |
| seaborn | Gráficos estadísticos (distribuciones, boxplots, mapas de calor) |
| scipy | Pruebas estadísticas |
| scikit-learn | Entrenar, validar y comparar modelos de predicción |
| statsmodels | Análisis estadístico: significancia, intervalos de confianza y diagnósticos |

## Cómo ejecutarlo en local

**1. Requisitos:** tener Python 3.10 o superior instalado.

**2. Descargar la carpeta del proyecto**, que debe incluir el notebook `burnout_analysis.ipynb` y el archivo `developer_burnout_dataset_7000.csv` en el mismo lugar.

**3. Abrir una terminal dentro de esa carpeta.**

**4. (Opcional) Crear un entorno virtual** para no mezclar librerías:

```bash
python -m venv venv
```

Y activarlo:

- En Windows: `venv\Scripts\activate`
- En Mac o Linux: `source venv/bin/activate`

**5. Instalar las librerías y Jupyter:**

```bash
python -m pip install pandas numpy matplotlib seaborn scipy scikit-learn statsmodels jupyter
```

**6. Abrir Jupyter:**

```bash
jupyter notebook
```

Se abre el navegador con la lista de archivos. Hacer clic en `burnout_analysis.ipynb`.

**7. Ejecutar todo el notebook:** en el menú, elegir *Kernel → Restart & Run All* (o *Run All*). Las celdas se ejecutan en orden y los gráficos aparecen debajo de cada una.

> Si el CSV no está en la misma carpeta que el notebook, la lectura de datos va a fallar. Tiene que estar ahí.

## Reflexión del grupo

Estamos muy contentos de haber cursado esta materia. Aprendimos muchas cosas que no conocíamos, desde cómo preparar los datos hasta cómo interpretar un modelo y sacar conclusiones de él. Todavía nos cuesta entenderlo del todo, pero es un tema que nos gustó, y pensamos seguir profundizando en él en el futuro.


