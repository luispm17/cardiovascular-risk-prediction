# Resumen final del proyecto

## Proyecto

**Título:** Predicción explicable del riesgo cardiovascular a 10 años.

El objetivo del proyecto fue construir y comparar tres enfoques para estimar la probabilidad de sufrir un evento cardiovascular a 10 años:

- WHO 2019 Cardiovascular Risk Chart.
- Regresión logística.
- Gradient Boosting.

La variable objetivo utilizada fue:

- `EVENTO_CV_10_ANIOS`

Las variables predictoras utilizadas fueron:

- `EDAD`
- `HOMBRE`
- `FUMADOR_ACTUAL`
- `PRESION_SISTOLICA`
- `IMC`

## Datos finales

El conjunto final de modelado se dividió en entrenamiento y test de forma estratificada.

| Conjunto | Participantes | Eventos | Prevalencia |
|---|---:|---:|---:|
| Entrenamiento | 2596 | 307 | 11.83 % |
| Test | 650 | 77 | 11.85 % |

El conjunto de test se reservó exclusivamente para la evaluación final.

## Umbrales finales

Los umbrales se fijaron antes de evaluar el conjunto de test:

| Modelo | Umbral final |
|---|---:|
| WHO 2019 | 10.00 % |
| Regresión logística | 11.23 % |
| Gradient Boosting | 10.73 % |

No se seleccionaron nuevos umbrales utilizando el conjunto de test.

## Resultados probabilísticos en test

| Modelo | ROC-AUC | Average Precision | Brier score |
|---|---:|---:|---:|
| WHO 2019 | 0.7735 | 0.3588 | 0.0930 |
| Regresión logística | 0.7752 | 0.3501 | 0.0912 |
| Gradient Boosting | 0.7973 | 0.3854 | 0.0885 |

Gradient Boosting obtuvo el mejor rendimiento probabilístico global en test.

## Resultados de clasificación en test

| Modelo | Sensibilidad | Especificidad | F1-score | Balanced accuracy | Falsos negativos | Falsos positivos |
|---|---:|---:|---:|---:|---:|---:|
| WHO 2019 | 0.8571 | 0.5620 | 0.3350 | 0.7095 | 11 | 251 |
| Regresión logística | 0.7792 | 0.6440 | 0.3519 | 0.7116 | 17 | 204 |
| Gradient Boosting | 0.8052 | 0.6457 | 0.3626 | 0.7255 | 15 | 203 |

## Interpretación final

La evaluación final muestra que ningún modelo domina absolutamente todos los criterios.

**WHO 2019** destaca por su alta sensibilidad y por detectar el mayor número de eventos reales. Es el modelo que deja menos falsos negativos, aunque genera más falsos positivos.

**Regresión logística** destaca por su interpretabilidad y por una calibración global muy cercana a la prevalencia real del conjunto de test. Es una alternativa sólida cuando se prioriza explicar el efecto de cada variable.

**Gradient Boosting** obtiene el mejor rendimiento global en test. Presenta el mejor ROC-AUC, el mejor Average Precision, el mejor Brier score, el mejor F1-score y la mejor balanced accuracy.

## Conclusión

El modelo con mejor rendimiento global final fue:

**Gradient Boosting**

Sin embargo, la elección del modelo depende del objetivo:

- Para maximizar la detección de eventos: **WHO 2019**.
- Para obtener interpretabilidad y buena calibración: **Regresión logística**.
- Para maximizar rendimiento predictivo global: **Gradient Boosting**.

## Nota metodológica

El conjunto de test se utilizó únicamente para evaluación final.  
No se ajustaron modelos, hiperparámetros ni umbrales utilizando los resultados del test.

Fecha de generación del resumen: 2026-07-22 16:47:44