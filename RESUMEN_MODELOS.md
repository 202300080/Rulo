# Resumen: Deteccion de Tumores con Redes Neuronales

## Objetivo
Clasificar tumores de mama como **Benigno (0)** o **Maligno (1)** utilizando redes neuronales con dos datasets diferentes.

---

## Estructura de los Modelos

Ambos modelos siguen **exactamente los mismos 10 pasos**:

| Paso | Descripcion |
|------|-------------|
| 1 | Importar librerias (NumPy, Pandas, TensorFlow, sklearn) |
| 2 | Cargar y validar dataset |
| 3 | Limpieza de datos (duplicados, nulos, outliers) |
| 4 | Normalizacion con MinMaxScaler [0, 1] |
| 5 | Analisis exploratorio (distribucion de clases) |
| 6 | Preprocesamiento (train/val/test estratificado) |
| 7 | Crear y entrenar la red neuronal |
| 8 | Evaluacion del modelo (metricas y graficas) |
| 9 | Prediccion para nuevos parametros |
| 10 | Ingreso de datos personalizados |

---

## Arquitectura de la Red Neuronal

```
Input(features)
    |
Dense(64, activation='relu')
    |
Dropout(0.30)
    |
Dense(32, activation='relu')
    |
Dropout(0.20)
    |
Dense(16, activation='relu')
    |
Dropout(0.10)
    |
Dense(1, activation='sigmoid')
    |
Output (probabilidad 0-1)
```

---

## Hiperparametros de Entrenamiento

| Parametro | Valor |
|-----------|-------|
| Optimizer | Adam |
| Loss | Binary Crossentropy |
| Epochs | 100 (max) |
| Batch Size | 32 |
| Early Stopping | patience=15, monitor='val_loss' |
| Semilla | 42 |

---

## Division de Datos

| Conjunto | Porcentaje |
|----------|------------|
| Train | 64% |
| Validation | 16% |
| Test | 20% |

*Division estratificada para mantener proporcion de clases.*

---

## Comparacion de Datasets

| Caracteristica | Dataset Local (CSV) | Dataset Nube (sklearn) |
|----------------|---------------------|------------------------|
| **Fuente** | `Breast_cancer_Reseach.csv` | `load_breast_cancer()` |
| **Filas** | 1,200 | 569 |
| **Features** | 21 | 30 |
| **Correlacion maxima** | 0.0775 | 0.7936 |
| **Correlacion promedio** | 0.0215 | 0.4703 |
| **Tipo** | Sintetico/Aleatorio | Real (Wisconsin) |

---

## Resultados

### Modelo con Dataset Nube (sklearn)
| Metrica | Valor |
|---------|-------|
| Accuracy | **97.37%** |
| Precision | 100.00% |
| Recall | 92.86% |
| F1-Score | 96.30% |
| ROC-AUC | **0.9937** |

### Modelo con Dataset Local (CSV)
| Metrica | Valor |
|---------|-------|
| Accuracy | **50.42%** |
| Precision | 49.15% |
| Recall | 24.58% |
| F1-Score | 32.77% |
| ROC-AUC | **0.5033** |

---

## Conclusion

> **La calidad del dataset determina el exito del modelo, no la arquitectura.**

- Ambos modelos tienen **arquitectura identica** e **hiperparametros identicos**.
- La unica diferencia es el **dataset utilizado**.
- El modelo con datos **reales** (sklearn) alcanza **97% de accuracy**.
- El modelo con datos **sinteticos** (CSV local) se comporta como **clasificacion aleatoria** (~50%).

### Leccion Aprendida
Un dataset con **correlaciones reales** entre features y target (>0.3) es fundamental para que una red neuronal pueda aprender patrones significativos.

---

## Features Utilizadas

### Dataset Nube (30 features)
Medidas de nucleos celulares en imagenes digitalizadas:
- **Mean**: radio, textura, perimetro, area, suavidad, compacidad, concavidad, puntos concavos, simetria, dimension fractal
- **SE (Error estandar)**: mismas 10 medidas
- **Worst (Peor valor)**: mismas 10 medidas

### Dataset Local (21 features)
Subconjunto similar con menos medidas de error estandar.

---

## Como Usar los Modelos

1. Ejecutar celdas del Paso 1 al 9 para entrenar el modelo
2. Ir al **Paso 10** y modificar el diccionario `MIS_DATOS`
3. Ejecutar la celda para obtener:
   - Probabilidad de Benigno
   - Probabilidad de Maligno
   - Diagnostico final
   - Grafica de resultados

---

*Documento generado como resumen del analisis comparativo de modelos de ML.*
