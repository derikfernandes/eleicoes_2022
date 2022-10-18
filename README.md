**Análise Estatísticas das eleições em 2022**

**1- Objetivo do Trabalho**
O objetivo deste trabalho é analisar estatisticamente as bases de dados fornecidas pelo TSE, para a eleição de deputado federal no estado de São Paulo, e encontrar pontos de destaque bem como responder as perguntas previamente definidas e abaixo listadas.

A partir da base de dados fornecida pelo TSE conseguimos construir um modelo com qual percentual de explicabilidade?

Quais as variáveis mais influenciaram na quantidade de votos?

Quais candidatos mais se descataram nessas variáveis?

**A escolha inicial foi focar na eleição de Deputados Federais no Estado de São Paulo, porém a ideia é elaborar um modelo que esteja pronto para ser rodado para outros estados e outros tipos de candidatura**


**2- Base de Dados**

A primeira parte do estudo é voltada para analisar a base de dados fornecida pelo TSE, escolher as melhores variáveis e mesclar a base de dados objetivando formar uma base de dados final que servirá para este estudo.

Dados do TSE:

          A) Boletim de Urna

          link: https://dadosabertos.tse.jus.br/dataset/resultados-2022-boletim-de-urna
         
Esses dados estão quebrados pela zora eleitoral e seção, visando manter os dados agrupados por candidatos (objeto do nosso estudo), agrupamos os dados e criamos algumas variáveis que são:

DFS_MUNICIPIO= Quantidade de municípios diferente que o candidato teve voto

DFS_ZONA=Quantidade de zonas diferente que o candidato teve voto

DFS_SECAO=Quantidade de seções diferente que o candidato teve voto

DFS_LOCAL_VOTACAO=Quantidade de locais de votação diferentes que o candidato teve voto

QT_VOTOS =Quantidade de locais de votos totais que o candidato teve

STD_VOTOS = Desvio padrão dos votos (objetivo medir a variância da quantidade de votos dentro das zonas)      
        

          B) Prestação de Contas Eleitorais

          link: https://dadosabertos.tse.jus.br/dataset/dadosabertos-tse-jus-br-dataset-prestacao-de-contas-eleitorais-2022
          
Esses dados estão quebrados pelas diferentes categorias de gasto, visando manter os dados agrupados por candidatos (objeto do nosso estudo), agrupamos os dados e criamos algumas variáveis representativas que são:




          C) Candidatos

          link: https://dadosabertos.tse.jus.br/dataset/candidatos-2022
          
 

**Trabalhos Futuros:** 
Analise de classificação de candidados eleitos

Criar grupos (clusterizações)

Fazer um estudo embutindo a quantidade de seguidores de cada candidato

Análise a partir da desconsideração do gasto (voto/gasto)
