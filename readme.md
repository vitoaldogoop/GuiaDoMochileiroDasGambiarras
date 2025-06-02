
# GUIA DO MOCHILEIRO DAS GAMBIARRAS

#### Um guia básico sobre API's da Takao, sobre o que fazer em casos de problemas comuns, como debugar, etc.  

## Placas API

Tudo o que vai precisar mexer em si fica centralizado no GetPlacaHandler ( PlacasAPI.Mediator\Placa\GetPlaca\GetPlacaHandler.cs), no método Handle. Ali, é feito uma busca na nossa base para verificar se a placa existe na nossa base.

![infoCarVerify](infocarverify.jpg)

Armazenando as informações do carro no infoCarVerify, ou nulo caso não encontre nada e em seguida faz uma busca com a API da LBMInfo. Se conseguir retornar dados, salva no histórico de placas. A base do histórico de placas armazena apenas o retorno da API de consulta, não os dados de peças relacionadas ao veiculo.

![Chamada API da LBMInfo](image.png)

Depois disso, ele tenta converter os dados do carro para o filtro de produtos do catalogo

![alt text](image-1.png)

Depois disso, ele efetua a busca usando os filtros e retorna a lista de peças.

Caso encontre problemas com a API não achando o veiculo, pode ser na verdade não encontrando as peças por não conseguir criar o filtro para o catalogo apropriadamente. Seguindo o caminho dos prints e debugando o código, conseguirá entender o funcionamento principal.

Chamada principal, lembrar de usar os headers corretos
![alt text](image-2.png)
![alt text](image-3.png)

## CPFR

Há duas chamadas principais relacionadas ao CPFR/Hub. Estoque e pedidos. Primeiro sobre a de estoque que fica na EstoqueController

![alt text](image-4.png)

É uma simples chamada para uma proc que capta a quantidade de estoque de acordo com qualquer quantidade de SKU passados.

![alt text](image-5.png)

Ele monta um TVP para os códigos de empresa para também verificar multiplas empresas.

![alt text](image-6.png)

