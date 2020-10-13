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
- Todas as consultas devem ser realizadas para o endpoint /entries/{key}
- A key pode ser email, CPF/CNPJ ou telefone e ter no máximo 77 caracteres 

<br/>
<br/>

### Parâmetros do Header:

**PI-RequestingParticipant:** código identificador de 8 dígitos da Vamos Parcelar, ele deverá ser fictício no mock porque só é fornecido após o seu cadastro no SPI por um participante direto.

**PI-PayerId:** Valor hexadecimal de 64 caracteres, “Como sugestão de implementação, pode ser utilizado o valor hexadecimal da aplicação de HMAC-SHA-256 a um identificador do usuário, com chave de conhecimento restrito ao participante.”

**PI-EndToEndId:** uma String que deve ser gerada aleatoriamente e utilizada como um identificador da transação.

<br/>
<br/>

### Tipos de retorno:

**código 200:** quando tudo ocorreu bem e as informações da chave do usuário são retornadas, além disso, no header é retornado informações relacionadas ao RateLimit;

**código 404:** quando a chave passada para consulta não é encontrada;

**código 429:** quando o Rate Limit é atingido.

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

[Link para mais informações: PIX-API](https://github.com/lift-learning/pix-api)
[Link para mais informações: API-DICT](https://www.bcb.gov.br/content/estabilidadefinanceira/pix/API_do_DICT-v1.0.html#operation/getEntry)
