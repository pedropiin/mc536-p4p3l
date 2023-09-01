# Modelo para Apresentação do Lab02 - Modelagem Conceitual de Refeições em um Restaurante


# Equipe `PLAY`

# Subgrupo `A`
* `Luiz Felipe Corradini Rego Costa` - `230613`
* `Pablo Henrique Almeida Mendes` - `230977`
* `Pedro da Rosa Pinheiro` - `231081`

## Modelo Conceitual ER Original

<img src="images/ER_MC536_P4P3R - Page 1.png" width="400px" height="auto">

*Diagrama ER Original*



## Mapeamento para o Modelo Relacional

~~~
DIA(Ano, Mês, <ins>Dia</ins>)
CARDAPIO (<ins>ID Cardapio</ins>, Balanceamento, Guarnicao, Sobremesa, Salada, Fruta, Prato Principal Regular, Prato Principal Vegano)
    Guarnição chave estrangeira -> Porção (ID Porção)
    Sobremesa chave estrangeira -> Porção (ID Porção)
    Salada chave estrangeira -> Porção (ID Porção)
    Fruta chave estrangeira -> Porção (ID Porção)
    Prato Principal Regular chave estrangeira -> Porção (ID Porção)
    Prato Principal Vegano chave estrangeira -> Porção (ID Porção)
CARDAPIO REGULAR 
CARDAPIO VEGANO
REFEIÇÃO (ID Cardapio, Dia, RA, Perfil Nutricional)
    ID Cardápio chave estrangeira -> CARDÁPIO (ID Cardápio)
    Dia chave estrangeira -> DIA (Dia)
    RA chave estrangeira -> Aluno (RA)
ALUNO (<ins>RA</ins>, Nome)
PORÇÃO (Aceitação, Frequência, Valor Nutricional, <ins>ID Porção</ins>)
COMPONENTES (ID Porção, ID Ingrediente)
    ID Porção chave estrangeira -> Porção (ID Porção)
    ID Ingrediente chave estrangeira -> Ingrediente (ID Ingrediente)
INGREDIENTE (ID Ingrediente, Valor Energético, Quantidade Proteína, Quantidade, Carboidrato, Quantidade Lipídio, Quantidade Vitaminas)
~~~