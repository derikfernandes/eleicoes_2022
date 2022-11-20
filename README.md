**Análise Estatísticas das eleições em 2022**

---------------------------------------------------------------------------------------------------------------------------------------------------------------------

**1- Objetivo do Trabalho**
O objetivo deste trabalho é analisar estatisticamente as bases de dados fornecidas pelo TSE, para a eleição de deputado federal no estado de São Paulo, e encontrar pontos de destaque bem como responder as perguntas previamente definidas e abaixo listadas.

A partir da base de dados fornecida pelo TSE conseguimos construir um modelo com qual percentual de explicabilidade? 

Quais as variáveis mais influenciaram na quantidade de votos?

Quais candidatos mais se destacaram nessas variáveis?

**A escolha inicial foi focar na eleição de Deputados Federais no Estado de São Paulo, porém a ideia é elaborar um modelo que esteja pronto para ser rodado para outros estados e outros tipos de candidatura**

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------


**2- Base de Dados**

A primeira parte do estudo é voltada para analisar a base de dados fornecida pelo TSE, escolher as melhores variáveis e mesclar a base de dados objetivando formar uma base de dados final que servirá para este estudo.

Dados do TSE:

          A) Boletim de Urna

          link: https://dadosabertos.tse.jus.br/dataset/resultados-2022-boletim-de-urna
         
Esses dados estão quebrados pela zona eleitoral e seção, visando manter os dados agrupados por candidatos (objeto do nosso estudo), agrupamos os dados e criamos algumas variáveis que são:

DFS_MUNICIPIO= Quantidade de municípios diferente que o candidato teve voto

DFS_ZONA=Quantidade de zonas diferente que o candidato teve voto.

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


**A Base de dados final ficou com 1531 dados com 60 variáveis**

A baixo listados:

ABT_CANDIDATO

(1531,59)

'SQ_CANDIDATO', 'NR_CANDIDATO', 'NM_CANDIDATO', 'DS_SITUACAO_CANDIDATURA', 'DS_DETALHE_SITUACAO_CAND', 'TP_AGREMIACAO','NM_PARTIDO', 
'NM_COLIGACAO', 'DS_COMPOSICAO_COLIGACAO','DS_NACIONALIDADE', 'SG_UF_NASCIMENTO', 'NM_MUNICIPIO_NASCIMENTO','NR_IDADE_DATA_POSSE', 'DS_GENERO', 
'DS_GRAU_INSTRUCAO','DS_ESTADO_CIVIL', 'DS_COR_RACA', 'DS_OCUPACAO', 'DS_SIT_TOT_TURNO', 'ST_REELEICAO',
'ST_DECLARAR_BENS', 'NR_PROCESSO', 'DS_SITUACAO_CANDIDATO_PLEITO','DS_SITUACAO_CANDIDATO_URNA', 'ST_CANDIDATO_INSERIDO_URNA',
'NM_TIPO_DESTINACAO_VOTOS', 'DS_SITUACAO_CANDIDATO_TOT','ST_PREST_CONTAS', 'recencia_DT_NASCIMENTO', 'DFS_MUNICIPIO',
'DFS_ZONA', 'DFS_SECAO', 'DFS_LOCAL_VOTACAO', 'QT_VOTOS', 'STD_VOTOS','FIRST_ORIGEM_DESPESA', 'LAST_ORIGEM_DESPESA', 'STD_ORIGEM_DESPESA',
 'FIRST_DS_DOCUMENTO', 'LAST_DS_DOCUMENTO', 'STD_DOCUMENTO','VR_PESSOA_FISICA', 'VR_PESSOA_JURIDICA', 'recencia_media_DESPESA','recencia_STD_DESPESA', 'VR_DESPESA_CONTRATADA', 'VR_BEM_CANDIDATO','REDE_SOCIAL_facebook', 'REDE_SOCIAL_flickr', 'REDE_SOCIAL_instagram','REDE_SOCIAL_kwai', 'REDE_SOCIAL_linkedin', 'REDE_SOCIAL_site','REDE_SOCIAL_telegram', 'REDE_SOCIAL_tiktok', 'REDE_SOCIAL_twitter','REDE_SOCIAL_whatsapp', 'REDE_SOCIAL_youtube' e 'TOTAL_REDE_SOCAL'.
 
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------
 
 **3- Análise Exploratória**
 
 1- Análise Situação Candidatura
 
          Qde Candidatos = 1531
                    1432 Candidatos APTOS
                              1370 Deferidos
                              58 Indeferidos com Recursos
                              4 Deferidos com Recurso
                              
                    99   Candidatos INAPTOS
                              56 Renúncia
                              43 Indeferidos
                              
                              
                              
