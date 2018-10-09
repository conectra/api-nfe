# INUTILIZAÇÃO DE NUMERAÇÃO DE NF-e 

Serviço destinado à inutilização de numeração de NF-e.

**Endpoint:** /api/v1/inutilizar
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
| serie | Série que contém a numeração a ser inutilizada
| numeroInicio | Número inicial da faixa a ser inutilizada
| numeroFim | Número final da faixa a ser inutilizada
| justificativa | Justificativa para inutilização da faixa de numeração


### Mensagem de Envio

```json
{
 "tpAmb": 2,
 "razaoSocial": "DEV E DEVELOPER TELECOMUNICACOES LTDA",
 "cnpj": "11551180000116",
 "siglaUf": "SC",
 "certPasswd": "12654821811",
 "certificado": "(certificado codificado em base 64)",
 "serie": 2,
 "numeroInicio": 117,
 "numeroFim": 117,
 "justificativa": "Teste de operação do sistema"
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
          "bStat" :  true,
          "versao" :  "4.00",
          "tpAmb" :  2,
          "verAplic" :  "SVRS201808211440",
          "cStat" :  102,
          "xMotivo" :  "Inutilizacao de numero homologado",
          "cUF" :  42,
          "dhRecbto" :  "2018-10-09T10:21:03-03:00",
          "ano" :  18,
          "CNPJ" :  "13004289000169",
          "mod" :  55,
          "serie" :  2,
          "nNFIni" :  118,
          "nNFFin" :  118,
          "nProt" :  "342180004432074"
      }
    }
  ]
}
```