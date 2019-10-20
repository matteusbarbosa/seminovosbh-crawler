# Projeto de crawler atualizado em outubro/2019 do portal SEMINOVOSBH

Resumidamente, disponibiliza 2 endpoints: busca e detalhe

## Instalação

- Clone

Se for contribuir

- Envie pull request

Se quiser sua própria versão

- Fork

## Nota de atualização pós-fork

Atualizei a versão do Lumen para 5.8 (mais atual) entre outras em outubro/2019

## Problema de certificado

- baixe https://curl.haxx.se/docs/caextract.html
- Abra o php.ini da versão que está usando e modifique a linha: curl.cainfo = (caminho onde está seu certificado baixado)

## Quem sou eu

Matteus Barbosa. Acesse https://desenvolvedormatteus.com.br

## Agradecimento

josecfcts por criar o projeto base em 2017. Com um trabalho de ~5 horas consegui atualizar algumas dependências pra fazer funcionar em 2019

# Enunciado do teste

The objective of this test is to assess your level of knowledge in the technologies and tools we will be using. You will need to implement a solution for a common use case in our software.

The test can be completed in many different ways and levels of detail. Try not to limit yourself and use as many tools, modules and tricks as you can. Also, pay attention to the quality and clarity of your code and the extensibility of your proposed solution. The design and architecture are mostly open, so you will have to make sensible decisions about it. These are the things that will make you stand out from the crowd.

The code can be open-sourced in a public repository as the origin of the data used is also public. If you choose to make it private, please provide the necessary credentials to access it. You can also make a public or private fork of this same repository.
Task

The website seminovosbh.com.br is a local portal to search used cars. We need that stock of cars in our services. To do so, you gone crawl the website.

Using PHP, you must provide a RESTful endpoint to search cars (according the existing filters) and another endpoint to view the details of a selected car.

Good look!

# Documentação

