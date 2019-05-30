# Documentação
Todas as documentações de negócio e infraestrutura tendem a ser centralizadas em um único local, para que a equipe saiba exatamente o que se passa com o projeto e que fique registrado nossos passos para o futuro.

## Framework de documentação
O framework utilizado para gerar as documentações é o **mkdocs**, pacote do próprio python que disponibiliza um servidor de documentação pronto para uso.

Para saber mais sobre o mkdocs:
https://www.mkdocs.org/


**Como funciona?**


O mkdocs utiliza arquivos markdown para subir as documentações, ou seja todas as documentações devem ser escritas dentro da pasta *docs* e apontadas no arquivo *mkdocs.yml*

![alt text](https://www.mkdocs.org/img/initial-layout.png "Estrutura Mkdocs")
__fonte__: https://www.mkdocs.org/img/initial-layout.png

## Como escrever documentações?
Para escrever documentações é necessário escrever documentos em Markdown, para saber mais sobre markdown:
 https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet

Não é necessário nada demais para escrever arquivos markdown, assim como HTML, Markdown é uma linguagem de marcação, ou seja basta um editor de texto simples.

Alguns editores de texto tem plugins que possibilitam uma preview do documento, porém, nesse exato momento eu (Lucas Siqueira), estou utilizando o aplicativo mobile Markor.


Depois de escrever, é necessário que estes arquivos estejam dentro da pasta *docs* e que sejam apontados dentro do *nav* no arquivo *mkdocs.yml*, identificando o nome da sessão e o arquivo que será utilizado.

```yaml
   site_name: Site Exemplo
   nav:
      - Home: index.md
      - Sobre: about.md
```

Para testar, instale os requisitos utilizando:
```sh
    $ pip install -r requirements.txt
```

*build* a documentação com:
```sh
   $ cd locapy

   $ mkdocs build
```

E depois subir o servidor:
```sh
    # Estamos subindo o servidor na porta 8001    
    # para que não haja conflitos com o Django

    $ mkdocs serve  --dev-addr=127.0.0.1:8001
```


## Subindo no GitPages
Para que a documentação fique exposta para toda a equipe, estamos utilizando o GitPages do Github para hospedar nosso servidor de documentação, o mkdocs tem integração com o GitPages o que torna tudo mais fácil.

Para realizar o deploy das modificações para o GitPages utilize o comando:

```sh
   mkdocs gh-deploy
```

Feito isso, é só conferir a documentação.
