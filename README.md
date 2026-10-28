# ml_challenge_da2026 — ID 26

Predicción de entregas tardías en comercio electrónico (Olist) · Tercer corte · Data Analytics 2026-2

| | |
|---|---|
| **Estudiante** | María Valentina Salgado Cifuentes |
| **ID asignado** | 26 |
| **Semilla** | 1026 (1000 + ID) |
| **Programa** | Ingeniería de Sistemas |
| **Universidad** | Universidad Central, Bogotá, Colombia |
| **Asignatura** | Data Analytics, 2026-2 |
| **Profesor** | Elias Buitrago Bolivar |

## Caso
¿Es posible anticipar los retrasos en las entregas? Se usa el *Brazilian E-Commerce Public Dataset by Olist*
(CSV fijados al commit `fa0cc6d1aff713d3c8b9a1e633b56889881848bf`). Cada estudiante trabaja con una muestra
reproducible de 35.000 pedidos (24.500 train / 5.250 valid / 5.250 test).

## Estructura
```
data/raw/         datos originales (no se publican)
data/processed/   datos preparados (se regeneran)
notebooks/        notebooks de las semanas S12 a S15
src/              código modular reutilizable (uso progresivo)
reports/          métricas (JSON) e informe ejecutivo
docs/             guía técnica y presentación del reto
```

## Avance por semana
| Semana | Laboratorio | Peso | Estado |
|---|---|---|---|
| S12 | Lab 1: modelos base y métricas | 3 % | Completado |
| S13 | Lab 2: ajuste y regularización | 3 % | Pendiente |
| S14 | Lab 3: validación e inferencia | 2 % | Pendiente |
| S15 | Lab 4: red neuronal y escalabilidad | 2 % | Pendiente |
| S16 | Desafío integrador | 15 % | Pendiente |

## Resultados S12 (validación, ID 26)
| Modelo | Accuracy | Recall | F1 | ROC-AUC | AP | Costo (R$) |
|---|---|---|---|---|---|---|
| Referencia (siempre "a tiempo") | 0,932 | 0,000 | 0,000 | – | – | 12.425 |
| Regresión logística (`class_weight='balanced'`) | 0,661 | 0,642 | 0,204 | 0,705 | 0,145 | 17.685 |

Regresión Ridge (días de entrega): MAE = 5,27 días. Huella de la muestra: `78a4ad412176`.

## Cómo reproducir
1. Abrir `notebooks/S12_ML_Challenge.ipynb` en Google Colab.
2. Verificar que `ID_ESTUDIANTE = 26`.
3. Ejecutar *Entorno de ejecución → Reiniciar y ejecutar todo*.
4. El reporte se genera en `reports/S12_resultados_ID_26.json`.

## Licencia
MIT.
