# Fluxo de Trabalho

A equipe optou por utilizar algumas cerimônias ágeis e o quadro Kanban para acompanhar o trabalho, realizando Sprints de 2 semanas.

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



## Github

* **master** - Branch utilizado somente para funcionalidades já testadas e aprovadas pelo cliente
* **develop** - Branch que consiste no desenvolvimento atual da equipe

* **features** - Demais funcionalidades que estão sendo desenvolvidas


![alt text](https://www.bitbull.it/blog/git-flow-come-funziona/gitflow-1.png "GitFlow")
__fonte__: https://www.bitbull.it/blog/git-flow-come-funziona/gitflow-1.png

**SEMPRE**:
* Para novas funcionalidades utilize: feature/nome_da_func
* Para melhorias no codigo: bugfix/nome_da_correcao

---


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
    git checkout -b DBconnection
```

Certifique-se de que sua branch está atualizada:
```sh
    git pull origin <nome_da_branch_mais_att>

    <Exemplo>
    git pull origin develop
```
---

## Rodando o projeto local

#### Adicione suas credenciais
Para trabalhar com o projeto, crie um arquivo chamado .env na raiz do diretorio, e
adicione as credenciais fornecidas pela **equipe de desenvolvimento**.


---
#### Utilizando Docker

Docker é uma tecnologia que fornece containers que isolam processos, com a ajuda do Docker Compose é possível orquestrar containers e subir aplicações complexas com poucos comandos.

Instalação do Docker no Windows: [https://docs.docker.com/docker-for-windows/install/](https://docs.docker.com/docker-for-windows/install/)

Instalação do Docker Compose no Linux: [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)

**Iniciando o projeto**

Atualize o repositorio local
```sh
    git pull origin develop
```
Para iniciar o projeto:

```sh
    docker-compose up
```
