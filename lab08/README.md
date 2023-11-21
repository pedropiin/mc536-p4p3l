# Equipe `PLAY`

# Subgrupo `A`
* `Luiz Felipe Corradini Rego Costa` - `230613`
* `Pedro da Rosa Pinheiro` - `231081`

## Modelo Lógico do Banco de Dados de Grafos
> Coloque aqui o modelo lógico.
> Utilize este [modelo de base](https://docs.google.com/presentation/d/10RN7bDKUka_Ro2_41WyEE76Wxm4AioiJOrsh6BRY3Kk/edit?usp=sharing) para construir o seu.
> Coloque a imagem do PNG do seu modelo lógico como ilustrado abaixo (a imagem estará na pasta `image`):
>
<img src="images/lab_atualizado.png" width="400px" height="auto">

## Perguntas de Pesquisa/Análise Combinadas e Respectivas Análises

>
### Quais são as receitas mais completas?
> 
>  * Para responder a essa análise, precisamos, primeiramente, alterar nosso grafo inicial. Como nosso grafo é bipartido, podemos realizar um pŕojeção,na qual ligaremos apenas receitas. A partir disso, podemos realizar junções, para criarmos um grafo conectado por todos os ingredientes. Desse modo, enfim, podemos encontrar, calculando para cada nó do grafo, os nós com maiores coeficientes de proximidade.

### Quais ingredientes que não são utilizados em conjunto em nenhuma receita, poderiam potencialmente formar uma combinação?
>   
>   * Podemos procurar ingredientes que apresentam poucas ou nenhuma receitas em comum, mas, das receitas que fazem parte, existem muitos ingredientes em congruência. Por exemplo: geleia e pasta de amendoim. Ambos aparecem em suas respectivas receitas, que, em grande parte, apresentam os mesmos ingredientes, como, por exemplo, torrada com geleia e torrada com pasta de amendoim. Consequentemente, por mais que não registrado, é possível estabelecer um alto grau de combinação entre ambos ingredientes. Precisamos, para tal análise, analisar os motifs triangulares dentro do grafo, no qual os ingredientes A e B fazem parte da receita X e a os ingredientes B e C compõe a receita Y. Assim, conforme encontramos múltiplas receitas em que A e C estão interligados indiretamente, podemos estabelecer, no fim, uma relação entre os dois.

### Como podemos identificar diferentes grupos de receitas?
>   
>   * Nesse caso, precisamos avaliar o conceito de comunidade. Para isso, realizamos uma projeção, para que apenas receitas estejam interligadas. Para analisar as comunidades, verificamos os conjuntos de nós que existem mais arestas entre eles, e poucas arestas ligadas a outros nós fora deles. Assim, conseguimos separar o nosso grafo em comunidades, ou seja, conseguimos encontrar diferentes grupos de receitas.
