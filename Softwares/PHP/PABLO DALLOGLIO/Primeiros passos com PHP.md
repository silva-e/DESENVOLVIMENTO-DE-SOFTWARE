### Primeiros passos com PHP

#### Configurando o php.ini

O php.ini é o arquivo de configurações global de todo comportamento da linguagem. Suas principais váriaveis de configuração são:

1. error_log: indica o caminho do log. Exemplo: /tmp/apache2/error.log

2. memory_limit = 256M é a quantidade de memória que um script php pode consumir durante o seu tempo de execução.

3. max_execution_time = 120 é o tempo máximo que uma requisição a um script php irá durar. Caso o script não tenha finalizado está requisição em geral é abortada gerando uma saída nos logs.

4. file_uploads = on|off quando on permite o envio de arquivos para o servidor. Quando off não permite.

5. post_max_size = 100M tamanho máximo de dados por requisição

6. upload_max_filesize = 100M Tamanho máiximo de upload do arquivo. Obs: É importante que post_max_size e upload_max_filesize andem juntas para a correta troca de informações.

7. session.gc_maxlifetime =14000 tempo máximo de vida de uma sessão

8. display_error = On|off Quando ligado exibe os error em tela sendo recomendado apenas em em ambiente de desenvolvimento. Ao colocar seu projeto em produção mantenha ele desligado para não gerar uma má impressão nos seus usuários.

9. error_reporting = E_ALL Diretiva informa qual o level (tipos warnings, faltal etc) dos error serão exibidos.

Para conferir como esta todas as configurações execute a funcão phpinfo(); dentro de um arquivo ponto php.

```
<?php

 phpinfo();
```

### Níveis de erros do php

1. Notice: São erros ou recomendações de que algo está inconsistente no seu código. Não interrompe a execução do programa. É bom sanar todos os tipos de erros inclusives os do tipos notice

2. Warning: São erros mais expressivos porém não interrompe a execução do código. 

3. Fatal error: O código é interrompido. Necessita de correção

4. Parse error: Código de erro de codificação. Geralmente sintaxe errada. O verificador de sintaxe do php não conseguiu analisar o código como um código válido

# 
