## Plano de Gerenciamento e Configuração de Software

<br/>
<br/>

### 1. Introdução
O objetivo deste documento é abordar os procedimento relacionados a gerência e configuração de software neste projeto. Objetiva-se padronizar e explicitar as políticas de contribuição a serem seguidas pela equipe durante o desenvolvimento e manutenção do projeto.

<br/>
<br/>

### 2. Ferramentas

|Ferramenta|Descrição|
|----------|---------|
|TSLint|Ferramenta de análise estática extensível que verifica o código TypeScript para erros de legibilidade, manutenção e funcionalidade. https://www.npmjs.com/package/tslint|
|ESLint|Ferramenta para analisar estaticamente o código para encontrar problemas rapidamente. https://eslint.org/|
|ESLint|Ferramenta para analisar estaticamente o código para encontrar problemas rapidamente.https://eslint.org/|

<br/>
<br/>

### 3. Políticas de Contribuição

<br/>

#### 3.1 Folha de Estilo
	O padrão adotado no código deverá seguir a folha de estilo do Airbnb.

<br/>

#### 3.2 Política de Commits
Os commits deverão ser atômicos. Para isso, ele deveria conter uma única alteração, seguindo o padrão de folha de estilo, e com uma descrição significativa.

<br/>

#### 3.3 Política de Branches
As branches serão criadas com base no modelo estabelecido pelo Gitflow.

<br/>

- A **master** é a branch principal do projeto. Ela conterá todas as funcionalidades estáveis e homologadas.

- A **develop** é a branch de desenvolvimento. Todas as branches (bug, hotfix, estória ou task) deverão ser criadas a partir dela e quando finalizadas, mescladas (merged) nela a partir do Pull Request.

- A **staging** é a branch que será usada para homologar novas funcionalidades. O ambiente de homologação é feito na AWS. Após aprovação, será mesclada na master. Ex.: release/1.0.0

- A **hotfix** é a branch que será usada quando tiver um erro crítico na master, branch de produção. Ex.: hotfix/bug-alteracao-senha
As branches para as features deverão ser criadas a partir da develop e deverão ser nomeadas com a numeração e nome da História de Usuário a ser desenvolvida. Ex.: feature/us_*

<br/>
<br/>

#### 3.4 Política de Pull Requests

Os Pull Requests (PR) poderão ser abertos durante o desenvolvimento da feature, como draft (rascunho) para ser acompanhado, ou após a finalização da História de Usuário.
Para o PR ser considerado completo para ser revisado, ele deverá seguir alguns requisitos:
- template para PRs;
- padrão de branches;
- padrão de commits;
- ter todas as tarefas da História de Usuário realizadas;
- ter a build no Continuous Integration (CI) construída com sucesso.

<br/>

#### 3.5 Política de Revisão de Código
	Após o Pull Request ser considerado feito, pelo menos um desenvolvedor pleno deverá revisar o PR, para ver se segue a política de Pull Requests, e se o que foi desenvolvido atende o que foi solicitado.
  Com o passar do tempo e ganho de maturidade dos desenvolvedores juniores, eles também poderão fazer parte das revisões.

<br/>
<br/>

### Pipeline
	O pipeline de integração contínua deve possuir os passos de verificação de estilo de código, build e testes. Essas etapas devem ser gerenciadas por uma ferramenta de CI como o Bitbucket. O CI deve ser executado toda vez que um PR for aberto e deve ser um critério bloqueio de merge do mesmo. Enquanto o PR estiver aberto, todo push na branch executará uma verificação no CI.
	Bitbucket é um serviço de hospedagem de projetos controlados através do Mercurial, um sistema de controle de versões distribuído e é configurado utilizando a linguagem python.

