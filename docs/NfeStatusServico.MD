# CONSULTA STATUS DO SERVIÇO

Serviço destinado à consulta do status do serviço prestado pelo Portal da Secretaria de Fazenda Estadual.

**Endpoint:** /api/v1/status
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


### Mensagem de Envio

```json
{
 "tpAmb": 2,
 "razaoSocial": "DEV E DEVELOPER TELECOMUNICACOES LTDA",
 "cnpj": "11551180000116",
 "siglaUf": "SC",
 "certPasswd": "12654821811",
 "certificado": "(certificado codificado em base 64)"
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
        "verAplic": "SVRS201805211008",
        "cStat": "107",
        "xMotivo": "Servico em Operacao",
        "cUF": "42",
        "dhRecbto": "2018-10-09T09:41:00-03:00",
        "tMed": "1",
        "dhRetorno": "",
        "xObs": ""
      }
    }
  ]
}
```
