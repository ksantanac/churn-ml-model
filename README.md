# 📊 Churn Prediction Model - Telecom

Este repositório implementa modelos de **Machine Learning** para prever o **churn de clientes em telecomunicações**, utilizando tanto **Regressão Logística** quanto **Random Forest**.  
O objetivo é identificar clientes com maior propensão a cancelar o serviço, permitindo ações proativas de retenção.  

---

## 📂 Estrutura do Projeto

```
churn-ml-model-main/
├─ README.md
├─ requirements.txt
└─ src/
   ├─ LogisticRegression/
   │  └─ telecom_predict_logistc.ipynb
   └─ RandomForest/
      ├─ telecom_predict_forest.ipynb
      ├─ telecom_predict_forest_test.ipynb
      ├─ pipeline_churn.pkl
      └─ data/
         └─ telecom_churn.csv
```

---

## 🗃️ Dataset

- **Arquivo**: `telecom_churn.csv`
- **Entradas**:
  - Demográficas: `gender`, `SeniorCitizen`, `Partner`, `Dependents`
  - Relacionamento: `tenure`, `PhoneService`, `MultipleLines`, `InternetService`
  - Serviços adicionais: `OnlineSecurity`, `OnlineBackup`, `DeviceProtection`, `TechSupport`, `StreamingTV`, `StreamingMovies`
  - Contrato e cobrança: `Contract`, `PaperlessBilling`, `PaymentMethod`, `MonthlyCharges`, `TotalCharges`
- **Saída (Target)**: `Churn` (Yes/No)

---

## 🔄 Pré-Processamento

- Conversão de colunas numéricas (`TotalCharges` para float, tratamento de missing values).
- Transformação de variáveis binárias `Yes/No → 1/0`.
- One-Hot Encoding para variáveis categóricas (`Contract`, `PaymentMethod`, `InternetService`, etc.).
- Normalização de variáveis numéricas (`StandardScaler`).
- Balanceamento do dataset com **SMOTE** para corrigir desbalanceamento de classes.

---

## 🤖 Modelos

### 1️⃣ Logistic Regression
- Implementado em: `src/LogisticRegression/telecom_predict_logistc.ipynb`
- **Pipeline**:
  - Pré-processamento de variáveis
  - Balanceamento com SMOTE
  - Treinamento do modelo de Regressão Logística
- **Pontos fortes**:
  - Interpretação simples (coeficientes indicam peso de cada feature)
  - Modelo baseline eficiente
- **Métricas**:
  - Acurácia, Precisão, Recall e F1-Score
  - Matriz de confusão para análise detalhada

---

### 2️⃣ Random Forest
- Implementado em:  
  - `src/RandomForest/telecom_predict_forest.ipynb` (treinamento e avaliação)  
  - `src/RandomForest/telecom_predict_forest_test.ipynb` (validação e testes)
- **Pipeline**:
  - Pré-processamento completo
  - Aplicação de SMOTE
  - Treinamento com `RandomForestClassifier` (GridSearchCV para otimização de hiperparâmetros)
  - Persistência do modelo em `pipeline_churn.pkl`
- **Pontos fortes**:
  - Maior robustez e acurácia
  - Melhor performance em detectar clientes propensos a churn
- **Métricas**:
  - Acurácia geral
  - Curva ROC e AUC
  - Relatório de classificação detalhado

---

## 📈 Avaliação

- **Logistic Regression**: bom baseline, fornece interpretabilidade.
- **Random Forest**: melhor desempenho preditivo, indicado para produção.
- Métricas utilizadas:
  - ✅ Accuracy  
  - ✅ Precision  
  - ✅ Recall  
  - ✅ F1-Score  
  - ✅ ROC-AUC  

---

## 💾 Persistência

- O modelo final de Random Forest é salvo em:
  ```
  src/RandomForest/pipeline_churn.pkl
  ```
- Pode ser carregado diretamente com `joblib` ou `pickle`.

---

## ⚙️ Como Reproduzir

1. Clonar este repositório:
   ```bash
   git clone <repo_url>
   cd churn-ml-model-main
   ```
2. Instalar dependências:
   ```bash
   pip install -r requirements.txt
   ```
3. Executar os notebooks em:
   - `src/LogisticRegression/` → regressão logística
   - `src/RandomForest/` → random forest

---

## 👨‍💻 Autor 
Projeto desenvolvido para estudo e aplicação prática de **Machine Learning em churn prediction**.
