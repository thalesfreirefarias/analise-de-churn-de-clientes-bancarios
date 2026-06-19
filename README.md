# analise-de-churn-de-clientes-bancarios
Analisar o comportamento de churn de clientes bancários para identificar padrões relacionados à saída de clientes da base e gerar insights que possam apoiar ações de retenção.

---

## 📌 Project Overview

Python project focused on ** Rent Analysis**

### Avarage Rent value by accomodation type

```
dados.groupby('Tipo').mean(numeric_only=True).round(2)

Get just numeric values to calculate mean

media = round(dados.groupby('Tipo')['Valor'].mean(),2).sort_values(ascending=True)
print(media)

Get especific values on Type Accomodation.
```

### Bar visualization

```
df_preco_tipo = dados.groupby('Tipo')[['Valor']].mean().sort_values('Valor')

df_preco_tipo.plot(kind='barh', figsize=(14, 10), color ='purple');
```
<table>
  <tr>
    <td align="center">
      <a href="#" title="Age">
        <img src="1.png" width="1000" alt="Rent"/><br>
      </a>
    </td>
  </tr>
</table>
---


## Rent

This Python project presents :
Revenue by Brand
Revenue and Sales Quantity by Month
Revenue by Continent


```
Codes:
AnoMes = FORMAT('Planilha1'[Data da Venda], "YYYY-MM")

AnoMesOrdenacao = 
YEAR('Planilha1'[Data da Venda]) * 100 +
MONTH('Planilha1'[Data da Venda])

Mes = FORMAT('Planilha1'[Data da Venda], "MMM")
MesNum = MONTH('Planilha1'[Data da Venda])
```

---

###Filter Information

```
Code :
selecao = (df['Quartos'] >= 2) & (df['Valor'] < 3000) & (df['Area'] > 70)
df[selecao]

dados_selecao = pd.read_csv(url, usecols=['Id', 'Year_Birth', 'Income'])
dados_selecao.sort_values(by='Year_Birth', ascending=True).head(5)

```

###New Columns

```
dados['Descricao'] = dados['Tipo'] + ' em ' + dados['Bairro'] + ' com ' + \
                                        dados['Quartos'].astype(str) + ' quarto(s) ' + \
                                        ' e ' + dados['Vagas'].astype(str) + ' vaga(s) de garagem.'
dados.head()

dados['Possui_suite'] = dados['Suites'].apply(lambda x: "Sim" if x > 0 else "Não")
dados

dados['Valor_por_ano'] = dados['Valor_por_mes'] * 12 + dados['IPTU']
dados.head()
```



---

## 🛠️ Technologies Used

* Python as Pandas
* Google Colab
* Matplotlib
* Seaborn
* GitHub





---

## 🤝 Author

<table>
  <tr>
    <td align="center">
      <a href="https://www.linkedin.com/in/thalesfreirefarias/" target="_blank">
        <img src="grecia.jpg" width="100" alt="Thales Farias"/><br>
        <sub><b>Thales Farias</b></sub>
      </a>
    </td>
  </tr>
</table>


baixo está a estrutura já adaptada.

1. Importação
python


import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
sns.set(style="whitegrid")
plt.rcParams["figure.figsize"] = (10, 6)
2. Leitura da base
python


df = pd.read_csv("bank_churn.csv")
df.head()
3. Entendimento inicial
python


df.shape
df.info()
df.describe()
df.isnull().sum()
4. Duplicados
python


df.duplicated().sum()
5. Remover identificador da análise
python


df_analysis = df.drop(columns=["customer_id"], errors="ignore")
df_analysis.head()
6. Taxa geral de churn
python


churn_rate = df_analysis["churn"].mean()
print(f"Churn rate: {churn_rate:.2%}")
7. Distribuição de churn
python


sns.countplot(x="churn", data=df_analysis)
plt.title("Customer Churn Distribution")
plt.xlabel("Churn")
plt.ylabel("Count")
plt.show()
8. Idade por churn
python


sns.boxplot(x="churn", y="age", data=df_analysis)
plt.title("Age Distribution by Churn Status")
plt.show()
9. País por churn
python


