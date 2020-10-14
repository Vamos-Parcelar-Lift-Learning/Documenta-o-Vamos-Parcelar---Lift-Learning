## Documento de Arquitetura

<br/>
<br/>

### 1. Introdução
A arquitetura do projeto realizado em parceria com a Vamos Parcelar, é feita com base na arquitetura de microsserviços. São sete componentes mínimos, independentes e responsáveis que se comunicam por API Rest. A aplicação consistirá em uma aplicação web.

<br/>
<br/>

### 2. Representação arquitetural
Os quatro componentes da aplicação são:

- **VP-CHECKOUT:** serviço responsável pelos pagamentos realizados pelos clientes.

- **VP-CAPTURE:** serviço responsável pelo. Onde estará contida a controller do Pix.

- **MOCK-DICT:** serviço responsável pelos mocks dos dados necessários para a validação da chave Pix. 

- **MOCK-PSP:** serviço responsável pelos mocks das mensagens relacionadas a transação do Pix pelo participante direto. Os dados a serem mockados são:

<br/>
<br/>

[![](https://github.com/Vamos-Parcelar-Lift-Learning/Documentos/blob/main/Imagens/arquitetura.png)](https://github.com/Vamos-Parcelar-Lift-Learning/Documentos/blob/main/Imagens/arquitetura.png)

Imagem 1 - Relacionamento entre Serviços e Tecnologias

<br/>
<br/>

As tecnologias que serão utilizadas no projeto estão detalhadas nos diagramas abaixo, bem como se relacionam. A escolhas das tecnologias utilizadas se deu com base nas tecnologias já utilizadas pela empresa Vamos Parcelar.

<br/>
<br/>

#### Frontend:

- React js: é uma biblioteca utilizada para desenvolver aplicações web. A biblioteca será utilizada para implementação do front-end da aplicação;

- Typescript: é a linguagem utilizada no React. Por ser uma linguagem que faz a tipagem de dados, a experiência no desenvolvimento em equipe melhora;

- Redux: é um gerenciador de estados da aplicação;

- Material Design: é uma linguagem de design desenvolvida pela Google;

- Styled Components: são técnicas que permitem escrever código CSS real para estilizar, removendo o mapeamento entre componentes e estilos.

<br/>

#### Backend:

- Node.js: é um interpretador de JavaScript assíncrono com código aberto orientado a eventos, que foca no desenvolvimento de servidores. O interpretador será utilizado para implementação do back-end da aplicação;

- Typescript: é a linguagem utilizada no Node.js. Por ser uma linguagem que faz a tipagem de dados, a experiência no desenvolvimento em equipe melhora;

- Express.js: é um framework para aplicações web para Node.js. É feito para otimizar a construção de aplicações web e API's;

- MongoDB: é um banco de dados orientado a documentos. A tecnologia será utilizada para persistência de dados na aplicação.

- Mongoose: é uma biblioteca do Node.js que proporciona uma solução baseada em esquemas para modelar os dados da sua aplicação. Ele possui sistema de conversão de tipos, validação, criação de consultas e hooks para lógica de negócios;

- Spring: é um framework open source para a plataforma Java, um framework não intrusivo, baseado nos padrões de projeto inversão de controle e injeção de dependência.

<br/>
<br/>

### 3. Metas e restrições da arquitetura

- A aplicação deve ser funcional na plataforma web;

- A aplicação deve ter layout responsivo para se adaptar a diferentes tamanhos de tela;
Toda a aplicação receberá os dados por meio do mock do DICT e mock do PSP.

<br/>
<br/>

### 4. Visões arquiteturais

Na imagem 2, é apresentado o fluxograma com o fluxo da experiência do usuário com o sistema e funcionalidades, a fim de possibilitar a realização do serviço de pagamentos de débitos e consequentemente a geração do formato de pagamento aceito pelo PIX. Também é contemplado nesse fluxograma a delimitação do escopo onde entra a solução proposta no projeto.

<br/>
<br/>

### 5. Escalabilidade e desempenho
A aplicação deve ser modular, e respeitar as arquiteturas e convenções que já são utilizadas na Vamos Parcelar, para facilitação de sua manutenção. Utilizaremos linters e processos de revisão para adequação a esses padrões, bem como onde couber, TDD.

<br/>
<br/>

### 6. Indicativos de qualidade
Para assegurar a qualidade do produto a ser entregue será utilizado o ESLint, uma ferramenta de lint plugável para Javascript e JSX, que analisará o código fonte para sinalizar erros de programação, bugs e erros estilísticos, conforme o padrão da folha de estilo do projeto.
