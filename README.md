# Expectativa-de-Vida
Neste projeto, foi aplicado modelo de machine learning em um dataset obtido no kaggle para fazer a estimativa da expectativa de vida (o dataset pode ser encontrado [aqui](https://www.kaggle.com/datasets/kumarajarshi/life-expectancy-who)).

## Analise exploratória

Olhando as distriuição das variaveis, podemos ver que:

![image](https://user-images.githubusercontent.com/39843884/175321638-94c86362-e35d-48ef-bc1e-77ddf961adbb.png)

- maior parte da expectativa de vida está entre 70 e 80 anos;
- o consumo de álcool e começa bem alto nos primeiro e vai diminuindo;
- O número de anos na escola está entre 10 e 15 anos em sua maior parte;
- a taxa de magreza, tanto de 5 a 9 anos, quanto de 10 a 19 anos, começa alto e vai diminuindo, mostrando que a maior parte dos paises tem um baixo indice de magreza.

![image](https://user-images.githubusercontent.com/39843884/175322065-e70aa548-b72f-4b01-963f-09fcf52c21ac.png)

Podemos ver que mortalidade em adultos e a expectativa de vida tem uma certa relação, o interessante é que os países desenvolvidos neste dataset tem uma tendecia de ter as maiores expectativas de vida, apesa de serem poucos, como melhor mostra no grafico abaixo.

![image](https://user-images.githubusercontent.com/39843884/175322191-9ff84996-ea87-438f-9ebb-81200401a54a.png)

Interessante falar sobre o indice de massa corporal que quanto maior é,a expectativa de vida costuma ficar em um intervalo a medida que vai crescendo.

![image](https://user-images.githubusercontent.com/39843884/175322753-34389682-1118-4e71-9562-df74927d05cc.png)

Podemos ver que com o indice de magreza que quanto maior a tendência é a diminuição da expectativa de vida, juntamente com os anos na escola.

![image](https://user-images.githubusercontent.com/39843884/175323184-e4af4826-fa44-42ad-8bca-5479314a52c8.png)

Podemos ver aqui que paises acima de 90 anos de exptativa de vida não tem mortes por aids, o q a tendência é diminuir conforme o número de mortes vai aumentando.

![image](https://user-images.githubusercontent.com/39843884/175323373-2c2e6cac-ea09-481c-bc0c-8cc4c87a7fc3.png)

Como podemos ver, quaanto maior é o desenvolvimento humano do pais, maior é a expectativa de vida.

Verificando os mapas de calor com as correlações de *pearson* e *spearman*:

correlação de pearson:
![image](https://user-images.githubusercontent.com/39843884/175323983-287c3af4-a5ce-4ea0-b953-954d47358541.png)

correlação de spearman:
![image](https://user-images.githubusercontent.com/39843884/175324108-8ec67fd2-3c28-46bd-a7aa-86659fdd2fbf.png)

## Aplicando o modelo

Sobre o modelo, depois de preencher os valores nulos, e excluir os 10 valores do target, o melhor modelo q teve a melhor perfoace foi o random forest, em 
que teve as seguintes métricas:

![image](https://user-images.githubusercontent.com/39843884/175324709-e93b5cb9-f273-4647-8365-f2d05c37e540.png)

Aplicando o Grid Search, obteve os seguintes parametro {'criterion': 'absolute_error', 'max_features': 0.5} e tivemos uma melhora nos resultados:

![image](https://user-images.githubusercontent.com/39843884/175324897-0cecf404-7712-49e1-873c-7a56ecdc86d7.png)

E aplicando o rfe com as 12 colunas e teve as seguintes colunas:
'Year', 'Adult Mortality', 'Alcohol', 'BMI', 'under-five deaths','Polio', 'Total expenditure', 'HIV/AIDS', 'thinness  1-19 years',
'thinness 5-9 years', 'Income composition of resources','Schooling'

E se teve os seguintes resultados:

![image](https://user-images.githubusercontent.com/39843884/175325592-efb17dc3-9aa6-47c1-a22e-77122e229c0f.png)

 Então com RFE temos o melhor resultado, então olhando as estimativas, temos que:
 
 ![image](https://user-images.githubusercontent.com/39843884/175326001-0c3bc2a0-a612-4e0e-9a48-9208284d709e.png)

Podemos ver no gráfico acima que no geral o modelo teve uma boa estimativa, com uma taxa de erro muito pequena, logo esse modelo será de grande ajuda ṕra fazer estimativas de expectativa de vida. Acerca dos valores que estão um pouco distante no inicio e no fim, tera que ter um estudo mais aprofundado
se seria um *outlier* ou se faz parte mesmo e quem sabe, poderia ter melhores resultados, mas no mais, o modelo tem uma boa perfomace apesar de tudo.

