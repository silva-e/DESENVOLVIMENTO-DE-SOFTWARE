### Git comandos uteis

#### git init

Inicia um repositório local

#### git add . ou git add nome_arquivo

Adicioan os arquivos para área de commit

```
git commit -m 'mensagem do commit'
```

### Origin
- O endereço remoto de ORIGIN é definido quando realizamos um clone do repositório do servidor remoto.

#### git pull

Baixa as modificações de todos os branchs do servidor remoto(origin).
```
git pull
```
### Baixando alterações de um branch específico
Para baixar alterações de um branch específico você deve utilizar o `git pull` da seguinte maneiira:
```
git pull <remote> <branch>
```
Onde na maioria dos casos o <remote> = origin (origem remota url do) o nome do branch em questão. Você pode utilizar o tab que o git ajuda completando o remote e o nome do branch para evitar erros de digitação.


#### git push

Envia todas as modificações de todos os branchs do projeto para o servidor remoto do git.

```
git push 
```
Se você executar o comando `git push` apenas, o Git por padrão irá assumir que o envio do push será para seu repositório remoto e por de baixo dos panos utilizará origin(origem remota) para fazer o push de todos os branchs locais.
 
 
- Enviando uma branch específica para origin(origem remota).
```
$ git push <remote> <branch>
```

Se houver apenas uma branch e ela recebeu o nome de `main`, o comando `git push` vai completar os outros dois parâmetros pré-definidos – executando, efetivamente, `git push origin main`.

#### Branchs

Toda vez que se inicia um projeto com git automáticamente é criando uma branch. Uma branch significa um ramo do projeto. Você pode criar branchs para fazer correções ou adições de novos recursos sem que precise mexer na branch principal. Evitando, desta forma, atrapalhar o que já está funcioando na branch principal e que irá ser a versão final do cliente. O que está na branch principal (ou qualquer nome que você dê a ela) deve ser considerado o que será utilizado em produção.

Toda vez que você está trabalhando em uma branch diferente da branch principal, é interessante que você faça um merge da branch principal para a sua branch atual quando a branch principal receber atualizações de código. Dessa forma ambas as branchs irão andar em conjunto e você irá identificar se o que você está desenvolvendo na sua branch separada está funcionado e compatível com a branch principal. Após enviar o merge da branch principal para sua branch atual e identificar alguma incompatibilidade você poderá fazer as correções para ajustar o que for necessário. Desta forma você saberá antes de fazer um mérge para a branch principal se algo está errado ou pode ter 'quebrado seu código'. 

 **IMPORTANTE: Antes fazer um merge da sua branch atual para branch principal, você deve fazer o inverso. Fazer o merge da branch principal para sua branch atual trazendo todas as modificações que outros desenvolvedores fizeram. Fazer os testes necessários e só então fazer o merge para a branch principal. isso também é conhecido como WORKFLOW DE TRABALHO COM GIT** e visa grarantir erros de conclitos em arquivos e códigos. 
 

#### Criando novas branchs

O comando `git branch nomeDabranch` cria uma nova branch. 

Para você acessar a nova branch você utilizara o comando: `git checkout nomeDabranch`. Desta forma você poderá continuar codificar nessa nova branch. Quando você terminar de adicionar ou corrigir o que precisa, você irá fazer commit normalmente.
 
Posteriormente você precisa fazer o mérge de tudo que está na branch principal para a branch que você está trabalhando. Pode ser que enquanto você trabalhava em algum recurso outro desenvolvedor acrescentou algo no código. Feito o mérge da branch principal para sua branch você poderará fazer o inverso mesclar a branch que você estava trabalhando com a principal após garantir que nada 'quebrou no código' e fazer um push para o servidor remoto disponibilizando as mudanças para que os outros desenvolvedores possam baixar.


#### branch e checkout

O comando checkout além de alterar a branch em que se deseja trabalhar, também permite você andar pelos commits dentro da brach que você está, para verificar algum código que estava funcionando ou foi motivo de algum bug em um determinado momento da linha do tempo da branch, por exemplo:

O comando:
 ```
 git ckeckout + o códigoDoCommit
 ```
 
