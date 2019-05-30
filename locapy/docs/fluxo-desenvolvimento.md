# Fluxo de Trabalho

A equipe optou por utilizar algumas cerimônias ágeis e o quadro Kanban para acompanhar o trabalho, realizando Sprints de 2 semanas.

## Papéis

Os papéis dentro da equipe são:

**PO** - Por definição, deveria haver alguém que fizesse esse papel, porém devido a falta de recursos a equipe optou que todos nós fizéssemos o papel de PO.

**Scrum Master** - Lucas Siqueira

**Time de desenvolvimento** - Bruno Lima, Lucas Araújo e Oseas Fernandes

**Time de negócios** - César Augusto, Lucas Siqueira e Vinicius Tavares

## Cerimônias

As cerimônias utilizadas são, por ondem cronológica:

**Planning** - Cerimônia em que a equipe realiza  o planejamento do que será realizado dentro da SPRINT. Se houver necessidade essa reunião será para que a equipe discuta os critérios de aceite, descrição, pontuação e tasks das estórias de usuário.

**Daily** - Cerimônia diária realizada no horário combinado pela equipe, a ideia é que o tempo seja utilizado para que cada integrante diga o que fez no dia anterior e o que fez/irá fazer no dia. Discussões técnicas podem ser feitas após a _daily_ .

**Review** - Cerimônia realizada após a conclusão da estória, o responsável pela estória apresentará para a equipe, se for aprovada entrará na fila para deploy, senão o desenvolvimento continua.

## Quadro Kanban

O quadro Kanban é utilizado para ter uma visão macro do andamento do processo de trabalho, a ferramenta escolhida foi o Trello, disponível em:
https://trello.com/b/Regw3bNx/locapy-sprint-n%C3%A3o-definida

**BACKLOG DO PRODUTO** - Representa todas as estórias escritas para o produto, o backlog é priorizado, as estórias do topo são as mais prioritárias.

**BACKLOG DA SPRINT** - Representa todas as estórias que serão feitas na Sprint atual, todas as estórias que entrarem para o backlog da sprint precisam ser revisadas pela equipe.

**EM DESENVOLVIMENTO** - Representa todas as estórias que estão sendo desenvolvidas no momento.

**CODE REVIEW** - Representa todas as estórias que terminaram o desenvolvimento e estão disponíveis para a equipe revisar o código. A revisão é feita pelo Github e precisa de 2 aprovações para estar pronta para a revisão. **Atenção: Não realize o Merge nessa etapa**

**REVISÃO** - Representa a etapa em que o responsável pelo desenvolvimento realiza o deploy no ambiente de DEV e apresenta para a equipe, caso a decisão seja unﾃ｢nime, o código entra na fila para deploy.
**Atenção: Não realize o Merge nessa etapa**

**AGUARDANDO DEPLOY** - Representa a etapa em que a estória está aguardando para fechar uma release e realizar o deploy, é importante que o PR esteja aberto no Github e a label identificando essa etapa.
**Atenção: Não realize o Merge nessa etapa**

**DEPLOY** - Representa a etapa em que uma release será fechada e o código entrará em produção, é importante criar uma tag no Git com o número da versão.

## Gitflow

### Branchs

Utilizamos o Git como ferramenta de versionamento de código e o Github para hospedar o código desenvolvido.
Definições de Branch's:

* **master** - Branch utilizado somente para funcionalidades já testadas e aprovadas pelo cliente.

* **develop** - Branch que contém o código em desenvolvimento da equipe, todas as novas Branchs serão criadas a partir de develop.

* **feature** - Demais funcionalidades que estão sendo desenvolvidas, os nomes das Branchs que representam novas funcionalidades serão correspondentes ao código das estórias do Kanban. Ex: feature/pt-01

* **bugfix** - Correções de bugs que estão sendo desenvolvidas, os nomes das Branchs que representam correções de problemas serão correspondentes ao código das estórias do Kanban, caso não existam estórias o nome deve condizer a qual problema o código resolverá.
Ex: bugfix/pt-03
Ex: bugfix/correcao-bug-cadastro

Sempre que uma nova branch é criada, deve ser criada a partir de develop, pois o código não deve conter dependências de outras funcionalidades que estejam sendo desenvolvidas. Quando o código é colocado para revisão, apenas o que é pertinente a estória em questão deve ser mergeado.

