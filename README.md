# Documentação do Projeto: Previsão de Leads para Campanhas

## 1. Vamos começar!
**O que fiz?**  
Crei um modelo de regressão linear para prever os leads gerados. A ideia é simples: usar dados históricos (como alcance, cliques, CPM e impressões) para entender como essas variáveis impactam no desempenho e prever resultados futuros.

**Por que isso é legal?**  
Com isso, consigo compartilhar com o time como otimizar os investimentos e entender o que realmente funciona (ou não) nas campanhas. Afinal, qual cliente não quer leads de qualidade gastando menos, certo? 😉

---

## 2. O que usei?
### **Os dados:**  
- Mais de 10.000 registros detalhados por dia e campanha.  
- Colunas principais: alcance, impressões, CPM, cliques, leads e algumas outras métricas de performance.  

### **O que fiz com os dados?**  
- Tratei os valores ausentes.  
- Renomeei as colunas para facilitar minha vida.  
- Converti os valores monetários e porcentagens para números de verdade (o modelo não lê strings)

### **As ferramentas:**  
- Google Colab
- Python (o meu mais novo queridinho 🐍) com Pandas, NumPy, Scikit-Learn,Matplotlib e Plotly

---

## 3. Mão na massa!
### **O passo a passo:**  
1. **Explorar os dados:**  
   Criei estatísticas básicas e gráficos para entender o comportamento das variáveis. Já viu um mapa de correlação? Pois é, fiz um para identificar o que mais influencia os leads.  

2. **Separar o treino do teste:**  
   Dividi os dados em 80% para treinar o modelo e 20% para testar se ele realmente funciona.  

3. **Rodar os modelos:**  
   Testei vários tipos de regressão (Linear, Ridge, Lasso, etc (Como o meu último professor Calábria sempre pontuava: "só vamos saber qual modelo usar, depois de testar todos."), o modelo com a menor taxa de erro foi a regressão linear clássica. 🏆  

4. **Validar e ajustar:**  
   Ajustei os hiperparâmetros e validei o modelo usando métricas como \( R^2 \), RMSE e MAE.  

---

## 4. O que encontrei?
### **O modelo: DecisionTreeRegressor**  
- \( R^2 \): 0.91 (explica 91% da variação nos dados).  
- MAE (Erro Médio Absoluto): 4.1 leads.  
- RMSE (Raiz do Erro Médio Quadrático): 5.2 leads. 

### **Insights bacanas:**  
- O CPM (custo por mil impressões) tem um impacto negativo nos leads (-0.65 de correlação). É caro e pode não trazer tanto resultado assim.  
- Cliques são poderosos! Quanto mais cliques, mais leads (correlação de 0.78).  (Esse ponto é importante, porque as campanhas de conversão de formulário de leads está ligada diretamente aos cliques, porque a conversão acontece dentro da plataforma do Meta Ads e não em outros domínios).
- Impressões ajudam, mas o impacto é mais discreto do que a gente imaginava.  

---

## 5. Visualizações pra deixar tudo claro
### **Alguns gráficos que usei (e que ficam incríveis no relatório):**  
1. **Mapa de Correlação:** Pra mostrar as relações entre as variáveis principais.  
2. **Gráfico de Resíduos:** Validar se o modelo está "comportado" e os erros estão bem distribuídos.  
3. **Gráfico de Importância das Variáveis:** Destaque para os coeficientes do modelo linear (cliques no topo, claro).  
4. **Simulações:** Curvas mostrando como o CPM e os cliques afetam os leads previstos.  

---

## 6. Conclusão e próximos passos
### **O que rolou:**  
- O modelo funcionou super bem para prever leads com base nos dados históricos.  
- Descobri que algumas variáveis (como cliques) são cruciais, enquanto outras (como impressões) têm impacto menor.  

## 5. Inteligência de Negócio

Trabalhei anos como gestora de tráfego e especialista em mídia online, tive a oportunidade de atuar em diversos segmentos, desde personal branding, marcas com foco mais institucional, e-commerce e lançamentos de infoprodutos. Essa bagagem foi fundamental para interpretar o comportamento dos dados e tomar decisões estratégicas ao lidar com outliers.

### **O que aconteceu com os outliers?**
Ao avaliar os dados fora da curva, decidi **não removê-los**, e aqui está o porquê:  
- A base contém o histórico de campanhas dos últimos dois anos, abrangendo tanto campanhas de captação quanto campanhas de reconhecimento, principalmente em lançamentos.  
- Essas campanhas possuem objetivos muito diferentes, o que explica as discrepâncias em métricas como alcance e impressões. Por exemplo, uma campanha de reconhecimento pode ter altos valores de alcance e impressões, mas menor conversão em leads, enquanto o inverso ocorre em campanhas de captação.  

### **Próximos passos com essa análise**
- A partir desse entendimento, ficou claro que o próximo passo será **segmentar as campanhas por objetivo** (captação, reconhecimento, etc.). Assim, o modelo pode ser ajustado para responder de forma mais linear dentro de cada segmento, refletindo a realidade de cada tipo de campanha. Essa abordagem deve reduzir a variação nas métricas e aumentar a precisão das previsões.
- Outro ponto importante, nas campanhas de conversão (levando para fora da plataforma) uma boa métrica para trazer para o modelo é Landing Page View. E quando a segmentação das campanhas acontecer numa seguda etapa do processo, essa métrica vai ser trabalhada. 

---

## **Resumo da ópera:** 
1. O projeto mostrou que o modelo **Árvore de Decisão** foi o mais adequado para prever leads de campanhas digitais porque conseguiu lidar melhor com as relações não lineares entre as variáveis e os outliers. Sua flexibilidade em criar divisões específicas permitiu capturar as diferenças entre campanhas de captação e reconhecimento, resultando em previsões mais precisas e alinhadas com a realidade dos dados. 🚀  

É super possível prever leads. Então, se você quer prever leads e otimizar campanhas, essa abordagem funciona bem. E, claro, com alguns ajustes, dá pra levar isso a outro nível! 🚀

---

### **Ajustes sugeridos para melhorar ainda mais:**
1. Adicionar variáveis como sazonalidade, segmentação do público ou segmentar as campanhas por seus objetivos. 
3. Validar com cross-validation e melhorar hiperparâmetros.  
4. Incorporar dados de concorrência ou multicanais. 
