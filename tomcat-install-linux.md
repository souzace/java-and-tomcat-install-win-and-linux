Instalação Tomcat linux

1º Faça o Download do binário do Tomcat
Usaremos a versão 5.5.36 como descrito no link:

https://archive.apache.org/dist/tomcat/tomcat-5/v5.5.36/bin/apache-tomcat-5.5.36.tar.gz (Linux)

* Após realizar o download Descompacte o arquivo apache-tomcat-5.5.36.tar.gz

[user@host /home/user/Downloads]$ tar -xvzf apache-tomcat-5.5.36.tar.gz

2º Instalação e Configuração do Tomcat como um Serviço

* Mova a pasta criada apache-tomcat-5.5.36 para dentro da pasta /usr/share (root)

[user@host /home/user/Downloads]$ sudo mv -v apache-tomcat-5.5.36 /usr/share

* Crie um arquivo na pasta /etc/init.d (script para o serviço do tomcat)

[user@host /home/user/Downloads]$ sudo touch /etc/init.d/tomcat

* Edite o arquivo tomcat com o editor de sua preferencia, usaremos o vim para este exemplo

[user@host /home/user/Downloads]$ sudo vim /etc/init.d/tomcat

* O script a seguir, contém instruções para iniciar, reinicializar ou desligar o serviço do tomcat, de acordo como o comando for chamado, adicione as instruções ao arquivo tomcat da pasta etc/init.d:

#!/bin/bash
# description: Tomcat Start Stop Restart
# processname: tomcat
# chkconfig: 234 20 80
JAVA_HOME=/usr/java/jdk1.7.0_05
export JAVA_HOME
PATH=$JAVA_HOME/bin:$PATH
export PATH
CATALINA_HOME=/usr/share/apache-tomcat-7.0.29

case $1 in
start)
sh $CATALINA_HOME/bin/startup.sh
;; 
stop)   
sh $CATALINA_HOME/bin/shutdown.sh
;; 
restart)
sh $CATALINA_HOME/bin/shutdown.sh
sh $CATALINA_HOME/bin/startup.sh
;; 
esac    
exit 0

* Salve e feche o arquivo


