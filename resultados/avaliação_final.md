# Comparação e Escolha do Melhor Modelo

## Com base nas métricas apresentadas:

### Random Forest
- **Acurácia no teste:** 0.99992927864215
- **Acurácia no treinamento:** 0.9999393807133677
- **Validação cruzada (5-fold):**
  - Acurácia média: 0.9999151325944784
  - Desvio padrão: 4.021e-05
- **Métricas detalhadas:** Precision, Recall e F1-score iguais ou próximos de 1.0, indicam um desempenho excelente tanto para classes 0 quanto 1.

### LightGBM
- **Acurácia no teste:** 0.99998585572843
- **Acurácia no treinamento:** 0.9999939380713367
- **Validação cruzada (5-fold):**
  - Acurácia média: 0.9999939381080836
  - Desvio padrão: 1.212e-05
- **Métricas detalhadas:** Precision, Recall e F1-score iguais ou próximos de 1.0, indicam previsões perfeitas em várias métricas.

## Qual modelo mais diferenciado?

- **LightGBM** tem métricas um pouco superiores ao **Random Forest** em termos de precisão global (acurácia mais alta tanto no teste quanto na validação cruzada).
- Os resultados da validação cruzada mostram uma consistência maior no desempenho do **LightGBM**, com desvio padrão menor e valores próximos de 1.0 em todos os folds.

## Exatidão e Escolha Final

**LightGBM** se destaca como o modelo mais exato devido a:
- Acurácia superior em teste, treinamento e validação cruzada.
- Desvio padrão menor, indicando maior consistência.
- Previsões perfeitas (com base em métricas como Recall e F1-Score) em ambas as classes.

Mesmo que a diferença entre os modelos seja mínima, eu escolhi o **LightGBM**, pois ele apresenta métricas ligeiramente melhores e maior estabilidade.