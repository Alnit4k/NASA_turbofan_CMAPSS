# 🔧 Previsão para Manutenção Preventiva

Projeto de Machine Learning para previsão da **Vida Útil Remanescente (RUL — Remaining Useful Life)** de motores, utilizando o dataset **FD001** (NASA C-MAPSS) e modelos baseados em árvores otimizados com GridSearch e validação cruzada.

## Sobre o Projeto

O objetivo é prever quantos ciclos operacionais restam antes de um motor falhar, permitindo que a manutenção seja planejada de forma **preventiva** em vez de corretiva — reduzindo custos e paradas não programadas.

## Estrutura do Repositório

```
.
├── data/              # Dataset FD001
├── semantix.ipynb     # Notebook com todo o pipeline de análise e modelagem
└── README.md
```

## Dataset

O conjunto de dados **FD001** é composto por séries temporais multivariadas que representam o funcionamento de uma frota de **100 motores** do mesmo tipo. Cada linha representa um ciclo operacional de um motor específico, contendo:

- Identificador da unidade (motor)
- Número do ciclo operacional
- 3 configurações operacionais
- 21 medições de sensores

**Características do dataset:**

| Conjunto | Descrição |
|---|---|
| Treino | Motores operam até a falha completa |
| Teste | Séries terminam antes da falha — é necessário prever o RUL |

- Uma única condição operacional
- Um único modo de falha (degradação do HPC)
- Presença de ruído nos sensores

## Metodologia

### 1. Pré-processamento
- Separação entre conjunto de treino e teste
- Definição da variável alvo (RUL)
- Validação cruzada com 5 folds

### 2. Modelos Avaliados
Modelos de aprendizado de máquina baseados em árvores:

- **ExtraTrees Regressor**
- **XGBoost Regressor**

### 3. Validação e Otimização
Utilização de **GridSearch com validação cruzada** para otimização de hiperparâmetros.

## Resultados

| Métrica | Valor |
|---|---|
| RMSE | 20.06 |
| MAE | 15.29 |
| R² | 0.767 |

O modelo consegue explicar aproximadamente **76,7%** da variabilidade da variável alvo, com erro médio absoluto de cerca de **15 ciclos**.

## Conclusões

- Boa capacidade de generalização
- Estabilidade entre os folds da validação cruzada
- Modelos baseados em árvores se mostraram eficazes para o problema de previsão de falha em séries temporais industriais

### Próximos passos
- Engenharia de atributos adicional
- Ajuste mais refinado de hiperparâmetros
- Técnicas de ensemble

## Como executar

```bash
git clone https://github.com/Alnit4k/Previs-o-para-manuten-o-preventiva.git
cd Previs-o-para-manuten-o-preventiva
jupyter notebook semantix.ipynb
```

## Tecnologias

- Python
- Jupyter Notebook
- scikit-learn (ExtraTrees, GridSearchCV)
- XGBoost
- Pandas / NumPy

## Autor

[Alnit4k](https://github.com/Alnit4k)
