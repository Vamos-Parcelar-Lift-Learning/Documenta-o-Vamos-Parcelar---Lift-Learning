## Documentação do serviço de Mock - DICT
<br/>
<br/>

### O serviço será responsável por:

- Gerar a chave do DICT 
- Vincular chave aos dados bancários do usuário PIX - Dados gerados de forma dinâmica
- Validar chave - DICT
- Retornar endpoint com o resultado da validação realizada

<br/>
<br/>

### OBSERVAÇÕES DO SERVIÇO:

- O serviço será mockado por meio da utilização da biblioteca: *json server* 
- O acesso se derá apenas por meio de utilização de  chave de autenticação 

<br/>
<br/>

### Descrição do Schema implementado:

```
{
“type”: “object”,
“properties”: {
“Account”: {
“type”: “object”,
“properties”: {
    “AccountNumber”: string
    “AccountType”: string
    “Branch”: string
    “OpeningDate”: string
    “Participant”: string
},
  required: all
},
  “key”: string,
  “keyType”: “string”,
  “Owner”:{
    “properties”: {
      “Name”: string
      “TaxIdNumber”: number
      “Type”: string
      “tradeName”: string
  },
required: all
}
},
required: all
}
```