sns.countplot(x="country", hue="churn", data=df_analysis)
plt.title("Churn by Country")
plt.show()
10. Cliente ativo por churn
python


sns.countplot(x="active_member", hue="churn", data=df_analysis)
plt.title("Churn by Active Membership")
plt.show()
11. Número de produtos por churn
python


sns.countplot(x="products_number", hue="churn", data=df_analysis)
plt.title("Churn by Number of Products")
plt.show()
12. Score de crédito por churn
python


sns.boxplot(x="churn", y="credit_score", data=df_analysis)
plt.title("Credit Score by Churn Status")
plt.show()
13. Saldo por churn
python


sns.boxplot(x="churn", y="balance", data=df_analysis)
plt.title("Balance by Churn Status")
plt.show()
14. Tempo de relacionamento por churn
python


sns.boxplot(x="churn", y="tenure", data=df_analysis)
plt.title("Tenure by Churn Status")
plt.show()
15. Cartão de crédito por churn
python


sns.countplot(x="credit_card", hue="churn", data=df_analysis)
plt.title("Churn by Credit Card Ownership")
plt.show()
16. Salário estimado por churn
python


sns.boxplot(x="churn", y="estimated_salary", data=df_analysis)
plt.title("Estimated Salary by Churn Status")
plt.show()
Insights em tabela resumida
No notebook, depois dos gráficos, você pode montar algo assim:

python


churn_by_country = df_analysis.groupby("country")["churn"].mean().sort_values(ascending=False)
print(churn_by_country)
churn_by_active = df_analysis.groupby("active_member")["churn"].mean()
print(churn_by_active)
churn_by_products = df_analysis.groupby("products_number")["churn"].mean()
print(churn_by_products)
Isso ajuda a sair do visual e mostrar também análise numérica.

Texto de insights para usar no notebook
Você pode escrever no final algo nessa linha:

markdown


## Key Insights
- The overall churn rate indicates that customer attrition is concentrated in specific segments rather than evenly distributed across the customer base.
- Older customers appear to present higher churn levels compared to younger groups.
- Active members tend to show lower churn rates, suggesting that engagement is an important retention factor.
- The number of products and country distribution may also influence customer churn behavior.
- Financial profile variables such as balance and credit score may provide additional signals for identifying risk patterns.
Conclusão de negócio
markdown


## Business Conclusion
The analysis suggests that churn is likely influenced by a combination of demographic profile, engagement level, and product relationship. Customers with lower engagement and specific account characteristics may deserve greater retention attention. These findings could support more targeted retention strategies in banking environments.
README ajustado para esse dataset
Você pode usar este texto:

markdown


# Bank Customer Churn Analysis
## Project Overview
This project analyzes customer churn behavior in a banking dataset to identify patterns associated with customer attrition. The analysis focuses on demographic, financial, and behavioral variables that may influence churn.
## Objective
Understand which customer characteristics are more frequently associated with churn and generate business insights that could support retention strategies.
## Tools Used
- Python
- Pandas
- Matplotlib
- Seaborn
- Google Colab
## Dataset Columns
- customer_id
- credit_score
- country
- gender
- age
- tenure
- balance
- products_number
- credit_card
- active_member
- estimated_salary
- churn
## Analysis Questions
- What is the overall churn rate?
- Do older customers churn more?
- Does country influence churn?
- Are active members less likely to churn?
- Does the number of products affect retention?
- Are financial indicators such as balance and credit score related to churn?
## Key Insights
- Churn is concentrated in specific customer segments.
- Customer activity level appears strongly related to retention.
- Age, country, and number of products may influence churn patterns.
- Balance and credit profile can provide additional retention signals.
## Author
Thales Freire Cavalcante Farias
Minha recomendação prática
Com essas colunas, seu projeto ficou até melhor do que o exemplo inicial, porque:

está limpo;
tem variáveis boas;
dá para fazer análise visual e numérica;
é fácil de explicar em entrevista.
O que eu faria amanhã
carregar a base;
calcular churn geral;
fazer 4 gráficos primeiro:
idade
país
active_member
products_number
escrever 3 insights iniciais;
depois expandir para saldo, score e tenure.
Resposta curta
Sim, essas colunas são ótimas para o projeto.
Você já consegue montar uma análise bem apresentável com elas.