2- Análise dos Partidos
          
          Qde de Partidos = 32
                     
          
          Partidos Isolados = 1341
                    Em mediana cada partido lançou 58 candidatos
                    Partidos com mais de 70 candidatos =PTB, PODEMOS, PSB, AVANTE, AGIR, PROGESSISTAS, PL, REPUBLICANOS, PRTB, PROS 
                    
          Federação = 190
                    Somente haviam 3 Coligações
                    PT/PC do B/PV = 72
                    PSOL/REDE = 60
                    PSDB/CIDADANIA = 58
          
                              
3- Detalhamento dos Candidados
          
          Qde de Nacionalidade = 3
                    
![image](https://user-images.githubusercontent.com/93551585/197288949-a68ff54c-69c7-46f1-a426-a397a16b3001.png)
               
          
          Quantidade de Estados diferentes de Nascimento dos candidatos = 24
          
![image](https://user-images.githubusercontent.com/93551585/197290345-ff75a77e-9a9d-4a17-8ad4-14f4a5a4c8d0.png)

          Quantidade de Municípios diferentes de Nascimento dos candidatos = 476
          
![image](https://user-images.githubusercontent.com/93551585/197290766-65acf376-f36f-4538-8f00-e09f1f8da86e.png)


         
         Idade dos Candidatos
                    63 idades diferentes dos candidatos
                    Idade Mínima = 21
                    Idade Máxima = 92
                    Média = 49
                    Mediana = 50
         
![image](https://user-images.githubusercontent.com/93551585/198124580-8097a051-8ee9-4e19-b068-b5bc7098164a.png)

Existe uma tendência a uma distribuição normal em torno de 50 anos de idade

          Gênero 
              Masculino = 1032 (67,4%) 
              Feminino  = 499  (32,59%)
              
A maioria dos candidatos ainda é composto por homens 


 Grau Instrução
          
![image](https://user-images.githubusercontent.com/93551585/198732660-d6b5914f-efa4-4805-868f-9806b6cb0519.png)

 Estado Civil 
          
![image](https://user-images.githubusercontent.com/93551585/199283387-3f2e9d77-0814-4efb-8b54-6f29ba4ab295.png)

Raça

![image](https://user-images.githubusercontent.com/93551585/199283951-ee63fb03-ccef-44f1-95ce-81e3080cc350.png)

Ocupação

![image](https://user-images.githubusercontent.com/93551585/199284252-21b809df-1563-46b3-bfe5-eda81326257b.png)

Valor do Bem dos Candidatos
          
          Valor Máximo = R$ 88.441.467,08
          Valor Médio  = R$ 809.195,92
          Valor Mediano  = R$ 107.300,00
  
434 candidatos não prestaram conta/ apresentaram valor zerado de bem 

Apoio presidencial

![image](https://user-images.githubusercontent.com/93551585/201998484-532b8151-9c44-4f8a-bc2c-7996053c2471.png)

          De todos os candidatos:
          923 estavam apoiando Bolsonaro
          608 estavam apoiando Lula
          
         
4- Comparação entre Redes Sociais declaradas dos candidatos

          Rede social declarada por candidato
   
![image](https://user-images.githubusercontent.com/93551585/199286026-e9dc76bd-a4f4-4e20-8325-0cbe3437478d.png)


Dos 1531 candidatos 
          
          840 não declararam nenhuma rede social (54,87%)
          167 declararam pssuir pelo menos 2 redes sociais (10,91%)
          153 declararam possuir pelo menos uma rede social (10%)
          115 declararam possuir 3 redes sociais (7,51%) 
          94  declararam possuir 4 redes sociais (6,14%)
          71  declararam possuir 6 redes sociais (4,64%)
          64  declararam possuir 5 redes sociais (4,18%)
          24  declararam possuir 7 redes sociais (1,57%)
          3   declararam possuir 8 redes sociaise (0,20%)
          
          

          Redes sociais mais declaradas 
          
![image](https://user-images.githubusercontent.com/93551585/199564013-1b4b44cc-b1b6-4d9a-a784-95d90b4fa1df.png)

5- Gastos em Campanhas

          Máximo = R$ 3.286.454,99 (Candidato Arnaldo Jardim)
                    Máximo (Gasto com PJ) = R$ 2.357.873,91
                    Máximo (Gasto com PF) = R$ 1.823.078,98
          
          Mínimo = Zero (podendo ser não declarado)
          
          Média  = R$ 286.645,55
                    Média  (Gasto com PJ)= R$ 182.531,83
                    Média  (Gasto com PF)= R$ 104.113,72
                    
 A seguir esta a análise em relação a data da despesa, medido pela recência
 
          Máximo = O gasto mais antigo esta com 297 dias
                    O desvio Padrão máximo dos gasto esta em 171
          Média  = A média dos gastos esta girando em torno de 111 dias
                    O desvio Padrão médio dos gastos esta em 61 dias
  
 De todos os candidatos 563 não prestaram contas
 
          As despesas que mais estiveram em primeiro em **quantidade** nos gastos estão elencadas abaixo
          
![image](https://user-images.githubusercontent.com/93551585/199579729-580a7dc6-3d08-440c-ade1-41e088f6c1fb.png)

          As despesas que mais estiveram em primeiro em **valor** nos gastos estão elencadas abaixo
          
![image](https://user-images.githubusercontent.com/93551585/202002103-5b172f10-56cf-4919-a23b-ea8456dba5ef.png)

          As despesas que mais estiveram em primeiro em **média** nos gastos estão elencadas abaixo
          
![image](https://user-images.githubusercontent.com/93551585/202002386-b34c6e73-c257-4414-8954-4e2ae4f9e667.png)

          As despesas que mais estiveram em último em **quantidade** nos gastos estão elencadas abaixo
          
 ![image](https://user-images.githubusercontent.com/93551585/201999788-f2ffb410-74f4-4fea-8dee-b2fe0ac7b5b6.png)
 
           As despesas que mais estiveram em último em **valor** nos gastos estão elencadas abaixo
          
![image](https://user-images.githubusercontent.com/93551585/202003236-ab078026-6cb1-407f-8d39-846c1822e9b1.png)

           As despesas que mais estiveram em último em **média** nos gastos estão elencadas abaixo
          
![image](https://user-images.githubusercontent.com/93551585/202003473-5a10e568-9c6e-459b-ad6b-3e1206ed4d5a.png)

 
6- Resultado Eleição

Situação dos Candidatos após eleição

![image](https://user-images.githubusercontent.com/93551585/202266606-ab486e56-6454-4d08-8dae-d850c20cb188.png)

70 candidatos eleitos e 781 suplentes



 

**Trabalhos Futuros:** 
Analise de classificação de candidados eleitos

Criar grupos (clusterizações)

Fazer um estudo embutindo a quantidade de seguidores de cada candidato

Análise a partir da desconsideração do gasto (voto/gasto)

Estender a análise para outros estados

Analisar comportamento d emunicípios visando um entendimento para futuras eleições municipais

construir um dado de nº de seguidores 

Comparar diferentes estados e regiões

Avaliação através dos reeleitos

