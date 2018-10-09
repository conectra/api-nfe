# EVENTO DE CANCELAMENTO DE NFE

Serviço destinado à emissão de evento para cancelamento da NF-e.

**Endpoint:** /api/v1/cancelar
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
| justificativa | Justificativa para o cancelamento da respectiva NF-e
| protocolo | Protocolo de autorização da NF-e a ser cancelada


### Mensagem de Envio

```json
{
 "tpAmb": 2,
 "razaoSocial": "DEV E DEVELOPER TELECOMUNICACOES LTDA",
 "cnpj": "11551180000116",
 "siglaUf": "SC",
 "certPasswd": "12654821811",
 "certificado": "(certificado codificado em base 64)",
 "chave" : "42180913004289000169550010000000211398633734",
 "justificativa": "Teste de operação do sistema",
 "protocolo": "342180004431921"
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
        "bStat": true,
        "versao":  "4.00",
        "tpAmb":  2,
        "cStat":  101,
        "verAplic":  "SVRS201809061124",
        "xMotivo":  "Cancelamento de NF-e homologado",
        "dhRecbto":  "2018-10-09T10:58:50-03:00",
        "cUF":  42,
        "chNFe":  "42180913004289000169550010000000211398633734",
        "aProt": {
            "chNFe":  "42180913004289000169550010000000211398633734",
            "dhRecbto":  "2018-10-09T09:55:44-03:00",
            "nProt":  "342180004431921",
            "digVal":  "FaCXEdlk0mq1xg2ZqmX72A3JJ/M=",
            "cStat":  100,
            "xMotivo":  "Autorizado o uso da NF-e"
        },                      
        "aEvent": {         
            "tpAmb":  2,
            "verAplic": "SVRS201809101416",
            "cOrgao": 42,
            "xMotivo": "Evento registrado e vinculado a NF-e",
            "cStat": 135,
            "chNFe": "42180913004289000169550010000000211398633734",
            "tpEvento": "110110",
            "xEvento": "",
            "nSeqEvento": 1,
            "cOrgaoAutor": "",
            "dhRegEvento": "2018-10-09T10:06:38-03:00",
            "CNPJDest": "85641066000113",
            "emailDest": "",
            "nProt": "342180004431970"
        }
      }
    }
  ]
}
```