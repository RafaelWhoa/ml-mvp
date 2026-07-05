# 📊 Minimal viable product: Classificação de Tipos de Feijão com Machine Learning

Projeto de classificação multiclasse desenvolvido como MVP para a Sprint de Machine Learning & Analytics.

🚀 Sprint: Machine Learning & Analytics  
Aluno: Rafael Henrique da Costa  
RA: 4052025002012  
Turma: 40530010056_20260_01  

## Google Colab  
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1xNfA3sqnJB6ipBI-46IZrVOQhXCvHTI0?usp=sharing)

## 📋 Sobre o Projeto

O objetivo é classificar grãos de feijão em sete variedades distintas — Barbunya, Bombay, Cali, Dermason, Horoz, Seker e Sira — com base em características morfológicas extraídas de imagens, como área, perímetro, comprimento dos eixos e fatores de forma, eliminando a necessidade de inspeção visual humana.

## 📊 Dataset

- **Nome:** Dry Bean Dataset
- **Fonte:** [Kaggle](https://www.kaggle.com/datasets/muratkokludataset/dry-bean-dataset)
- **Registros:** 13.611
- **Features:** 16 variáveis numéricas morfológicas
- **Variável-alvo:** `Class` — 7 variedades de feijão
- **Valores ausentes:** Nenhum

## 🔍 Principais Descobertas da Análise Exploratória

- Dataset com escalas muito distintas entre features, exigindo normalização
- Outliers presentes em praticamente todas as features — variação biológica natural
- `Area` e `ConvexArea` com correlação de 1.0 — `ConvexArea` removida por redundância
- Desbalanceamento moderado: Dermason com 26% vs Bombay com apenas 3,8%

## 🤖 Modelos Treinados

| Modelo | Configuração | Acurácia Teste |
|---|---|---|
| KNN | Baseline (sem tratamento) | 72,71% |
| KNN | StandardScaler | 92,51% |
| KNN | RobustScaler | 92,14% |
| KNN | Baseline + sem ConvexArea | 82,78% |
| **KNN** | **StandardScaler + sem ConvexArea + K=26** | **92,62%** |
| Random Forest | Baseline | 92,51% |
| Random Forest | StandardScaler | 92,54% |
| Random Forest | RobustScaler | 92,54% |
| Random Forest | Baseline + sem ConvexArea | 92,36% |

## ⚙️ Otimização

O hiperparâmetro K do KNN foi ajustado via busca manual com cross validation de 5 folds, testando valores de K=1 até K=37. K=26 foi selecionado por apresentar a maior média de acurácia (0.9229) com o menor desvio padrão (0.0021) entre os folds.

## 🏆 Melhor Resultado

**KNN com StandardScaler, sem ConvexArea e K=26**, atingindo 92,62% de acurácia no conjunto de teste com F1-score macro de 0.94 e overfitting de apenas 0,22%. O Bombay foi classificado com 100% de precisão em todos os modelos, confirmando sua distinção morfológica em relação às demais variedades.

## 🛠️ Tecnologias Utilizadas

- Python 3
- Pandas
- Seaborn / Matplotlib
- Scikit-learn
