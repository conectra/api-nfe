# CONSULTA SITUAÇÃO ATUAL DE NFE

Serviço destinado à consulta da situação atual da NF-e.

**Endpoint:** /api/v1/consultar
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
| chave | Chave do documento fiscal a ser consultado


### Mensagem de Envio

```json
{
 "tpAmb": 2,
 "razaoSocial": "DEV E DEVELOPER TELECOMUNICACOES LTDA",
 "cnpj": "11551180000116",
 "siglaUf": "SC",
 "certPasswd": "12654821811",
 "certificado": "(certificado codificado em base 64)",
 "chave" : "42180913004289000169550010000000211398633734"
}
```

## Leiaute de Mensagem de Retorno

### Mensagem de Retorno

O retorno da requisição conterá uma string em formato JSON com a seguinte estrutura.

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
        "bStat": true,
        "versao": "4.00",
        "tpAmb": "2",
        "verAplic": "SVRS201809061124",
        "cStat": "100",
        "xMotivo": "Autorizado o uso da NF-e",
        "cUF": "42",
        "dhRecbto": "2018-10-09T09:56:27-03:00",
        "chNFe" : "42180913004289000169550010000000211398633734",
        "aProt": {
          "chNFe": "42180913004289000169550010000000211398633734",
          "dhRecbto": "2018-10-09T09:55:44-03:00",
          "nProt": "342180004431921",
          "digVal": "FaCXEdlk0mq1xg2ZqmX72A3JJ",
          "cStat": "100",
          "xMotivo": "Autorizado o uso da NF-e"
        },
        "xmlProt": "(Arquivo XML de retorno do SEFAZ)"
      }
    }
  ]
}
```