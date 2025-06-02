
# GUIA DO MOCHILEIRO DAS GAMBIARRAS

#### Um guia básico sobre API's da Takao, sobre o que fazer em casos de problemas comuns, como debugar, etc.  

## Placas API

Tudo o que vai precisar mexer em si fica centralizado no GetPlacaHandler ( PlacasAPI.Mediator\Placa\GetPlaca\GetPlacaHandler.cs), no método Handle. Ali, é feito uma busca na nossa base para verificar se a placa existe na nossa base.

![infoCarVerify](infocarverify.jpg)

Armazenando as informações do carro no infoCarVerify, ou nulo caso não encontre nada e em seguida faz uma busca com a API da LBMInfo.

![Chamada API da LBMInfo](image.png)