O código do commit pode ser encontrado digitando `git log`.

O comando git log permite ver a linha do tempo de commits do mais recente para o mais antigo. Para cada commit feito é gerado um hash único que indentifica o ponto do projeto naquele momento.

Após navegar pelos commits você pode voltar para o último commit que aponta para HEAD. Para fazer isso faça um checkout:
 
 ```
 git checkout nomeDaBranch
 ```
 Fazendo isto você volta para o último commit que aponta para HEAD e pode continuar trabalhando.
 
 ### Git reset. Ideal para voltar o projeto em determinada linha do tempo dispensando ou não alterações a partir de um determinado commit ou corrigir um mérge feito para uma branch errada.
 
 O comando git reset redefini o HEAD para a condição espeficicada. Pode receber três argumentos que vão determinar a profudidade de execução do comando.
 
 --soft
Não toca no arquivo de índice ou na árvore de trabalho (mas redefine o cabeçalho para <commit>, assim como todos os modos fazem). Isso deixa todos os seus arquivos alterados como "Changes to be committe" (Alterações onde serão realizados os commits), como o git status colocaria. Ideal se você já fez algum código que não gostaria de perder. Neste caso você faria ajustes para incluir esses códigos no próximo commit

--mixed
Redefine o índice, mas não a árvore de trabalho (ou seja, os arquivos alterados são preservados, mas não marcados para um commit) e relata o que não foi atualizado. Esta é a ação predefinida.

--hard
Redefine o índice e a árvore de trabalho. Quaisquer alterações nos arquivos rastreados na árvore de trabalho desde <commit> serão descartados.
 
 ### Voltar na linha do tempo de uma branch
 
 As vezes precisamos voltar o código de um branch para uma determinada linha do tempo e dispensar todos os commits feitos após aquele ponto. 
 
 - Primeiro passo é executar um git log para listar os commits com seus hash.
 ```
 git log 
 ```
 - Identificado o código do commit você executará o seguinte comando:
 
 ```
 git reset (--soft, --mixed ou --hard) codigoCommit
 ```
 Na dúvida utilizar --soft
 
 #### Desfazendo mérge errado.
 
 As vezes você fez um merge de uma branch que ainda estava em desenvolvimento para sua branch principal e precisará reverter a branch principal antes que vá para o servidor de produção. Você terá as seguintes alternatívas:
 
 - Se você acabou de fazer o mérge, o último commit está apontando para o mérge realizado bem como sua mensagem. Neste caso basta executar o comando:
 
 ```
 git reset --hard HEAD~1
 ```
 Isso faz o reset para o commit imediatamente anterior ao mérge feito e descartará tudo que está a frente deste commit.
 
 - Se já foram feitos outros commits no projeto você precisára identificar o momento do merge com o git log para anotar o hash do commit:
  ```
 git log 
 ```
 Feito isto você executará o comando:
 ```
 git reset --hard codigo_do_commit
```
 Iss faz o reset para o commit especificado e descartará todas as alterações feitas daquele ponto para frente.
 
#### Enviando uma branch para o servidor remoto
 
Quando uma branch é criada localmente e outros desenvolvedores ou até mesmo você irá dar continuidade nela a partir de outro computador, você precisa enviar ela para o servidor remoto para que todos possam ter acesso. Para enviar uma branch local para o servidor remoto você deve fazer o seguinte comando:

``` 
git push <remote> <branch>
```
Isto irá criar a branch no servidor remoto.

 Outro exemplo:
```
 git push origin nova-feature
```

#### Baixando uma branch remota para o projeto caso ela não exista no computador

- Para listar as branchs disponíveis no servidor digite o seguinte comando:
 ```
 git branch -r
 ```

- Encontrando a branch que deseja baixar você poderá executar o seguinte comando: 
 ```
 git checkout -b nome-da-minhabranchlocal origin/nome-da-branch-remota
 ```
É ideal baixar uma branch que não exita no seu computador utilizando o mesmo nome da branch remota para manter a coesão.
 
- Após isto você poderá relizar o comando `git branch` para listar todas as branchs locais. E fazer o checkout para a branch que acabou de trazer do servidor remoto (ORIGIN)

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

