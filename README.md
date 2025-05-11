# UDD_BOOTCAMP
# 🏆 Proyecto M7 - Predicción de Edad en Ganadores del Oscar

Este repositorio contiene el desarrollo completo del **Proyecto M7** del Bootcamp UDD, enfocado en predecir la edad con la que una persona gana un premio Oscar, usando técnicas de Machine Learning e ingeniería estadística robusta.

---

## 🎯 Objetivo del Proyecto

Desarrollar un modelo que prediga la **edad al recibir el premio Oscar** a partir de:
- El año del premio (`year_of_award`)
- La categoría del premio (`award`, codificada con one-hot encoding)

El objetivo incluye además:
- Evaluación rigurosa con K-Fold
- Estimación de incertidumbre mediante bootstrapping
- Exposición del modelo como una API REST

---

## 📂 Contenido del repositorio

- `UDD_Proyecto_M7.ipynb` → Notebook con todo el flujo:
  - Exploración y limpieza de datos
  - Ingeniería de características
  - Selección de variables con Lasso
  - Entrenamiento de modelos (OLS, GLM, RLM)
  - Estimación de incertidumbre (±2.16 años)
  - Evaluación visual y numérica
- `main.py` → API REST lista para usar con FastAPI
- `modelo_rlm.pkl` → Modelo entrenado con RLM
- `readme_P7.md` → Este archivo

---

## 🧠 Técnicas y herramientas aplicadas

- `pandas`, `numpy`, `seaborn`, `matplotlib`
- `statsmodels.api` para regresión robusta (RLM)
- `scikit-learn` para validación cruzada y regularización (Lasso, Ridge)
- `FastAPI` + `Uvicorn` para la API
- `Ngrok` para exposición pública temporal

---

## 🔬 Modelos entrenados

Se entrenaron los siguientes modelos:

- ✅ `OLS` (modelo base)
- ✅ `GLM` (familia Gaussiana)
- ✅ `RLM` (modelo robusto con M-estimadores)

El mejor modelo fue `RLM`, con MAE promedio bajo y buen comportamiento en presencia de outliers.

---

## 🔁 Validación y resultados

- Validación cruzada con 5 folds
- MAE promedio del modelo RLM: ~2.1 años
- Incertidumbre estimada: ±2.16 años (IC 95%) mediante bootstrapping

---

## 🌐 API REST

La API permite enviar un JSON con las características de un ganador y devuelve la predicción de edad.

### Ejemplo de entrada:

```json
{
  "year_of_award": 2012,
  "award_Best_Actress": 1,
  "award_Best_Director": 0,
  "award_Best_Supporting_Actor": 0,
  "award_Best_Supporting_Actress": 0
}
