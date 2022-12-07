### Lista de softwares utilitários para Linux

#### Encontrando pastas que estão utilizando muito espaço no sistema operacional.
1 -  ncdu - Utilize o utilário para fazer a listagem a partir de diretórios de sua escolha. É necessário instalação.

#### Monitoramento de processos
1 - HTOP - É necessário instalar. Ferramenta que permite verificar todos os processos contando com filtros de busca entre outras ferramentas.
2 - BASHTOP - É necessário instalar. Ferramenta que permite monitorar CPU, RAM, DISCO entre outros recursos.

### Monitoramento de querys SQL
1 - mytop - É necessária a instalação. Monitora querys sql no banco de dados em tempo real. Ideal para profile das consultas e encontrar gargalos.

### PIPE VIEWER (PV)
1 - Cria barra de progressos para atividades em cli que não tenha um verbose. É baseado em pipeline. Pode ser utilizado por exemplo com mysqldump ou mysql para acompanhar as operações e exportação ou importação de banco de dados. Para instalar utilize apt install pv.

Exemplo:
```
  mysqldump -u usuario -p nomeBanco | pv | > backup.sql
```
Para uma barra de progresso coerente você pode utilizar o paramentro -s e informar o valor em MB (m) ou Gigas(g);

```
  mysqldump -u usuario -p nomeBanco | pv -s 1024m | > backup.sql
```
Consulte o **man pv** no terminal para ter acesso a todas as opções de saída.