Se quiser, o próximo passo mais útil é eu te entregar o notebook inteiro já escrito em Python, em bloco corrido, pronto para colar no Google Colab.




eu só copiei os seus dados e subi no github tudo bem?


Sim - tudo bem como primeiro passo.

Voce nao fez nada errado por subir uma versao baseada no roteiro que eu te passei. Para portfolio inicial, isso serve para:

ganhar ritmo;
aprender a estrutura de um projeto;
ter uma primeira entrega visivel;
perder o medo de publicar.
O ponto importante
O que voce nao deve fazer e apresentar isso como se fosse:

um projeto totalmente original do zero;
um trabalho profundo seu sem apoio;
prova de dominio avancado.
Mas se a realidade for algo como:

"usei uma estrutura guiada, adaptei ao dataset e publiquei como parte do meu aprendizado e portfolio"

entao isso esta totalmente ok.

Em outras palavras
Tem diferenca entre:

aceitavel
usar um roteiro;
seguir uma estrutura sugerida;
adaptar codigo;
entender o que esta fazendo;
publicar como projeto de aprendizado;
problema
copiar sem entender nada;
nao conseguir explicar o projeto;
dizer que criou tudo sozinho se nao criou;
publicar algo que voce nao sabe defender em entrevista.
Regra mais importante
Se alguem te perguntar sobre o projeto, voce precisa conseguir explicar:

qual era o objetivo;
quais colunas voce analisou;
por que removeu customer_id;
o que churn significa;
quais variaveis pareceram mais relevantes;
quais insights encontrou;
o que faria na proxima versao.
Se voce consegue fazer isso, o projeto ja e seu o suficiente para portfolio de entrada.

Como enquadrar esse projeto de forma honesta
Na sua cabeca e na sua narrativa, pense assim:

"Eu construí um projeto orientado de análise de churn para praticar Python, análise exploratória e geração de insights."

Isso e uma narrativa honesta e boa.

O que eu recomendo fazer agora para deixar mais seu
Faca pelo menos 3 pequenas personalizacoes:

1. Reescreva os insights com suas palavras
Nao deixe o texto final igual ao que eu sugeri.
Olhe os graficos e escreva sua propria leitura.

2. Ajuste o README
Pode usar a estrutura, mas mude:

a introducao;
as perguntas;
os insights finais;
os proximos passos.
3. Inclua uma observacao sua
Por exemplo:

um grafico extra;
uma tabela adicional;
uma conclusao de negocio mais sua;
uma sugestao de retencao.
Isso ja tira o projeto da zona de "copiei e subi" e leva para "usei um guia e adaptei".

Minha resposta honesta
Para o momento em que voce esta, sim, tudo bem.
Nao e fraude usar uma estrutura de apoio para montar um projeto de portfolio inicial.

O que define se isso esta ok ou nao e:

se voce entendeu o que subiu
e se consegue evoluir a partir disso
O que fazer antes de divulgar mais
Antes de usar esse projeto em candidatura ou post, eu faria este checklist:

voce entende cada grafico?
voce sabe explicar o dataset?
voce sabe o que e churn?
voce sabe por que usou essas colunas?
voce sabe dizer 3 insights?
voce sabe dizer 1 melhoria futura?
Se a resposta for sim, entao pode usar sem problema.

O que eu faria no seu lugar agora
abrir o notebook;
revisar linha por linha;
reescrever os insights com sua voz;
melhorar o README;
subir uma versao 2 ainda hoje ou amanha.
Isso ja deixa o projeto muito mais autentico.

Conclusao
Sim, tudo bem ter usado a estrutura e subido no GitHub.
Para portfolio inicial, o importante nao e ter feito tudo sozinho do zero - e sim:

entender o projeto;
conseguir explicar;
e mostrar evolucao nas proximas entregas.
O que vai te diferenciar nao e este primeiro projeto ser 100% original.
E voce conseguir transformar os proximos em algo cada vez mais seu.

Se quiser, eu posso fazer o melhor proximo passo agora: revisar com voce o README e os insights para deixar esse projeto com a sua cara.

