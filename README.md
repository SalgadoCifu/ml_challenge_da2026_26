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
notebooks/SXX/    un notebook por semana (S12 a S15)
src/              código modular reutilizable (uso progresivo)
reports/SXX/      métricas (JSON) e informe ejecutivo de cada semana
docs/SXX/         guía técnica de cada semana (docs/ guarda el PDF del reto)
```

## Avance por semana
| Semana | Laboratorio | Peso | Estado |
|---|---|---|---|
| S12 | Lab 1: modelos base y métricas | 3 % | Completado |
| S13 | Sin clase; su tema (PCA) pasó a la S14 | 3 % | No se dictó |
| S14 | Lab 2: PCA y evaluación de mejoras | 2 % | Completado |
| S15 | Lab 4: red neuronal y escalabilidad | 2 % | Pendiente |
| S16 | Desafío integrador | 15 % | Pendiente |

## Resultados S12 (validación, ID 26)
| Modelo | Accuracy | Recall | F1 | ROC-AUC | AP | Costo (R$) |
|---|---|---|---|---|---|---|
| Referencia (siempre "a tiempo") | 0,932 | 0,000 | 0,000 | – | – | 12.425 |
| Regresión logística (`class_weight='balanced'`) | 0,661 | 0,645 | 0,205 | 0,705 | 0,145 | 17.642 |

Regresión Ridge (días de entrega): MAE = 5,27 días. Huella de la muestra: `78a4ad412176`.

## Resultados S14 (validación, ID 26)
Se aplicó PCA a las 24 variables numéricas: 15 componentes explican al menos el 90 % de la varianza (0,904). Los cuatro modelos usan la misma muestra, la misma partición, `class_weight='balanced'` y umbral 0,50.

| Modelo | Accuracy | Precision | Recall | F1 | AP | Costo (R$) |
|---|---|---|---|---|---|---|
| A. Referencia (sin PCA, C=1) | 0,661 | 0,122 | 0,645 | 0,205 | 0,145 | 17.642 |
| B. PCA 90 % (C=1) | 0,646 | 0,112 | 0,611 | 0,189 | 0,127 | 18.582 |
| C. PCA 90 % (C=0,1) | 0,645 | 0,112 | 0,614 | 0,190 | 0,130 | 18.611 |
| D. PCA 90 % (C=10) | 0,646 | 0,112 | 0,611 | 0,189 | 0,126 | 18.598 |

Modelo elegido: A. Referencia (sin PCA, C=1), por tener el menor costo en validación. Prueba KS sobre `valor_flete` (entrenamiento frente a validación): D = 0,0144, valor p = 0,3242; no se rechaza H0 al 5 %. El detalle está en `reports/S14/S14_resumen_ID_26.md`.

## Cómo reproducir
1. Abrir en Google Colab el notebook de la semana: `notebooks/S12/S12_ML_Challenge.ipynb` o `notebooks/S14/S14_PCA_Modelos.ipynb`.
2. Verificar que `ID_ESTUDIANTE = 26`.
3. Ejecutar *Entorno de ejecución → Reiniciar y ejecutar todo*.
4. Los reportes se generan en `reports/S12/` y `reports/S14/`.

## Licencia
MIT.
