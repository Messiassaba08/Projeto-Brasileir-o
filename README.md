# Analise de dados da série A do campeonato brasileiro entre 2013-2023

***** Corrigir cartões por temporada e não ano e corrigir Correlação pontos x Saldos de gols *****



Projeto criado para praticar o uso de Figma, Power BI e Estatística na análise de dados da série A do campeonato brasileiro de futebol de 2013 a 2023.
- Link do Projeto concluído: https://app.powerbi.com/reportEmbed?reportId=c9745383-e81c-4d2a-bb91-61aae2911182&autoAuth=true&ctid=64126139-4352-4cd7-b1fb-2a971c6f69a6
- Link da base de dados: https://www.kaggle.com/datasets/victorhts/brasileiro-srie-a-resultados-2013-2023
- Link do Tutorial de Figma: https://www.youtube.com/watch?v=o5MyY1jCWg8&t=841s
- Link curso gratuito de Power BI: https://www.youtube.com/watch?v=YqH_gTzKZVI&list=PL29iyd7VxXguJm4NiXMKNlh5uNspQsxzv

## Introdução
Esta documentação tem como objetivo principal explicar as decisões voltadas a analise de dados, uso de estatística e da ferramenta de manipulação de dados Power BI. Sendo assim, não irei especificar sobre a criação do dashboard pelo Figma, mas irei deixar o link dos vídeos que usei para auxiliar no uso da ferramenta logo acima. Também deixei o link do curso gratuito de Power BI que realizei para criação do projeto. Lembrando que apenas a vizualização dos cursos não irá desenvolver suas habilidades com as ferramentas se não houver prática. Esse é o objetivo da criação desse projeto. :) 
 
## Perguntas
Inicialmente, antes de manipularmos os dados, devemos nos perguntar o que queremos extrair dos mesmos. Em uma empresa, na maioria das vezes, teremos questionamentos prontos para solucionarmos com o dataset disponibilizado. Dessa forma, torna-se mais interessante, antes da manipulação, a criação de perguntas para que possamos respondê-las ao longo do projeto. Sendo assim, separei as perguntas em cinco categorias: Cartões Amarelos, Cartões Vermelhos, Gols, Aproveitamento e Campeões.

### Cartões Amarelos:
- Qual a média geral de cartões amarelos por jogo e temporada? Além disso, gostaria de poder comparar a média de cartões geral com a média invidial dos clubes.
- Qual foi o comportamento do número de cartões amarelos ao longo dos anos?
- Existe uma relação forte entre o número de cartões amarelos e o aproveitamento dos clubes?
- Quais os clubes com maior média de cartões amarelos por temporada?
### Cartões Vermelhos:
- Qual a média geral de cartões vermelhos por jogo e temporada? Além disso, gostaria de poder comparar a média de cartões geral com a média invidial dos clubes.
- Qual foi o comportamento do número de cartões vermelhos ao longo dos anos?
- Existe uma relação forte entre o número de cartões amarelos e o número de cartões vermelhos?
- Quais os clubes com maior média de cartões vermelhos por temporada?
### Gols: 
*Observação: Gols contra = tomados pela equipe. Gols pró = Marcados pela equipe.*
- Qual a média geral de gols pró por temporada? Além disso, gostaria de poder comparar a média de gols pró geral com a média invidial dos clubes.
- Qual a média geral de gols contra por temporada? Além disso, gostaria de poder comparar a média de gols contra geral com a média invidial dos clubes.
- Qual a relação entre Pontos e Saldo de Gols?
- Qual a relação entre Posição e Saldo de Gols?
- Quais os clubes com maior média de gols por temporada?
### Aproveitamento:
- Quais times disputaram mais temporadas?
- Qual a média de aproveitamento por estado?
- Quais times tiveram maior aproveitamento médio por temporada
### Campeões:
- Gostaria de vizualizar a soma de todos os dados em uma única tabela
- Quais times fizeram mais pontos ao longo de todas temporadas?
- Quais foram os campeões e quantos títulos tiveram cada um?
