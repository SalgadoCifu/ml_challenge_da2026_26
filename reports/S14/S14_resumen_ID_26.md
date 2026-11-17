# S14. Resumen del análisis (ID 26)

## Datos de partida
- Muestra: 35.000 pedidos (24.500 de entrenamiento, 5.250 de validación y 5.250 de prueba sin usar).
- Umbral de clasificación: 0,50. Costos didácticos: R$ 8 por falso positivo y R$ 35 por falso negativo.

## PCA
- Variables numéricas iniciales: 24. Componentes que explican al menos el 90 %: 15 (varianza acumulada 0,904).
- Figura: `S14_varianza_acumulada_ID_26.png`

## Resultados en validación
| Experimento | Accuracy | Precision | Recall | F1 | AP | FP | FN | Costo (R$) |
|---|---|---|---|---|---|---|---|---|
| A. Referencia (sin PCA, C=1) | 0,661 | 0,122 | 0,645 | 0,205 | 0,145 | 1.654 | 126 | 17.642 |
| B. PCA 90 % (C=1) | 0,646 | 0,112 | 0,611 | 0,189 | 0,127 | 1.719 | 138 | 18.582 |
| C. PCA 90 % (C=0,1) | 0,645 | 0,112 | 0,614 | 0,190 | 0,130 | 1.727 | 137 | 18.611 |
| D. PCA 90 % (C=10) | 0,646 | 0,112 | 0,611 | 0,189 | 0,126 | 1.721 | 138 | 18.598 |

## Prueba KS sobre `valor_flete` (entrenamiento vs validación)
- D = 0,0144; valor p = 0,3242; alfa = 0,05.
- Hipótesis y decisión: H0 dice que `valor_flete` se comporta igual en entrenamiento y validación, y H1 que se comporta distinto. Con D = 0,0144 y valor p = 0,3242, no se rechaza H0 al 5 %.

## Interpretación
- Modelo elegido y justificación: A (sin PCA, C=1), porque tiene el menor costo en validación (R$ 17.642).
- Utilidad de PCA para este problema: redujo 24 variables numéricas a 15 componentes, pero no ayudó a encontrar más pedidos tardíos.
- Limitación de la prueba KS: mira una sola variable a la vez, y un valor p alto no prueba que los datos sean iguales.
