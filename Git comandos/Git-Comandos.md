### Git comandos uteis

#### git init

Inicia um repositório local

#### git add . ou git add nome_arquivo

Adicioan os arquivos para área de commit

git commit -m 'mensagem do commit'

#### git pull

Baixa as modificações do projeto do servidor remoto

#### git push

Envia todas as modificações para o servidor remoto do git

Se você executar o comando `git push`, o Git por padrão escolherá dois parâmetros a mais para você: o **repositório remoto** para realizar o push e a **branch** do push.

A forma genérica do comando é esta:

```
$ git push <remote> <branch>
```

Por padrão, o Git escolhe a `origin` como repositório remoto e sua *branch atual* como a branch para o push.

Se a sua branch atual é a `main`, o comando `git push` vai completar os outros dois parâmetros pré-definidos – executando, efetivamente, `git push origin main`.



#### Branchs

Toda vez que se inicia um projeto com git automáticamente é criando uma branch. Uma branch significa um ramo do projeto. Você pode criar branchs para fazer correções ou adições de novos recursos sem que precise mexer na branch principal. Evitando desta forma de atrapalhar o que já está funcioando

Toda vez que se cria uma branch é interessante que você faça um merge com a branch principal para sempre se manter sincronizado com o que outras pessoas adicionaram. Desta forma você saberá antes de fazer um mérge para a branch principal se algo está errado ou pode ter quebrado seu código.

#### branch e checkout

O comando checkout tem duas funcões principais em uma branch. Ele permite você andar pelos commits para verificar algum código que estava funcionanando em um determinado momento da linha do tempo do git, por exemplo.

O comando fica git ckeckout + o código do commit. Este código pode ser encontrado digitando git log.

O comando git log permite ver a linha do tempo de commits. Para cada commit feito é gerado um hash única que indentifica o ponto do projeto naquele momento.



#### Criando novas branchs

O comando git branch nomeDabranch cria uma nova branch. 

Para você acessar a nova branch você utilizara o comando: git checktou nomeDabranch. Desta forma você poderá continuar codificar nessa nova branch. Quando você terminar de adicionar ou corrigir o que precisa você irá fazer commit normalmente. 

Posteriormente você precisa fazer o mérge de tudo que está na branch principal para a branch que você estava trabalhando. Pode ser que enquanto você trabalhava em algum recurso outro desenvolvedor acrescentou algo no código. Feito o mérge da branch principal para sua branch você poderará fazer o inverso mescar a branch que você estava trabalhando com a principal e fazer um push para o servidor remoto disponibilizando as mudanças para que os outros desenvolvedores possam baixar

#### Enviando uma branch para o servidor remoto



Para enviar uma branch local para o servidor remoto você deve fazer

```
 git push <remote> <branch>
```

Exemplo git push origin novoBotao

Isto irá criar a branch no servidor remoto

*git push origin nova-feature*

#### Baixando uma branch remota para o projeto

- Para listar as branchs disponíveis no servidor digite o seguinte comando git branch -r

- Encontrando a branch que deseja baixar você poderá executar o seguinte comando git checkout -b nome-da-minhabranchlocal origin/nome-da-branch-remota

- Após isto você poderá relizar o comando git branch para listar todas as branchs locais. 

-  Outro comando que permite baixar branch remotas são

- *git checkout –track origin/nova-feature*

#### Deletando branch locais

Há duas formas de fazer o delete da branch locais. Ideal para realizar após fazer a integrações com a branch principal e ter certeza que tudo está funcionando

- git branch -d nomeDaBranch

- git branch -D nomeDaBranch . Está segunda opções força a deleção.

#### Deletando branch remota

git push origin --delete nomeDaBranch



#### Verificando quem alterou linha a linha do arquivo

```bash
git blame nome-do-arquivo
```

#### Adicinoando repositório remoto ao projeto local

Se você já criou seu repositório no servidor remoto você pode adicionar ele a um projeto local com o seguinte comando

```
git remote add origin urldoseuprojeto
``` 

#### Removendo respositório remoto

