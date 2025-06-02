# ✈ Projeto: Análise de Sentimentos em Avaliações de Companhias Aéreas

## 📍 Objetivo

Este projeto teve como objetivo analisar os sentimentos expressos por passageiros em avaliações de viagens aéreas, a partir de um dataset com informações textuais e numéricas. O objetivo final foi entender quais fatores mais impactam a experiência do cliente e calcular o impacto dos atrasos no Net Promoter Score (NPS) de três companhias aéreas.


## 🔍 Etapas realizadas

### 1️⃣ Importação e limpeza dos dados
- Corrigi tipos incorretos de colunas (`Overall_Rating`, `Review Date`).
- Removi duplicatas e tratei dados faltantes usando mediana para variáveis numéricas e “Unknown” para categóricas.

### 2️⃣ Análise exploratória (EDA)
- Realizei análises univariadas e bivariadas para entender distribuições, outliers e correlações.
- Usei gráficos para visualizar a distribuição das notas por companhia e por modelo de aeronave.

### 3️⃣ Processamento de texto (NLP)
- Apliquei limpeza textual (remoção de stopwords, lematização) nas colunas `Review` e `Review_Title`.
- Vetorizei os textos usando **TF-IDF** para alimentar modelos de machine learning.

### 4️⃣ Modelagem preditiva
- Treinei e comparei três modelos (RandomForest, LogisticRegression, XGBoost) usando duas abordagens:

  ✅ Apenas os textos das reviews  
  ✅ Apenas as notas numéricas separadas (`Seat Comfort`, `Cabin Staff Service`, etc.)

- O modelo vencedor foi o **XGBoost usando as notas numéricas**, com acurácia de ~78%.

### 5️⃣ Análise final: impacto de atrasos no NPS
- Como não havia coluna explícita de atraso, detectei atrasos usando palavras-chave no texto (`delay`, `cancelled`, `late`, etc.).
- Calculei o NPS para as três companhias com maior volume de dados (CityJet, Aerolineas Argentinas, QantasLink), comparando os grupos com e sem atraso.
- Observei variações claras no NPS entre esses grupos.


## 📊 Principais resultados (NPS)

| Companhia               | Com Atraso       | Sem Atraso        |
|-------------------------|------------------|-------------------|
| CityJet                 | -63.83%          | -49.06%           |
| Aerolineas Argentinas   | -66.67%          | -34.62%           |
| QantasLink              | -43.90%          | -57.63%           |

✅ Em geral, todos os NPS foram negativos, mostrando mais detratores do que promotores.  
✅ Aerolineas Argentinas e CityJet apresentaram NPS muito mais negativos com atraso, sugerindo forte impacto perceptivo.  
✅ QantasLink teve um NPS ligeiramente melhor com atraso, possivelmente porque outros fatores pesam mais na experiência negativa.


## 📝 Conclusões e recomendações

Com base na análise dos reviews, proponho as seguintes ações de melhoria para as companhias aéreas:

- **Gestão de atrasos:**  
  Investir fortemente em comunicação proativa, compensações e serviços durante atrasos, já que esses eventos afetam fortemente o NPS, especialmente para Aerolineas Argentinas e CityJet.

- **Qualidade do atendimento:**  
  Como `Cabin Staff Service` e `Seat Comfort` mostraram alta correlação com a nota geral, treinar e capacitar melhor as equipes a bordo pode aumentar a satisfação mesmo em situações adversas.

- **Investimento em conforto e entretenimento:**  
  Apesar de menos correlacionados, serviços como Wi-Fi e entretenimento a bordo ainda aparecem nas reclamações negativas — pequenos investimentos nessas áreas podem diferenciar a experiência.

- **Escuta ativa das reviews:**  
  Monitorar ativamente os textos das avaliações permite identificar rapidamente novos padrões de insatisfação e atuar antes que eles se espalhem.


## 🚀 Próximos passos

Se desejar expandir este projeto:
- Explorar modelos de linguagem mais avançados (ex.: BERT) para capturar nuances dos textos.
- Implementar dashboards dinâmicos para monitoramento contínuo das métricas.
- Avaliar padrões regionais ou por tipo de viagem (negócios vs. lazer).
