# Data Challenge 20221121 (Project ID: 4917)

### Introdução

- Este projeto apresenta a solução para o desafio 20221121 [(Project ID: 4917)](http://exemplo.com/) by [Coodesh](https://coodesh.com/).

## O desafio

Neste desafio iremos utilizar duas bases de dados uma da Netflix [netflix_titles.csv](./netflix_titles.csv) e uma da Amazon Prime [amazon_prime_titles.csv](./amazon_prime_titles.csv) contendo informações sobre a adição de conteúdos em seus respectivos catálogos de streaming.

Aqui você pode encontrar os metadados das tabelas [attributes.txt](./data/attributes.txt)


## Perguntas do desafio

Este projeto apresenta informação sobre as seguintes perguntas:

1- Top 10 atores/atrizes considerando todos os dados?

2- Top 5 países produtores de conteúdos considerando todos os dados e comparando as duas plataformas?

3- Mês no qual há mais adições de filmes na plataforma Netflix?

4- Quantidade de filmes listados como comédia?

5- Lista de todos os gêneros de filmes?

6- A frequência de "TV Show" de todos os dados e comparativamente em relação as duas plataformas?

7- A frequência de "Movies" de todos os dados e comparativamente em relação as duas plataformas?

## Tecnologias utilizadas

Este projeto foi realizado em Power BI e Python (plataforma [Colab](https://colab.research.google.com/)), com apoio das bibliotecas:

- Pandas
- Numpy
- Matplot

## Resolução

### 1- Top 10 atores/atrizes considerando todos os dados?
Hipotese de resposta:
- Consideramos Top 10 artistas como um ranking dos 10 artistas que mais participaram de filmes, considerando toda a base de dados. 

Tratamentos realizados:
- Para encontrar os artistas que mais participaram de filmes precisamos primeiro unir a base da Netflix com a base da Amazon isso gerou a duplicação de alguns titúlos que estão presentes nas duas plataformas. Removemos os titulos duplicados a partir de dois filtros: 1° desduplicando titulos com mesmo nome e duração e 2° desduplicando titulos com mesmo nome e mesmo diretor (foi necessário essa dupla filtragem para eliminar todas as redundancias).
- Filtro de tipo para considerarmos somente os filmes.
- Foi necessário "splitar" a coluna de cast para separarmos os atores.

Solução (Top 10 atores/atrizes):

1-Anupam Kher;

2-Maggie Binkley;

3-Amitabh Bachchan;

4-Nassar;

5-Akshay Kumar;

6-Shah Rukh Khan;

7-Paresh Rawal;

8-Naseeruddin Shah;

9-Danny Trejo;

10-Om Puri;

Obs: Existem +1.000 filmes sem a informação de 'cast'.


### 2- Top 5 países produtores de conteúdos considerando todos os dados e comparando as duas plataformas?
Hipotese de resposta:
- Consideramos Top 5 paises como um ranking dos 5 paises que mais produziram filmes, considerando toda a base de dados. 

Tratamentos realizados:
- Para encontrar os paises que mais produziram filmes utilizamos a base previamente unida e com as duplicidades tratadas.
- Foi necessário "splitar" a coluna de "country" para separarmos os paises, pois alguns filmes possuiam multiplos paises no campo country.
- Contagem de aparições de cada país.

Solução (Top 5 países produtores):

1-United States;

2-India;

3-United Kingdom;

4-Canada;

5-France;

Obs: Existem 7536 registros sem identificação de país.

Solução (Top 5 países produtores comparando as plataformas):

O Amazon Prime possuí 7245 registros faltantes sobre o país de origem dos filmes, esse volume não nos permite fazer uma comparação acurada, já a Netflix possuí 440 registros sem a identificação do país de origem.

Com os dados presentes nas tabelas temos os seguintes TOP 5 por plataforma:

Netflix:

1-United States - 2752 filmes produzidos;

2-India - 962 filmes produzidos;

3-United Kingdom - 534 filmes produzidos;

4-Canada - 319 filmes produzidos;

5-France - 303 filmes produzidos;

Amazon Prime:

1-United States - 267 filmes produzidos;

2-India - 230 filmes produzidos;

3-United Kingdom - 58 filmes produzidos;

4-Canada - 31 filmes produzidos;

5-France - 19 filmes produzidos;

### 3- Mês no qual há mais adições de filmes na plataforma Netflix?

Hipotese de resposta:
- Para compararmos os meses e podermos descobrir qual mês tem mais adições de filmes no Netflix, vamos somar todas as adições de cada mês sem considerarmos os anos, por exemplo o valor de janeiro representa a soma de todas as adições realizadas no mês de janeiro considerando todos os anos com dados disponíveis. O mês que apresentou a maior somatória foi considerado como a resposta final. 

Tratamentos realizados:
- Load somente da base da Netflix.
- Filtro de tipo para considerarmos somente os filmes.
- Contagem de adições mensal, gerando uma tabela com a somatório mensal e gerando o plot de um gráfico para apoio da interpretação.

Solução (Mês com mais adições Netflix):

1-Julho com 565 adições considerando a somatória do mês de julho de todos os anos da base da Netflix.

### 4- Quantidade de filmes listados como comédia?

Hipotese de resposta:
- Contagem do número de títulos classificados como "Comedies" no Netflix + a contagem dos títulos classificados como "Comedy" no Amazon Prime.

Tratamentos realizados:
- Utilizamos a base previamente unida e com remoção dos títulos duplicados.
- Filtro da coluna "listed_in" selecionando registros que contenham as plavaras "Comedy" ou "Comedies".
- Após esse filtro temos que o número de títulos listados como comédia é igual ao numero de linhas da tabela resultante 

Solução (Quantidade de filmes listados como comédia):

1-Existem 3.773 filmes listados como comédia.

### 5- Lista de todos os gêneros de filmes?

Hipotese de resposta:
- Lista com todos os generos de filmes, agrupando e ajustando as respostas redundantes quando comparamos as duas plataformas.

Tratamentos realizados:
- Utilizamos a base previamente unida e com remoção dos títulos duplicados.
- Esplitamos a coluna que contêm os generos para separamos filmes que contêm multiplos generos.
- Removemos os valores duplicados.
- Unimos os generemos redundantes e ajustamos os generos com inconsistências.

Solução (Lista de todos os gêneros de filmes):

Lista: action, action & adventure, adventure, culture, anime, arts, children & family movies, classic movies, comedy, documentary, drama, entertainment, faith & spirituality, fantasy, fitness ,historical ,horror ,independent movies ,international ,kids ,lgbtq ,military and war ,music & musicals ,romance ,sci-fi & fantasy ,special interest ,sports ,stand-up comedy ,suspense ,talk show and variety ,thrillers ,unscripted ,western ,young adult audience.

### 6- A frequência de "TV Show" de todos os dados e comparativamente em relação as duas plataformas?

Hipotese de resposta:
- Para esse desafio construímos uma a série temporal com os dados mensais de adição de "TV Shows" bem como plotamos um gráfico com essas informações.

Tratamentos realizados:
- Carregamos a base com a informação das duas plataformas.
- Filtro da coluna "type" selecionando registros "TV Show".
- Realizamos a remoção dos valores que não contem dados de data de adição.
- Ajustamos o campo de data de adição para o formato "YYYYMM" para que possamos construir uma visão mensão de frequencia de adição.
- Os dados também foram carregados de forma individual e foi realizado os mesmos passos de tratamento.
- Realizamos as contagem das freqeuncias de adições, geramos tabelas e plotamos os gráficos via matplot.
- Para uma melhor vizualização os valores foram replotados no Power BI. 

Solução (A frequência de "TV Show"):

![freq_tv](https://user-images.githubusercontent.com/128094095/226432419-ccc31b86-b369-4715-a9cd-128e2065e800.JPG)

![freq_tv_plat](https://user-images.githubusercontent.com/128094095/226429214-b016f72e-a033-45a9-a0ae-2b99cf4e75a7.JPG)

Obs: A base de dados da Amazon Prime apresentou poucos registros com informação de inclusão no serviço.


### 7- A frequência de "Movies" de todos os dados e comparativamente em relação as duas plataformas?
Para conseguir mesclar os dados você deverá tomar cuidado para que os identificadores não sobreponham valores.

Hipotese de resposta:
- Para esse desafio construímos uma a série temporal com os dados mensais de adição de "Movies" bem como plotamos um gráfico com essas informações.

Tratamentos realizados:
- Carregamos a base com a informação das duas plataformas.
- Filtro da coluna "type" selecionando registros "Movies".
- Realizamos a remoção dos valores que não contem dados de data de adição.
- Ajustamos o campo de data de adição para o formato "YYYYMM" para que possamos construir uma visão mensão de frequencia de adição.
- Os dados também foram carregados de forma individual e foi realizado os mesmos passos de tratamento.
- Realizamos as contagem das freqeuncias de adições, geramos tabelas e plotamos os gráficos via matplot.
- Para uma melhor vizualização os valores foram replotados no Power BI. 

Solução (A frequência de "Movies"):

![image](https://user-images.githubusercontent.com/128094095/226435748-a1815450-22a1-4621-a5b0-6dd882d4d318.png)

![freq_mo_plat](https://user-images.githubusercontent.com/128094095/226435783-27025f3c-8226-4a0c-94d8-5e4a17be860b.JPG)

Obs: A base de dados da Amazon Prime apresentou poucos registros com informação de inclusão no serviço.

