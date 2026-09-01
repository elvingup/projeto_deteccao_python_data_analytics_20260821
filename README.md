# Detecção de Fraudes em Transações Bancárias 💳
[Jupyter Notebook no Google Colab](https://colab.research.google.com/github/elvingup/projeto_deteccao_python_data_analytics_20260821/blob/main/projeto_deteccao_python_data_analytics_20260821.ipynb) para criar um sistema de Data Analytics que serve para a detecção de fraudes de transações registradas no [dataset creditcard](https://storage.googleapis.com/download.tensorflow.org/data/creditcard.csv)

## 📌 Visão Geral do Projeto
Este projeto de Data Analytics e Machine Learning tem como objetivo identificar transações fraudulentas em cartões de crédito. Indo além das métricas tradicionais de Machine Learning (como Acurácia e Recall), este projeto introduz uma **Análise de Impacto Financeiro**, traduzindo o desempenho do algoritmo em valor de negócio real (ROI e redução de prejuízos operacionais).

O notebook completo foi desenvolvido no [Google Colab](https://colab.research.google.com/) e utiliza dados do famoso *Credit Card Fraud Detection Dataset*.

## 📊 Sobre os Dados
Os dados consistem em transações de cartões de crédito realizadas em dois dias, onde temos 492 fraudes em quase 285.000 transações.
* **Desbalanceamento Extremo:** As fraudes representam apenas `0.172%` do total de transações.
* **Features:** Por questões de confidencialidade, as features `V1` a `V28` são componentes principais obtidos via transformação PCA. As únicas features originais são `Time` e `Amount` (valor da transação).

## 🛠️ Tecnologias e Bibliotecas Utilizadas
* **Linguagem:** Python 3.x
* **Manipulação e Análise:** Pandas, NumPy
* **Visualização:** Matplotlib, Seaborn, SHAP (Explainable AI)
* **Machine Learning:** Scikit-Learn, XGBoost, Imbalanced-learn (SMOTE)

## 🚀 Metodologia e Etapas do Projeto

1. **Feature Engineering e Pré-processamento:**
   - Transformação algorítmica da feature `Amount` utilizando `np.log1p` (Log) e `StandardScaler` para calibrar a escala e evitar vieses no modelo.
2. **Estratégias de Balanceamento:**
   - Testes comparativos entre *Undersampling*, *Oversampling (SMOTE)* e ajuste de pesos da classe (`class_weight="balanced"`).
3. **Modelagem:**
   - **Baseline:** Regressão Logística (Pipeline com StandardScaler) para estabelecer métricas iniciais.
   - **Ensembles:** Random Forest e XGBoost.
4. **Otimização de Hiperparâmetros:**
   - Utilização do `GridSearchCV` no XGBoost (focado em otimizar o *Recall*) com validação cruzada (`cv=3`).
5. **Explicabilidade do Modelo (XAI):**
   - Uso da biblioteca **SHAP** para entender o impacto e a contribuição de cada feature nas decisões do modelo XGBoost.

## 💰 Resultados e Impacto Financeiro (Valor de Negócio)

A avaliação do modelo final (XGBoost) não se limitou à matriz de confusão convencional, mas incorporou o custo real de Falsos Positivos (atrito com cliente) e Falsos Negativos (fraude efetivada).

* **Desempenho ML:** O XGBoost alcançou um F1-Score de **0.85** para a classe de fraude (Precision: 0.94 / Recall: 0.78).
* **Economia Gerada:** R$ 11.530,88 economizados no conjunto de teste.
* **Retorno Sobre Investimento (ROI):** **59.71%**.
* **Threshold Tuning Financeiro:** Através da simulação de custos, identificou-se que ajustar o limiar de decisão (Threshold) para **0.49** minimiza o prejuízo total da operação para R$ 6.997,49.

## ⚙️ Como Executar o Projeto

1. **Acesse o Notebook:**
   Você pode rodar este projeto diretamente na nuvem clicando no arquivo `projeto_deteccao_python_data_analytics_20260821.ipynb` neste repositório e selecionando a opção "Open in Colab".
2. **Clonando localmente:**
   Se preferir, pode fazer o *fork* deste repositório no GitHub e clonar o repositório localmente. Em seguida, execute o arquivo `projeto_deteccao_python_data_analytics_20260821.ipynb` localmente. A instalação via CLI pode ser feita executando
   ```bash
   pip install -r requirements.txt
   ```
