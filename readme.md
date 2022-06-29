# API Placa Fipe

API REST Full que retorna os dados e o valor da FIPE do veículo consultado pela placa ou o desvalorizômetro do veículo.
Também suporta placas padrão Mercosul.

## [Consulta Placa](#consultando-o-valor-da-fipe-pela-placa-do-veículo-getplacafipe)
## [Desvalorizômetro](#desvalorizometro)
## [Cotas](#consultando-a-quantidade-de-quotas-usadas-no-dia-getquotas)
## [Planos e Valores](#planos-e-valores-1)
## [Códigos dos retornos](codigos.md)
## [Contato](#contatos)

## Consultando o valor da Fipe pela Placa do veículo (getplacafipe)

Retorna os dados e o valor da FIPE do veículo consultado pela placa.

### Requisição POST https://api.placafipe.xyz/getplacafipe

```php
curl "https://api.placafipe.xyz/getplacafipe" \
  -X POST \
  -d "{\"placa\": \"ABC1234\",\"token\": \"aqui_vai_o_token\"}" \
  -H "Content-Type: application/json" 
```

#### Parâmetros

|Nome|Tipo|Required|Descrição|
|---|---|---|---|
|placa|String|Required|Placa do veículo a ser consultado|
|token|String|Required|Token gerado pelo sistema através da aquisição de um dos planos|
|tipo_veiculo|Integer|Opcional|1-Automóveis e Utilitários leves, 2-Motocicletas e 3-Caminhões e Microônibus|

### Resposta

```json
{
  "codigo": 1,
  "msg": "total de 2 modelo(s) encontrado(s)",
  "fipe": [
    {
      "similaridade": "100.00",
      "correspondencia": "100.00",
      "marca": "FIAT",
      "modelo": "BRAVO ESSENCE 1.8 FLEX 16V 5P",
      "ano_modelo": 2013,
      "codigo_fipe": "001337-4",
      "mes_referencia": "maio de 2022",
      "combustivel": "GASOLINA",
      "valor": "37527.00",
      "desvalorizometro": "MjAxMyM1NDQ4IzIwMTMjMjAxMyMxIzIxIzEjQlJBVk8gRVNTRU5DRSAxLjggRkxFWCAxNlYgNVAgLSBHQVNPTElOQSM4MGVlOTUyMjU5YTQxZTNlYmMzMDk1ZGQ1ZmM0MDkzYg==",
      "unidade_valor": "R$"
    },
    {
      "similaridade": "88.00",
      "correspondencia": "100.00",
      "marca": "FIAT",
      "modelo": "BRAVO ESSENCE DUALOGIC 1.8 FLEX 16V 5P",
      "ano_modelo": 2013,
      "codigo_fipe": "001338-2",
      "mes_referencia": "maio de 2022",
      "combustivel": "GASOLINA",
      "valor": "37699.00",
      "desvalorizometro": "MjAxMyM1NDQ5IzIwMTMjMjAxMyMxIzIxIzEjQlJBVk8gRVNTRU5DRSBEVUFMT0dJQyAxLjggRkxFWCAxNlYgNVAgLSBHQVNPTElOQSM5OTMyMmE2NjRjOGYyMGUxYjRmOTQ0YmQwMzQ5NmQ5YQ==",
      "unidade_valor": "R$"
    }
  ],
  "informacoes_veiculo": {
    "marca": "FIAT",
    "modelo": "BRAVO ESSENCE 1.8",
    "ano": "2012",
    "ano_modelo": "2013",
    "cor": "Prata",
    "chassi": "******1234",
    "municipio": "SAO PAULO",
    "uf": "SP",
    "segmento": "AUTO",
    "sub_segmento": "AU - HATCH MEDIO",
    "placa": "ABC1234",
    "cilindradas": "1800",
    "potencia": "132",
    "unidade_potencia": "cv",
    "combustivel": "ALCOOL / GASOLINA"
  },
  "tempo": 664,
  "undiade_tempo": "ms",
  "algoritmo": "phalcondecodev115",
  "placa": "ABC1234"
}
```

## Desvalorizometro

O campo desvalorizômetro vem do campo desvalorizometro do objeto "fipe" da consulta getplacafipe

### Requisição POST https://api.placafipe.xyz/getdesvalorizometro

