## Documentação do serviço de Mock - Direct-Participant(PSP)

<br/>
<br/>

### O serviço será responsável por:

- Mockar os dados necessários para criar e consultar um pedido/Order;
- Criar Order;
- Listar Order;
- Retornar endpoint com o Payload.

<br/>
<br/>

### OBSERVAÇÕES DO SERVIÇO:

- Serviço baseado na documentação da Shipay, denominada PSP pelas regras do PIX;
- O serviço será mockado por meio da utilização do bando de dados: _mongodb_;
- O acesso se derá apenas por meio de utilização de chave de autenticação.

<br/>
<br/>

### Parâmetros do Header:

**authorization:** _string_

_required_

uma key que deve ser passada no header e utilizada para autorizar a requisição feita.

<br/>
<br/>

### <span style="color:Navy">Criar Order</span>

Este serviço cria um pedido de pagamento no PIX.

```
POST: /order
```

<br>

#### SCHEMA - Corpo da Requisição:

**buyer:** object

Informações do comprador.

{

**cpf:** _string_

CPF do comprador  

**email:** _string_

Endereço de e-mail do comprador

**first_name:** _string_

Primeiro nome do comprador

**last_name:** _string_

Último nome do comprador

**phone:** _string_

Número de telefone do comprador

}
<br>

**callback_url:** _string_

url com notificação informando que houve uma alteração no status do pedido.

<br>

**items:** _Array of objects (Item)_

_required_

Lista de itens do pedido. É obrigatório enviar ao menos um item.

Array() [

**item_title:** _string_ `<= 100 characters`

Nome do item

**quantity:** _number_

Quantidade do item

**unit_price** _number_

Valor unitário do item

]

<br>

**order_ref:** _string ```<= 255 characters_```

_required_

Número de referência do pedido no sistema.

<br>

**total:** _number_

_required_

Valor total do pedido. Este valor tem que ser igual ao somatório dos valores dos itens

<br>

**wallet:** _string_

_required_

Fixo em : `"pix"`

Nome da carteira digital

```json
{
  "buyer": {
    "cpf": "000.000.000-00",
    "email": "rob.dias@gmail.com",
    "first_name": "Roberto",
    "last_name": "Dias",
    "phone": "(11) 99999-9999"
  },
  "callback_url": "url",
  "items": [
    {
      "item_title": "batata doce",
      "quantity": 2.1626,
      "unit_price": 3.69
    }
  ],
  "order_ref": "pedido-qualquer-123",
  "total": 7.98,
  "wallet": "pix"
}
```

<br/>

### POST- Tipos de retorno:

<br>

<span style="color:green">**código 200</span>:** _Order Created_

quando a requisição ocorre de forma correta e as informações da Order são retornadas.

#### **SCHEMA** - Corpo da Resposta: _/_

<br>

**order_id:** _string_

ID do pedido no MOCK-PSP

<br>

**qr_code:** _string_

QR Code em imagem, codificado em Base64

<br>

**qr_code_text:** _string_

QR Code em formato de texto

<br>

**status:** _string_

Status do pedido/pagamento. Neste caso, o único status possível é:

| **descrição** |                                             |
| ------------- | ------------------------------------------- |
| pending       | Pedido aberto e ainda não pago ou cancelado |

<br>

```json
{
  "order_id": "5fd26150b08407001780629c",
  "qrcode": "data:image/gif;base64,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",
  "qr_code_text": "https://mockdirectparticpant.herokuapp.com/payloads/5fd26150b08407001780629d",
  "status": "pending"
}
```

<br>

<span style="color:red">**código 400</span>:** _Bad Request_

quando o corpo da requisição é inválido ou está incorreto;

<br>

<span style="color:red">**código 401</span>:** _Unauthorized_

quando o corpo da requisição não é enviado;

<br>

<span style="color:red">**código 403</span>:** _User not authorized_

quando o token passado para a validação não é encontrado ou é invalido;

<br>

<span style="color:red">**código 500</span>:** _Error creating the order_

quando ocorre um erro interno no servidor;

<br/>
<br/>

### <span style="color:Navy">Listar Order</span>

Este serviço retorna informações de um pedido específico. Deve ser utilizado para consultar o status do pedido após a sua criação e confirmar se o comprador efetuou o pagamento, ou seja, se o status mudou de _pending_ para _approved_.

```
GET: /order/{order_id}
```

<br/>

### Tipos de retorno:

<br>

<span style="color:green">**código 200</span>:** _Order Status_

quando tudo ocorreu bem e as informações da chave do usuário são retornadas, além disso, no header é retornado informações relacionadas ao RateLimit;

<br>

#### **SCHEMA** - Corpo da Resposta: _/_

**created_at:** _string_

Data e horário da criação do pedido

<br>

**external_id:** _string_

Número de referência do pedido no sistema(igual ao 'order_ref' do POST /order)

<br>

**items:** _Array of objects (Item)_

Lista de itens do pedido.

<br>

**order_id:** _string_

ID do pedido na Shipay

<br>

**paid_amount:** _number_

Valor pago pelo cliente. Utilizado para o PDV verificar se o valor pago é igual ao valor do pedido.

<br>

**status:** _string_

