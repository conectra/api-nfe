# GERAÇÃO DE DANFE

Serviço destinado à geração de DANFe em modelo nacional a partir de um XML NF-e.

**Endpoint:** /api/v1/danfe
**Method** POST

## Leiaute de Mensagem de Entrada

### Parametros

| Variável | Detalhamento  |
| :---:  | :--- |
| xmlNFe | XML de NF-e a partir do qual será gerada a DANFe |
| logomarca | Imagem logamarca codificada em base 64 do contribuinte |


### Mensagem de Envio

```json
{
 "xmlNFe": "(conteúdo xml a ser utilizado como fonte para geração da DANFe)",
 "logomarca": "(imagem codificada em base 64)"
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
        "danfe": "(DANFe formato pdf codificada em base 64)"        
      }
    }
  ]
}
```
