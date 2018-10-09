# EVENTO DE CORREÇÃO DE NFE

Serviço destinado à emissão de evento para correção de informações da NF-e.

**Endpoint:** /api/v1/corrigir
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
| correcao | Informações relacionadas a correção a serem aplicadas a NF-e


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
 "correcao": "Informações relacionadas a correção da respectiva NF-e"
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
        "idLote": "201810091006375",
        "tpAmb": 2,
        "verAplic": "SVRS201809101416",
        "cOrgao": 42,
        "cStat": 128,
        "xMotivo": "Lote de Evento Processado",
        "aEvent" : [
          [
            {
              "tpAmb": 2,
              "verAplic": "SVRS201809101416",
              "cOrgao": 42,
              "xMotivo": "Evento registrado e vinculado a NF-e",
              "cStat": 135,
              "chNFe": "42180913004289000169550010000000211398633734",
              "tpEvento": 110110,
              "nSeqEvento": 1,
              "cOrgaoAutor": "",
              "dhRegEvento": "2018-10-09T10:06:38-03:00",
              "CNPJDest": "85641066000113",
              "emailDest": "",
              "nProt": "342180004431970"              
            }
          ]
        ],
        "xmlProt": "(Arquivo XML de retorno do SEFAZ)"
      }
    }
  ]
}
```