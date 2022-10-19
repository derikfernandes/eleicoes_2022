**Análise Estatísticas das eleições em 2022**

**1- Objetivo do Trabalho**
O objetivo deste trabalho é analisar estatisticamente as bases de dados fornecidas pelo TSE, para a eleição de deputado federal no estado de São Paulo, e encontrar pontos de destaque bem como responder as perguntas previamente definidas e abaixo listadas.

A partir da base de dados fornecida pelo TSE conseguimos construir um modelo com qual percentual de explicabilidade?

Quais as variáveis mais influenciaram na quantidade de votos?

Quais candidatos mais se destacaram nessas variáveis?

**A escolha inicial foi focar na eleição de Deputados Federais no Estado de São Paulo, porém a ideia é elaborar um modelo que esteja pronto para ser rodado para outros estados e outros tipos de candidatura**


**2- Base de Dados**

A primeira parte do estudo é voltada para analisar a base de dados fornecida pelo TSE, escolher as melhores variáveis e mesclar a base de dados objetivando formar uma base de dados final que servirá para este estudo.

Dados do TSE:

          A) Boletim de Urna

          link: https://dadosabertos.tse.jus.br/dataset/resultados-2022-boletim-de-urna
         
Esses dados estão quebrados pela zona eleitoral e seção, visando manter os dados agrupados por candidatos (objeto do nosso estudo), agrupamos os dados e criamos algumas variáveis que são:

DFS_MUNICIPIO= Quantidade de municípios diferente que o candidato teve voto

DFS_ZONA=Quantidade de zonas diferente que o candidato teve voto

DFS_SECAO=Quantidade de seções diferente que o candidato teve voto

DFS_LOCAL_VOTACAO=Quantidade de locais de votação diferentes que o candidato teve voto

QT_VOTOS =Quantidade de locais de votos totais que o candidato teve

STD_VOTOS = Desvio padrão dos votos (objetivo medir a variância da quantidade de votos dentro das zonas)      
   

          B) Prestação de Contas Eleitorais

          link: https://dadosabertos.tse.jus.br/dataset/dadosabertos-tse-jus-br-dataset-prestacao-de-contas-eleitorais-2022
          
Esses dados estão quebrados pelas diferentes categorias de gasto, visando manter os dados agrupados por candidatos (objeto do nosso estudo), agrupamos os dados e criamos algumas variáveis representativas que são:

FIRST_ORIGEM_DESPESA = A origem de despesa que tem mais gasto, em valor monetário, por candidato.

LAST_ORIGEM_DESPESA = A origem de despesa que tem menos gasto, em valor monetário, por candidato.

STD_ORIGEM_DESPESA = O desvio padrão da origem de despesa (objetivo medir a variância da origem da despesa)  

FIRST_DS_DOCUMENTO = A descrição de despesa que tem mais gasto, em valor monetário, por candidato.

LAST_DS_DOCUMENTO  = A descrição de despesa que tem menos gasto, em valor monetário, por candidato.

STD_DOCUMENTO = O desvio padrão da descrição da despesa (objetivo medir a variância da descrição da despesa)  

VR_PESSOA_FISICA = valor total gasto com despesas pagas para Pessoas Físicas

VR_PESSOA_JURIDICA  = valor total gasto com despesas pagas para Pessoas Jurídicas

recencia_media_DESPESA = quantidade média de dias que foram realizado os gastos (objetivo medir se o período em que foi mais gasto influenciará de alguma forma)

recencia_STD_DESPESA  = O desvio padrão da quantidade de dias da despesa (objetivo medir a variância da recência da despesa)  

VR_DESPESA_CONTRATADA = Valor total gasto por candidato


          C) Candidatos

          link: https://dadosabertos.tse.jus.br/dataset/candidatos-2022
         
Os dados dos candidatos foram agrupados por cada candidato, sendo que, abaixo listo quais as variáveis que foram criadas, a partir das variáveis da base de dados.

recencia_DT_NASCIMENTO = Quantidade de dias de referência da data de nascimento do candidato.

REDE_SOCIAL_XXXXX = Foram criadas 11 variáveis cada uma em relação a uma rede social (Facebook, flickr, instagram, kwai, linkedin, site, telegram, tiktok, twitter, whatsapp e youtube) sendo que o resultado de cada variável é binário, ou seja, apresenta o valor 1 para caso o candidato tenha declarado que possui a rede social e 0 caso não tenha a rede social. 

TOTAL_REDE_SOCAL = É o somatório de quantidade de redes sociais que o candidato possui


** A Base de dados final ficou com 1531 dados com 60 variáveis **
 

**Trabalhos Futuros:** 
Analise de classificação de candidados eleitos

Criar grupos (clusterizações)

Fazer um estudo embutindo a quantidade de seguidores de cada candidato

Análise a partir da desconsideração do gasto (voto/gasto)