![filtros seminovosbh](https://ibb.co/80V1Jh7)

# GET 
## {/busca?parametro=valor}
Ex.: ```/busca?marca=Renault&pagina=1&cidade=3148```

Obtém uma lista de veículos de acordo com os parâmetros passados como QueryString na URL

### Parâmetros 
| nome| tipo   |   Exemplo|Descrição|
|------------|--------|--------|--------|
| tipoVeiculo      | int | 1,2,3 |Carro, caminhão, moto|
| marca      | string | Renault |Marca do veículo|
| modelo      | int | 1717 |referente ao Cavallino|
| cidade     | int    |   3128| Código da cidade|
| valorDe    | int    |   12000|Valor mínimo do carro sem casas decimais, somente inteiro|
| valorAte    | int    | 25000|Valor máximo do carro sem casas decimais, somente inteiro|
| particular    | string    | origem | Quando presente, sinaliza particular|
| revenda    | string    | origem | Quando presente, sinaliza revenda|
| novo    | string    | estado | Quando presente, sinaliza zero km|
| seminovo    | string    | estado | Quando presente, sinaliza seminovo|
| placaId    | string    | HJM1217 | Quando presente, sinaliza veículo específico|
| anoDe    | int    |  2003|Ano máximo do carro com quatro dígitos|
| anoAte    | int    |  2005|Ano mínimo do carro com quatro dígitos|
| pagina     | int    |   3|Páginação|

### Response Code
* 404 Not found
* 200 Success

### Exemplo de Response Json
```JSON
[
    {
        "ano": "2007-2008",
        "id": "2123104",
        "marca": "renault",
        "nome": "clio-hatch",
        "anuncio": "Renault Clio Hatch 1.0 16V AUTENTIC  R$ 12.500,00"
    }
]
```



# GET 
## {/automovel/{id}}
Ex.: ```/automovel/234920```

Obtém os detalhes de um veículo

### Parâmetros 
| nome| tipo   |   Exemplo|Descrição|
|------------|--------|--------|--------|
| id| int| 234234 |Id do veículo|

### Response Code
* 404 Not found
* 200 Success

### Exemplo de Response Json
```JSON
[
    {
        "acessorios": [
            "ABS",
            "AIR BAG",
            "AIR BAG DUPLO",
            "ALARME",
            "AR CONDICIONADO",
            "AR QUENTE",
            "CÂMBIO MANUAL",
            "CD / MP3",
            "COMPUTADOR DE BORDO",
            "DIREÇÃO HIDRÁULICA",
            "FARÓIS DE MILHA",
            "LIMPADOR TRASEIRO",
            "MP3 / USB",
            "RODAS DE LIGA LEVE",
            "TRAVAS ELÉTRICAS",
            "VIDROS ELÉTRICOS",
            "VOLANTE AJUSTÁVEL"
        ],
        "dataCadastro": "11/10/2017",
        "detalhes": [
            "2014/2014",
            "92000km",
            "Bi-Combustível",
            "5 portas",
            "Prata",
            "Início da placa PUF****",
            "Aceito Troca"
        ],
        "imagens": [
            "http://carros.seminovosbh.com.br/renault-sandero-2014-2014-2177622-5973658fc7bf93c25e95749701234aa9871b.jpg",
            "http://carros.seminovosbh.com.br/renault-sandero-2014-2014-2177622-5973658fc7bf93c25e95749701234aa9871b.jpg",
            "http://carros.seminovosbh.com.br/renault-sandero-2014-2014-2177622-2092c5193e0e8e37ee8dc69ec1e673707529.jpg",
            "http://carros.seminovosbh.com.br/renault-sandero-2014-2014-2177622-8797d485a348b438ba87d880a4d53671ad0f.jpg",
            "http://carros.seminovosbh.com.br/renault-sandero-2014-2014-2177622-59482bf97f735ed6142f721fbe8ca9f6b23f.jpg",
            "http://carros.seminovosbh.com.br/renault-sandero-2014-2014-2177622-5361ebd395638f58f917c4d1e92ef00a408.jpg",
            "http://carros.seminovosbh.com.br/renault-sandero-2014-2014-2177622-7374607743b6c95f86778fde9bcedee3e2fc.jpg",
            "http://carros.seminovosbh.com.br/renault-sandero-2014-2014-2177622-5812da94836f8eec48cebdfec71f6bd34b89.jpg",
            "http://carros.seminovosbh.com.br/renault-sandero-2014-2014-2177622-2847c157a8a8107b6700a112f19833a48541.jpg",
            "http://carros.seminovosbh.com.br/renault-sandero-2014-2014-2177622-49064704a994d5fed4b9789feefba4b83a3f.jpg",
            "http://carros.seminovosbh.com.br/renault-sandero-2014-2014-2177622-8309bb7bb32a1fb16c07a143d8b8123a4439.jpg",
            "http://carros.seminovosbh.com.br/renault-sandero-2014-2014-2177622-5170ac97bfab8e123364a8dbd56b17b7a9d4.jpg",
            "http://carros.seminovosbh.com.br/renault-sandero-2014-2014-2177622-1083fdfa70f968dd5b17983a27f9492b8f98.jpg"
        ],
        "nomeAnuncio": "Renault Sandero 1.6 8V EXPRESSION",
        "obsevacoes": "KMS DE ESTRADA , CARRO EXCELENTE E SEM DETALHES , COMPLETO , COM SOM ORIGINAL E CONTROLE DE SOM NO VOLANTE , RODAS DO MEGANE COM 4 PNEUS NOVOS ( RODARAM APENAS 800 KMS ) .\nTRANSFIRO FINANCIAMENTO DO BANCO SANTANDER R$10.900,00 NA MÃO + 29 x 730,65 -  TRANSFERÊNCIA IMEDIATA COM TAXA DE R$675,00 POR CONTA DO COMPRADOR - NÃO ESTÁ EM ATRASO PRÓXIMA PARCELA VENCE EM 25/11/17 . ENTREGO QUITADO POR 26.900,00 \nCARRO ESTÁ EM OURO BRANCO , MAS ESTOU SEMPRE INDO A BH E POSSO IR NELE PARA MOSTRAR O INTERESSADO. TROCA EM CARROS DO MEU INTERESSE NO VALOR MAXIMO DE R$16.000,00 .",
        "proprietario": {
            "cidade": "  BELO HORIZONTE",
            "contato": "(31)99816-2288",
            "nome": "BRUNO CÉSAR"
        },
        "valorVeiculo": "R$ 10.900,00 + financiamento",
        "visualizacoes": 148
    }
]
```