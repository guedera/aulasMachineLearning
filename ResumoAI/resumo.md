# Resumo de Conceitos: Machine Learning

Este documento contém uma síntese dos tópicos abordados sobre redução de dimensionalidade, agrupamento e boas práticas de modelagem.

---

### 📉 1. Redução de Dimensionalidade (PCA, t-SNE, UMAP)
Técnicas utilizadas para simplificar dados complexos com muitas colunas (dimensões).

* **PCA (Principal Component Analysis):**
    * **O que faz:** Projeta os dados em novos eixos (Componentes Principais).
    * **O que maximiza:** A **Variância Explicada**.
    * **Uso principal:** Redução de ruído e aceleração do treinamento de modelos. É uma técnica linear.
* **t-SNE:**
    * **O que faz:** Foca em manter pontos que são vizinhos próximos no espaço de alta dimensão também próximos no espaço reduzido.
    * **Uso principal:** Visualização de clusters em 2D ou 3D.
* **UMAP:**
    * **O que faz:** Semelhante ao t-SNE, mas muito mais rápido e preserva melhor a estrutura global dos dados (a relação entre grupos distantes).

---

### 🧩 2. Agrupamento (Clustering)
* **K-Means:** Algoritmo que agrupa dados em *K* grupos baseando-se na proximidade dos centros (centroides).
* **Sensibilidade:** O K-Means é altamente sensível a:
    1.  **Escala dos dados:** Exige normalização/padronização.
    2.  **Outliers:** Pontos extremos puxam os centros para longe.
    3.  **Inicialização:** Onde os centros começam afeta o resultado final.
    4.  **Ordem dos dados:** Pode influenciar a convergência inicial.

---

### ⚙️ 3. Processos e Validação
* **Pipeline:** Uma "esteira de produção" que agrupa todos os passos (limpeza, escala, redução e modelo) em um único objeto. Garante que os dados de teste sigam exatamente as mesmas regras dos dados de treino.
* **Data Leakage (Vazamento de Dados):** O erro de deixar informações do conjunto de teste "vazarem" para o treino (ex: calcular a média de todos os dados antes de separar o teste). Isso cria modelos "falsamente perfeitos".
* **k-fold CV (Validação Cruzada):**
    * Divide os dados em $k$ partes.
    * Treina e valida o modelo $k$ vezes, alternando qual parte é usada para teste.
    * **Objetivo:** Medir a consistência e a capacidade de generalização do modelo.

---

### 💡 Conclusão
Para um projeto robusto: use **Pipelines** para evitar **Data Leakage**, valide com **k-fold CV** e utilize **PCA/UMAP** para entender a estrutura e reduzir a complexidade dos seus dados.