```php
curl "https://api.placafipe.xyz/getdesvalorizometro" \
  -X POST \
  -d "{\"desvalorizometro\": \"MjAxMyM1NDQ4IzIwMTMjMjAxMyMxIzIxIzEjQlJBVk8gRVNTRU5DRSAxLjggRkxFWCAxNlYgNVAgLSBHQVNPTElOQSM4MGVlOTUyMjU5YTQxZTNlYmMzMDk1ZGQ1ZmM0MDkzYg==\",\"token\": \"aqui_vai_o_token\"}" \
  -H "Content-Type: application/json" 
```

#### Parâmetros

| Nome | Tipo | Required | Descrição |
|-|-|-|-|
| desvalorizometro | String | Required | Gerado através da consulta da [placa](#consultando-o-valor-da-fipe-pela-placa-do-veículo-getplacafipe)  |
| token | String | Required | Token gerado pelo sistema através da aquisição de um dos planos |

### Resposta

```json
{
  "codigo": 1,
  "msg": "total de 113 tabela(s) encontrada(s)",
  "marca": "FIAT",
  "modelo": "BRAVO ESSENCE 1.8 FLEX 16V 5P",
  "combustivel": "GASOLINA",
  "ano_modelo": 2013,
  "desvalorizometro": {
    "tabelas": [
      {
        "valor": "47100.00",
        "mes_ano_extenso": "janeiro de 2013",
        "unidade_valor": "R$"
      },
      {
        "valor": "48712.00",
        "mes_ano_extenso": "fevereiro de 2013",
        "unidade_valor": "R$"
      },
      {
        "valor": "48116.00",
        "mes_ano_extenso": "março de 2013",
        "unidade_valor": "R$"
      },
      {
        "valor": "48941.00",
        "mes_ano_extenso": "abril de 2013",
        "unidade_valor": "R$"
      },
      {
        "valor": "47400.00",
        "mes_ano_extenso": "maio de 2013",
        "unidade_valor": "R$"
      },
      {
        "valor": "47502.00",
        "mes_ano_extenso": "junho de 2013",
        "unidade_valor": "R$"
      },
      {
        "valor": "46662.00",
        "mes_ano_extenso": "julho de 2013",
        "unidade_valor": "R$"
      },
      {
        "valor": "47865.00",
        "mes_ano_extenso": "agosto de 2013",
        "unidade_valor": "R$"
      },
      {
        "valor": "48338.00",
        "mes_ano_extenso": "setembro de 2013",
        "unidade_valor": "R$"
      },
      {
        "valor": "47549.00",
        "mes_ano_extenso": "outubro de 2013",
        "unidade_valor": "R$"
      },
      {
        "valor": "47973.00",
        "mes_ano_extenso": "novembro de 2013",
        "unidade_valor": "R$"
      },
      {
        "valor": "48664.00",
        "mes_ano_extenso": "dezembro de 2013",
        "unidade_valor": "R$"
      },
      {
        "valor": "47955.00",
        "mes_ano_extenso": "janeiro de 2014",
        "unidade_valor": "R$"
      },
      {
        "valor": "47884.00",
        "mes_ano_extenso": "fevereiro de 2014",
        "unidade_valor": "R$"
      },
      {
        "valor": "47176.00",
        "mes_ano_extenso": "março de 2014",
        "unidade_valor": "R$"
      },
      {
        "valor": "47862.00",
        "mes_ano_extenso": "abril de 2014",
        "unidade_valor": "R$"
      },
      {
        "valor": "47155.00",
        "mes_ano_extenso": "maio de 2014",
        "unidade_valor": "R$"
      },
      {
        "valor": "46923.00",
        "mes_ano_extenso": "junho de 2014",
        "unidade_valor": "R$"
      },
      {
        "valor": "46257.00",
        "mes_ano_extenso": "julho de 2014",
        "unidade_valor": "R$"
      },
      {
        "valor": "45894.00",
        "mes_ano_extenso": "agosto de 2014",
        "unidade_valor": "R$"
      },
      {
        "valor": "45691.00",
        "mes_ano_extenso": "setembro de 2014",
        "unidade_valor": "R$"
      },
      {
        "valor": "45361.00",
        "mes_ano_extenso": "outubro de 2014",
        "unidade_valor": "R$"
      },
      {
        "valor": "45184.00",
        "mes_ano_extenso": "novembro de 2014",
        "unidade_valor": "R$"
      },
      {
        "valor": "44615.00",
        "mes_ano_extenso": "dezembro de 2014",
        "unidade_valor": "R$"
      },
      {
        "valor": "44067.00",
        "mes_ano_extenso": "janeiro de 2015",
        "unidade_valor": "R$"
      },
      {
        "valor": "43463.00",
        "mes_ano_extenso": "fevereiro de 2015",
        "unidade_valor": "R$"
      },
      {
        "valor": "42897.00",
        "mes_ano_extenso": "março de 2015",
        "unidade_valor": "R$"
      },
      {
        "valor": "42348.00",
        "mes_ano_extenso": "abril de 2015",
        "unidade_valor": "R$"
      },
      {
        "valor": "41810.00",
        "mes_ano_extenso": "maio de 2015",
        "unidade_valor": "R$"
      },
      {
        "valor": "41434.00",
        "mes_ano_extenso": "junho de 2015",
        "unidade_valor": "R$"
      },
      {
        "valor": "40738.00",
        "mes_ano_extenso": "julho de 2015",
        "unidade_valor": "R$"
      },
      {
        "valor": "41100.00",
        "mes_ano_extenso": "agosto de 2015",
        "unidade_valor": "R$"
      },
      {
        "valor": "41270.00",
        "mes_ano_extenso": "setembro de 2015",
        "unidade_valor": "R$"
      },
      {
        "valor": "40563.00",
        "mes_ano_extenso": "outubro de 2015",
        "unidade_valor": "R$"
      },
      {
        "valor": "39862.00",
        "mes_ano_extenso": "novembro de 2015",
        "unidade_valor": "R$"
      },
      {
        "valor": "39217.00",
        "mes_ano_extenso": "dezembro de 2015",
        "unidade_valor": "R$"
      },
      {
        "valor": "38864.00",
        "mes_ano_extenso": "janeiro de 2016",
        "unidade_valor": "R$"
      },
      {
        "valor": "37953.00",
        "mes_ano_extenso": "fevereiro de 2016",
        "unidade_valor": "R$"
      },
      {
        "valor": "37955.00",
        "mes_ano_extenso": "março de 2016",
        "unidade_valor": "R$"
      },
      {
        "valor": "37685.00",
        "mes_ano_extenso": "abril de 2016",
        "unidade_valor": "R$"
      },
      {
        "valor": "37215.00",
        "mes_ano_extenso": "maio de 2016",
        "unidade_valor": "R$"
      },
      {
        "valor": "36894.00",
        "mes_ano_extenso": "junho de 2016",
        "unidade_valor": "R$"
      },
      {
        "valor": "36615.00",
        "mes_ano_extenso": "julho de 2016",
        "unidade_valor": "R$"
      },
      {
        "valor": "36562.00",
        "mes_ano_extenso": "agosto de 2016",
        "unidade_valor": "R$"
      },
      {
        "valor": "36368.00",
        "mes_ano_extenso": "setembro de 2016",
        "unidade_valor": "R$"
      },
      {
        "valor": "36188.00",
        "mes_ano_extenso": "outubro de 2016",
        "unidade_valor": "R$"
      },
      {
        "valor": "35903.00",
        "mes_ano_extenso": "novembro de 2016",
        "unidade_valor": "R$"
      },
      {
        "valor": "36394.00",
        "mes_ano_extenso": "dezembro de 2016",
        "unidade_valor": "R$"
      },
      {
        "valor": "35532.00",
        "mes_ano_extenso": "janeiro de 2017",
        "unidade_valor": "R$"
      },
      {
        "valor": "34893.00",
        "mes_ano_extenso": "fevereiro de 2017",
        "unidade_valor": "R$"
      },
      {
        "valor": "34684.00",
        "mes_ano_extenso": "março de 2017",
        "unidade_valor": "R$"
      },
      {
        "valor": "34671.00",
        "mes_ano_extenso": "abril de 2017",
        "unidade_valor": "R$"
      },
      {
        "valor": "34626.00",
        "mes_ano_extenso": "maio de 2017",
        "unidade_valor": "R$"
      },
      {
        "valor": "35102.00",
        "mes_ano_extenso": "junho de 2017",
        "unidade_valor": "R$"
      },
      {
        "valor": "34133.00",
        "mes_ano_extenso": "julho de 2017",
        "unidade_valor": "R$"
      },
      {
        "valor": "33942.00",
        "mes_ano_extenso": "agosto de 2017",
        "unidade_valor": "R$"
      },
      {
        "valor": "34294.00",
        "mes_ano_extenso": "setembro de 2017",
        "unidade_valor": "R$"
      },
      {
        "valor": "34104.00",
        "mes_ano_extenso": "outubro de 2017",
        "unidade_valor": "R$"
      },
      {
        "valor": "33482.00",
        "mes_ano_extenso": "novembro de 2017",
        "unidade_valor": "R$"
      },
      {
        "valor": "32857.00",
        "mes_ano_extenso": "dezembro de 2017",
        "unidade_valor": "R$"
      },
      {
        "valor": "33305.00",
        "mes_ano_extenso": "janeiro de 2018",
        "unidade_valor": "R$"
      },
      {
        "valor": "33752.00",
        "mes_ano_extenso": "fevereiro de 2018",
        "unidade_valor": "R$"
      },
      {
        "valor": "33908.00",
        "mes_ano_extenso": "março de 2018",
        "unidade_valor": "R$"
      },
      {
        "valor": "32849.00",
        "mes_ano_extenso": "abril de 2018",
        "unidade_valor": "R$"
      },
      {
        "valor": "33276.00",
        "mes_ano_extenso": "maio de 2018",
        "unidade_valor": "R$"
      },
      {
        "valor": "33718.00",
        "mes_ano_extenso": "junho de 2018",
        "unidade_valor": "R$"
      },
      {
        "valor": "34160.00",
        "mes_ano_extenso": "julho de 2018",
        "unidade_valor": "R$"
      },
      {
        "valor": "33790.00",
        "mes_ano_extenso": "agosto de 2018",
        "unidade_valor": "R$"
      },
      {
        "valor": "33958.00",
        "mes_ano_extenso": "setembro de 2018",
        "unidade_valor": "R$"
      },
      {
        "valor": "34414.00",
        "mes_ano_extenso": "outubro de 2018",
        "unidade_valor": "R$"
      },
      {
        "valor": "33766.00",
        "mes_ano_extenso": "novembro de 2018",
        "unidade_valor": "R$"
      },
      {
        "valor": "33899.00",
        "mes_ano_extenso": "dezembro de 2018",
        "unidade_valor": "R$"
      },
      {
        "valor": "33218.00",
        "mes_ano_extenso": "janeiro de 2019",
        "unidade_valor": "R$"
      },
      {
        "valor": "32944.00",
        "mes_ano_extenso": "fevereiro de 2019",
        "unidade_valor": "R$"
      },
      {
        "valor": "32759.00",
        "mes_ano_extenso": "março de 2019",
        "unidade_valor": "R$"
      },
      {
        "valor": "32633.00",
        "mes_ano_extenso": "abril de 2019",
        "unidade_valor": "R$"
      },
      {
        "valor": "32548.00",
        "mes_ano_extenso": "maio de 2019",
        "unidade_valor": "R$"
      },
      {
        "valor": "32340.00",
        "mes_ano_extenso": "junho de 2019",
        "unidade_valor": "R$"
      },
      {
        "valor": "32104.00",
        "mes_ano_extenso": "julho de 2019",
        "unidade_valor": "R$"
      },
      {
        "valor": "31883.00",
        "mes_ano_extenso": "agosto de 2019",
        "unidade_valor": "R$"
      },
      {
        "valor": "31748.00",
        "mes_ano_extenso": "setembro de 2019",
        "unidade_valor": "R$"
      },
      {
        "valor": "31646.00",
        "mes_ano_extenso": "outubro de 2019",
        "unidade_valor": "R$"
      },
      {
        "valor": "31496.00",
        "mes_ano_extenso": "novembro de 2019",
        "unidade_valor": "R$"
      },
      {
        "valor": "31253.00",
        "mes_ano_extenso": "dezembro de 2019",
        "unidade_valor": "R$"
      },
      {
        "valor": "30871.00",
        "mes_ano_extenso": "janeiro de 2020",
        "unidade_valor": "R$"
      },
      {
        "valor": "30745.00",
        "mes_ano_extenso": "fevereiro de 2020",
        "unidade_valor": "R$"
      },
      {
        "valor": "30485.00",
        "mes_ano_extenso": "março de 2020",
        "unidade_valor": "R$"
      },
      {
        "valor": "30133.00",
        "mes_ano_extenso": "abril de 2020",
        "unidade_valor": "R$"
      },
      {
        "valor": "30029.00",
        "mes_ano_extenso": "maio de 2020",
        "unidade_valor": "R$"
      },
      {
        "valor": "29743.00",
        "mes_ano_extenso": "junho de 2020",
        "unidade_valor": "R$"
      },
      {
        "valor": "29425.00",
        "mes_ano_extenso": "julho de 2020",
        "unidade_valor": "R$"
      },
      {
        "valor": "29166.00",
        "mes_ano_extenso": "agosto de 2020",
        "unidade_valor": "R$"
      },
      {
        "valor": "29000.00",
        "mes_ano_extenso": "setembro de 2020",
        "unidade_valor": "R$"
      },
      {
        "valor": "29145.00",
        "mes_ano_extenso": "outubro de 2020",
        "unidade_valor": "R$"
      },
      {
        "valor": "29223.00",
        "mes_ano_extenso": "novembro de 2020",
        "unidade_valor": "R$"
      },
      {
        "valor": "29618.00",
        "mes_ano_extenso": "dezembro de 2020",
        "unidade_valor": "R$"
      },
      {
        "valor": "29799.00",
        "mes_ano_extenso": "janeiro de 2021",
        "unidade_valor": "R$"
      },
      {
        "valor": "29874.00",
        "mes_ano_extenso": "fevereiro de 2021",
        "unidade_valor": "R$"
      },
      {
        "valor": "30019.00",
        "mes_ano_extenso": "março de 2021",
        "unidade_valor": "R$"
      },
      {
        "valor": "30981.00",
        "mes_ano_extenso": "abril de 2021",
        "unidade_valor": "R$"
      },
      {
        "valor": "31148.00",
        "mes_ano_extenso": "maio de 2021",
        "unidade_valor": "R$"
      },
      {
        "valor": "31814.00",
        "mes_ano_extenso": "junho de 2021",
        "unidade_valor": "R$"
      },
      {
        "valor": "32598.00",
        "mes_ano_extenso": "julho de 2021",
        "unidade_valor": "R$"
      },
      {
        "valor": "33436.00",
        "mes_ano_extenso": "agosto de 2021",
        "unidade_valor": "R$"
      },
      {
        "valor": "34247.00",
        "mes_ano_extenso": "setembro de 2021",
        "unidade_valor": "R$"
      },
      {
        "valor": "34607.00",
        "mes_ano_extenso": "outubro de 2021",
        "unidade_valor": "R$"
      },
      {
        "valor": "34320.00",
        "mes_ano_extenso": "novembro de 2021",
        "unidade_valor": "R$"
      },
      {
        "valor": "35153.00",
        "mes_ano_extenso": "dezembro de 2021",
        "unidade_valor": "R$"
      },
      {
        "valor": "36875.00",
        "mes_ano_extenso": "janeiro de 2022",
        "unidade_valor": "R$"
      },
      {
        "valor": "36201.00",
        "mes_ano_extenso": "fevereiro de 2022",
        "unidade_valor": "R$"
      },
      {
        "valor": "36015.00",
        "mes_ano_extenso": "março de 2022",
        "unidade_valor": "R$"
      },
      {
        "valor": "36021.00",
        "mes_ano_extenso": "abril de 2022",
        "unidade_valor": "R$"
      },
      {
        "valor": "37527.00",
        "mes_ano_extenso": "maio de 2022",
        "unidade_valor": "R$"
      }
    ]
  },
  "tempo": 12,
  "undiade_tempo": "ms",
  "algoritmo": "phalcondesv115"
}
```

## Consultando a quantidade de quotas usadas no dia (getquotas)

Retorna os dados de uso das quotas diárias pelo token.

### Requisição POST https://api.placafipe.xyz/getquotas

```php
curl "https://api.placafipe.xyz/getquotas" \
  -X POST \
  -d "{\"token\": \"aqui_vai_o_token\"}" \
  -H "Content-Type: application/json" 
```

#### Parâmetros

| Nome | Tipo | Required | Descrição |
|-|-|-|-|
| token | String | Required | Token gerado pelo sistema através da aquisição de um dos planos |

### Resposta

```json
{
  "codigo": 1,
  "msg": "Uso diário: 10 consultas",
  "limite_diario": 185,
  "uso_diario": "0"
}
```

## Planos e Valores

<img src='https://placafipe.com.br/planos.png' />


## Contatos

[E-mail](mailto:contato@placafipe.com.br)
