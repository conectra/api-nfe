# AUTORIZAÇÃO DE NF-e 

Serviço destinado ao envio e consulta de lote de NF-e (Autorização)

**Endpoint:** /api/v1/autorizar
**Method** POST

## Leiaute de Mensagem de Entrada

### Parametros

| Variável | Detalhamento  |
| :---:  | :--- |
| tpAmb | Tipo de ambiente de emissão. 1 - Produção / 2 - Homologação |
| razaoSocial | Razão social do contribuinte. |
| cnpj | Inscrição federal do contribuinte.  |
| certPasswd | Senha do certificado digital do contribuinte |
| certificado | Certificado dogital .pfx codificado em base 64 |
| nfe | Representação da NF-e a ser estruturada a partir do respectivo [SCHEMA]() |


### Mensagem de Envio

```json
{
 "tpAmb": 2,
 "razaoSocial": "DEV E DEVELOPER TELECOMUNICACOES LTDA",
 "cnpj": "11551180000116",
 "siglaUf": "SC",
 "certPasswd": "12654821811",
 "certificado": "(certificado codificado em base 64)",
 "nfe" : "{...} (compilação de campos representando a NF-e)"
}
```

## Leiaute de Mensagem de Retorno

### Mensagem de Retorno

O retorno da requisição conterá uma  em formato JSON com a seguinte estrutura.

```json
{
  "status": true,
  "message": "1 registros processados e 0 não foram processados. ",
  "count": 1,
  "detail": "(OPERACAO REALIZADA COM SUCESSO.)",
  "data": [
    {
      "success": true,
      "message": "OPERACAO REALIZADA COM SUCESSO.",
      "extra": {          
        "bStat":  true,
        "versao":  "4.00",
        "tpAmb":  2,
        "cStat":  104,
        "verAplic":  "SVRS201810051010",
        "xMotivo":  "Lote processado",
        "dhRecbto":  "2018-10-09T09:55:44-03:00",
        "cUF":  42,
        "nRec":  "423002182956758",
        "aProt": {
            "chNFe":  "42180913004289000169550010000000211398633734",
            "dhRecbto":  "2018-10-09T09:55:44-03:00",
            "nProt":  "342180004431921",
            "digVal":  "FaCXEdlk0mq1xg2ZqmX72A3JJ/M=",
            "cStat":  100,
            "xMotivo":  "Autorizado o uso da NF-e"
        },                     
        "xmlProt": "(XML retorno protocolado pelo SEFAZ)"
      }
    }
  ]
}
```