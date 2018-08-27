# Intalação - MySQL no Ubuntu 18.04 LTS
## Por que fazer um tutorial sobre isso?
Na data do post não havia tutorial dessa versão em português na internet. Basicamente eu tive problemas de configuração do MySQL nessa versão.
Na versão anterior existia uma espécie de Wizard na configuração durante a instalação, nessa última versão do Ubuntu não.

## Por onde começar?
Comece abrindo o terminal com Ctrl + Alt + T. Feito isso digite os seguintes comandos:
>sudo apt update

>sudo apt install mysql-server

>sudo mysql_secure_installation

É disso que você precisa para tê-lo instalado na máquina. Mas isso não é tudo. Não conseguirá acessa-lo por não ter usuário e senha não configurados.

## Configurando usuário e senha

É relativamente simple, digite no terminal:

>sudo mysql

Depois:

>SELECT user,authentication_string,plugin,host FROM mysql.user;

O usuário root deve estar sem a authentication string. Então para resolver isso faça:

>ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'SUASENHAAQUI-EEHPRASUBSITUIR';

Para que as alterações entrem em efeito é preciso dar um flush com o comando abaixo:

>FLUSH PRIVILEGES;

Verifique se agora o usuário está com authentication_string está preenchida:

>SELECT user,authentication_string,plugin,host FROM mysql.user;

Se estiver então saia do MySQL:

>exit

Pronto, agora você conseguirá acessar com o MySQL workbench ou PHPMyAdmin ou o cliente se sua preferencia.

>Atenção! Se você já tiver configurado com senha precisará executar o MySQL com o comando abaixo:
>mysql -u root -p