Status do pedido/pagamento. Neste caso, os status possíveis são:

| status         | descrição                                                                                                                                                                                                                       |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| pending        | Pedido aberto e ainda não pago ou cancelado                                                                                                                                                                                     |
| approved       | Pedido aprovado na carteira digital                                                                                                                                                                                             |
| cancelled      | Pedido (ainda não pago) cancelado na carteira digital                                                                                                                                                                           |
| expired        | Pedido expirado após 60 minutos com status "pending"                                                                                                                                                                            |
| refunded       | Pagamento devolvido ao comprador                                                                                                                                                                                                |
| refund_pending | Pagamento com devolução solicitada. Status aplicável somente à carteira Cielo. Os pagamentos com status = 'refund_pending' são estornados no dia após a confirmação do pagamento, quando o status será alterado para 'refunded' |
|                |                                                                                                                                                                                                                                 |

<br>

**total_order:** _number_

Valor total do pedido (igual ao 'total' do **POST /order**)

<br>

**updated_at:** _string_

Última atualização do pedido (data e horário)

<br>

**wallet:** _string_

Fixo em: `"pix"`

Nome da carteira digital

<br>

```json
{
  "id": "5fd26150b08407001780629c",
  "wallet": "pix",
  "external_id": "123123-1231-231-212",
  "status": "approved",
  "paid_amount": 354.99,
  "total_order": 354.99,
  "callback_url": "url",
  "items": [
    {
      "item_title": "conta de luz",
      "quantity": 1,
      "unit_price": 354.99
    }
  ],
  "created_at": "2020-12-10T17:56:32.008Z",
  "updated_at": "2020-12-10T17:56:37.152Z"
}
```

<br>

<span style="color:red">**código 401</span>:** _Unauthorized_

quando o parâmetro da consulta não é enviado;

<span style="color:red">**código 403</span>:** _Permission Denied_

quando o token passado para a validação não é encontrado ou é invalido;

<span style="color:red">**código 404</span>:** _Order not Found_

quando o order_id passado para consulta não é encontrado;

<span style="color:red">**código 500</span>:** _Error creating the order_

quando ocorre um erro interno no servidor;

<br/>
<br/>

### <span style="color:Navy">Retornar Payload.</span>

Este serviço retorna, assinadas, as informações do payload JSON do QR Code dinâmico

```
GET: /payloads/<hash_obtida_no_qr_code_text>
```

<br/>

### Tipos de retorno:

<span style="color:green">**código 200</span>:** _Order Status_

```json
"eyJ4NXQiOiJENTd2Q2dnRHg0SWU4MlN3X29MdG9tSmJNeE0iLCJqa3UiOiJsb2NhbGhvc3Q6MzAwMC9qd2siLCJraWQiOiI3VXdORFF5TFViNjVyQmwzdDNMVjJvRXR3X3JjQkw2WjBWdEdrMzdSVGVVIiwiYWxnIjoiUlMyNTYifQ.eyJpZCI6IjVmZDI2MTUwYjA4NDA3MDAxNzgwNjI5ZCIsImNhbGVuZGFyaW8iOnsicmVjZWJpdmVsQXBvc1ZlbmNpbWVudG8iOmZhbHNlLCJleHBpcmFjYW8iOiIyMDIwLTEyLTEwVDE4OjU2OjMyLjA0MFoifSwiZGV2ZWRvciI6eyJjcGYiOiIxMjM0NTY3ODkwMCIsIm5vbWUiOiJqb2FvemltIHNvdXphIn0sInZhbG9yIjp7Im9yaWdpbmFsIjozNTQuOTl9LCJjaGF2ZSI6IjMwLjMyMi4wNzQvMDAwMS0wNSIsInR4SWQiOiI2LjM2ODc4MzIxMzU1OTAzNWUrMzQiLCJ2ZXJzYW8iOiIxLjAuMCJ9.pp-mwMc_2Tgsc5k-dW7lZjSvUn3S8qcJM6MlpFxVGu-_kU5PfnzIQ6E0HwnpalEikyhY5EvRH-NIvSoPPzS_J9em70nhXs9Fi_6jLKz4ljLliMIzOkkVHklIBjVRHU42Lgp_wh90zAQEwvVIcmBd4lAIaD7uwJziNji3qpgSuTz5to3vDhzsRf1hNaI1P4YVeZv5i9QlYNd4U3YVNwe4VkcRFGOjFHQ2Q9D1QThnVwPjAn4iXEAXbTfuYpLG1Mic9vZrlvUSZz9f3l6se41VoCYTkhWQxA-e2uzPz8cOTn143MfkdDoBxO-HW-Lm6CLDAXXpu4n7RFY3YcPe1seiOQ"
```

<br>

<span style="color:red">**código 400</span>:** _Id out of expected format_

quando o id passado para a consulta está incorreto;

<br>

<span style="color:red">**código 404</span>:** _Payload not found_

quando o Payload não é encontrado;

<br>

<span style="color:red">**código 500</span>:** _Error_

quando ocorre um erro interno no servidor;

<br>

[Link para mais informações: PIX-API](https://github.com/lift-learning/pix-api)
[Link para mais informações: API-SHIPAY](https://api-staging.shipay.com.br/docs.html)
