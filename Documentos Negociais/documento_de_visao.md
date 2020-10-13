## Documento de Visão - Vamos Parcelar

### 1. Introdução

#### 1.1 Propósito
Este documento apresenta as diretrizes abstratas que guiarão o projeto, especificamente os requisitos relevantes, assim como os limites e restrições evidentes que dão uma visão geral. Essa visão viabiliza a identificação e a produção de documentos e requisitos mais técnicos, assim como do próprio sistema.
A visão deve servir como forma de reunir os participantes do grupo sob as mesmas ideias e lhes dar um contexto para viabilizar as decisões no que concerne aos requisitos do sistema.

<br/>

#### 1.2 Escopo
O presente projeto permitirá o sistema da Vamos Parcelar a validar a chave DICT utilizada para realizar um pagamento, através de um mock de validação a ser desenvolvido pela equipe de pesquisadores. Além disso também irá permitir o usuário realizar pagamentos a vista por meio de pagamentos instantâneos (PIX), através da geração de um QR code dinâmico e com o auxílio de um mock do participante indireto, que também será desenvolvido pela equipe.

<br/>

#### 1.3 Definições, Acrônimos e Abreviações

|Acrônimo/Abreviação|Definição|
|-------------------|---------|
|VP                 |Vamos Parcelar|
|PIX                |Pagamento Instantâneo|

<br/>

#### 1.4 Referências Bibliográficas

<br/>
Documento de Visão. International Business Machines Corporation (IBM). Disponível em: <https://www.ibm.com/support/knowledgecenter/pt-br/SSWMEQ_4.0.6/com.ibm.rational.rrm.help.doc/topics/r_vision_doc.html>. Acesso em: 5 de ago. de 2020.

<br/>
Quem somos. Vamos Parcelas. Disponível em: <https://vamosparcelar.com.br/quem-somos/>.  Acesso em: 5 de ago. de 2020.
Pagamentos Instantâneos. Banco Central do Brasil. Disponível em: <https://www.bcb.gov.br/estabilidadefinanceira/pagamentosinstantaneos>. Acesso em Acesso em: 5 de ago. de 2020.

<br/>
<br/>

### 2. Posicionamento

<br/>
<br/>

#### 2.1 Oportunidade de Negócio
A Vamos Parcelar é uma empresa que facilita pessoas físicas ou jurídicas a regularizarem seus débitos com instituições públicas e privadas.
Com o surgimento do PIX, a VP poderá adicioná-lo em suas opções de pagamento. Pelo fato do dinheiro ser transferido a qualquer momento e ser liquidado em até 10 segundos, o cliente que optou por usá-lo para pagar totalmente ou parcialmente suas contas.

<br/>
<br/>

#### 2.2 Instrução do Problema

|O problema de |inclusão de um novo meio de pagamento|
|--------------|-------------------------------------|
|afeta         |os clientes que possuem interesse em usar o novo meio de pagamento|
|O importante do problema é|permitir a possibilidade de realizar o novo meio de pagamento|
|Uma solução bem sucedida incluiria | implementar a nova funcionalidade de pagamento no sistema|

<br/>
<br/>


#### 2.3 Instrução de Posição do Produto

|Para o|cliente que utiliza plataforma Vamos Parcelar|
|------|---------------------------------------------|
|quem|Vamos Parcelar|
|O|PIX|
|é|um meio de pagamentos instantâneos|
|que|realiza transações de transferências bancárias em poucos segundos.|
|De outro modo|ao que ocorre em uma operação de simulação de  pagamento com boletos, com tempo de compensação e em horário comercial ou cartões de crédito e débito, com geração de custo|
|Nosso produto|Realiza transferências instantâneas a qualquer horário ou instituição financeira desde que esta mesma esteja vinculada ao PIX

<br/>
<br/>

### 3. Descrições da Parte Interessada e do Usuário
|Designação|Descrição|
|----------|---------|
|Instituição Financeira de Pagamento|Provedor de serviços de pagamentos|
|Clientes|Pessoas físicas ou jurídicas que precisam realizar o pagamento ou parcelamento de débitos públicos ou privados.|

<br/>
<br/>

### 4. Visão Geral do Produto

<br/>

#### 4.1 Perspectiva do produto		
	O objetivo  do produto é possibilitar que a plataforma da Vamos Parcelar (vendor) se torne um local onde o cliente possa pagar suas diferentes contas de uma única vez e por vários meios de pagamentos. Entre esses, se destaca o PIX por realizar o recebimento instantâneo em conta por parte do pagador primário (cliente).
	Principal funcionalidade levantada:
  
  - Conversão do valor final, em forma parcial ou total, da negociação realizada dentro da plataforma Vamos Parcelar em um formato PIX (QR Code dinâmico)

<br/>
<br/>

### 5. Restrições

- A aplicação deve ser desenvolvida até dezembro de 2020;
- A aplicação deve ser funcional na plataforma web;
- A aplicação deve ser intuitiva para o usuário.

<br/>
<br/>

### 6. Faixas de Qualidade
<br/>

#### 6.1 Requisitos do Desempenho
O desempenho da aplicação dependerá do poder de processamento do dispositivo do usuário e de sua velocidade de internet, já que a aplicação só poderá realizar suas operações quando on-line.

<br/>
<br/>

#### 6.2 Requisitos de Design
A aplicação deverá seguir o design adotado pela aplicação principal da Vamos Parcelar.

<br/>
<br/>

#### 6.3 Requisitos de Portabilidade
Aplicação web, que deverá funcionar nos principais navegadores de internet.

<br/>
<br/>

#### 6.4 Requisitos de Confiabilidade
Por tratar dados sensíveis, deverá ter uma boa segurança na requisição, tratamento e apresentação dos dados pessoais.

<br/>
<br/>

#### 6.5 Requisitos de Privacidade
Somente os proprietários dos dados e a Vamos Parcelar poderão acessar os dados pessoais cadastrados na aplicação.

<br/>
<br/>

### 7. Prioridades e precedência
A prioridade é do usuário poder realizar pagamentos usando PIX através do QR Code dinâmico, que é gerado a partir da chave DICT.

