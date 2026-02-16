# NASA_turbofan_CMAPSS
Projeto de Machine Learning para previsão de falha de motores (RUL) utilizando o dataset FD001 e modelos baseados em árvores com GridSearch e validação cruzada.

# Previsão de Vida Útil Remanescente (RUL) – Dataset FD001

## 1. Coleta de Dados

O conjunto de dados utilizado foi o FD001, composto por séries temporais multivariadas que representam o funcionamento de uma frota de 100 motores do mesmo tipo.

Cada linha do dataset representa um ciclo operacional de um motor específico, contendo:

- Identificador da unidade (motor)
- Número do ciclo operacional
- 3 configurações operacionais
- 21 medições de sensores

No conjunto de treinamento, os motores operam até a falha completa.  
No conjunto de teste, as séries temporais terminam antes da falha, sendo necessário prever a Vida Útil Remanescente (RUL).

O dataset considera:
- Uma única condição operacional
- Um único modo de falha (degradação do HPC)
- Presença de ruído nos sensores

---

## 2. Modelagem

### Pré-processamento

- Separação entre conjunto de treino e teste
- Definição da variável alvo (RUL)
- Aplicação de validação cruzada (5 folds)

### Modelos Avaliados

Foram testados modelos de aprendizado de máquina baseados em árvores:

- ExtraTrees Regressor
- XGBoost Regressor

### Validação

Foi utilizado GridSearch com validação cruzada para otimização dos hiperparâmetros.

Melhores resultados obtidos:

- **RMSE:** 20.06  
- **MAE:** 15.29  
- **R²:** 0.767  

Os resultados indicam que o modelo consegue explicar aproximadamente 76,7% da variabilidade da variável alvo.

---

## 3. Conclusões

O modelo apresentou bom desempenho na previsão da Vida Útil Remanescente dos motores.

Os resultados mostram:

- Boa capacidade de generalização
- Erro médio absoluto de aproximadamente 15 ciclos
- Estabilidade entre os folds da validação cruzada

Apesar dos bons resultados, melhorias adicionais podem ser obtidas com:
- Engenharia de atributos
- Ajuste mais refinado de hiperparâmetros
- Técnicas de ensemble

O estudo demonstra que modelos baseados em árvores são eficazes para problemas de previsão de falha em séries temporais industriais.