![alt text](https://www.bitbull.it/blog/git-flow-come-funziona/gitflow-1.png "GitFlow")
__fonte__: https://www.bitbull.it/blog/git-flow-come-funziona/gitflow-1.png


#### Trabalhe na branch correta

Para visualizar todas as branches:
```sh
    git branch -a
```


Utilize uma branch já existente:
```sh
    git checkout <nome_da_branch>
```

Ou crie uma nova para a sua funcionalidade:
```sh
    git checkout -b <nome_da_branch>

    <Exemplo>
    git checkout -b feature/pt-01
```

Certifique-se de que sua branch está atualizada:
```sh
    git pull origin <nome_da_branch_mais_att>

    <Exemplo>
    git pull origin develop
```

### Pull Requests

Sempre que um código está sendo desenvolvido deve-se criar um PR(Pull Request) com o código e nome da estória, descrevendo o que está sendo desenvolvido.

Exemplo: [PT-01] Eu como locador, quero cadastrar minhas salas, de modo que meus locatários consigam obter informações para alugar

O responsável pela tarefa deve abrir o PR e ser responsável pela manutenção dele até que o código seja mergeado.

#### Labels
Labels são rótulos que descrevem o andamento do código no fluxo de trabalho da equipe relacionando Github com o quadro Kanban:

* **Em desenvolvimento** - Label que relaciona a situação do código com a coluna de mesmo nome no Kanban. Códigos com essa Label não podem ser revisados até que o responsável atualize a situação.

* **Code Review** - Label que relaciona a situação do código com a coluna de mesmo nome no Kanban. Códigos com essa Label devem ser revisados por no mínimo 2 membros da equipe que não participaram do desenvolvimento da solução. Se o PR for aprovado **NÃO** realize o merge.

* **Revisão** - Label que relaciona a situação do código com a coluna de mesmo nome no Kanban. Códigos com essa Label devem ser revisados a nível de usuário pelos membros da equipe, portanto, o responsável pela tarefa deve fazer o deploy da solução no ambiente de desenvolvimento. Se a solução for aprovada **NÃO** realize o merge.

*  **Aguardando Deploy** - Label que relaciona a situação do código com a coluna de mesmo nome no Kanban. Códigos com essa Label devem permanecer assim até que a equipe decida realizar o empacotamento de uma nova release. **NÃO** realize o merge.

* **Deploy** - Label que relaciona a situação do código com a coluna de mesmo nome no Kanban. Códigos com essa Label devem ser mergeados em develop para gerar uma nova release.

### Code Review
Para garantir que o código foi revisado, temos uma trava no Github que só permite que um código entre em develop depois que for aprovado por 2 membros da equipe.
Ao revisar o código o desenvolvedor deve se atentar com:

* Se o código está funcional
* Se o código está com uma boa qualidade
* Se segue as convenções de PEP8 (python)
* Se é pythonico, no caso do backend.
* Se as funções estão documentadas (Numpy)

Se todos os requisitos acima estiverem dentro do esperado, o desenvolvedor deve aprovar a solução.

### Tags
Tags deverão ser geradas quando uma nova release está sendo gerada, ou seja quando códigos desenvolvidos pela equipe se tornarão disponíveis para uso em produção.
Após a estória for aprovada para o deploy, criamos releases utilizando o seguinte versionamento semântico:

MAJOR.MINOR.PATCH

* Versão Maior(MAJOR):
Quando fizer mudanças incompatíveis na API.

* Versão Menor(MINOR):
Quando adicionar funcionalidades mantendo compatibilidade.

* Versão de Correção(PATCH):
Quando corrigir falhas mantendo compatibilidade.

Exemplo: Começamos o sistema e desenvolvemos uma funcionalidade de login. TAG: 0.1.0

Exemplo: Corrigimos um bug no envio da senha do login.
TAG: 0.1.1

Exemplo: Mudamos a versão do Django de 1.x para 2.x, portanto o sistema quebrou por compatibilidade de versão.
TAG: 1.1.1

Para ver mais:
https://semver.org/lang/pt-BR/

Trabalhando com tags:

Listando tags:
```sh
    git tag
```

Criando tags:
```sh
     git tag <numero-versao>
```

Detalhando uma tag:
```sh
    git show <numero-versao>
```

Subindo tags para o Github:
```sh
    git push origin --tags
```
