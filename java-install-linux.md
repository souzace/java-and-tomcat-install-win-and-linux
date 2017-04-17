# Tutorial para instalação do Java JDK 1.7

## 1º - Faça o download do JDK 1.7 nesse link:

**Versão: 1.7**

http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase7-521261.html#jdk-7u80-oth-JPR (Requer login) (64 ou 32) bits
ou
https://www.dropbox.com/s/2cs9k4cfhag5gm0/jdk-7u80-linux-x64.tar.gz?dl=0 (download direto) (64 bits)

https://www.dropbox.com/s/qryvdq8uwfh8idq/jdk-7u80-linux-i586.tar.gz?dl=0 (download direto) (32 bits)

**Versão: 1.8**

http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html (última versão)

* Clique em Accept License Agreement (Aceitar o acordo da Licensa) para liberar o download.
  
* Se seu sistema operacional for de 64 bits
escolha o pacote jdk-7u80-linux-x64.tar.gz

* caso seja 32 bits 
escolha jdk-7u80-linux-i586.tar.gz

## 2º - Instalação do Java JDK

Vá até a pasta aonde você baixou o pacote .tar.gz e execute os comandos abaixo:

* Descompacte a pasta do binário do jdk
```[root@host /home/user/Downloads]$ tar -xvzf jdk-7u80-linux-x64.tar.gz```

* Crie a pasta para a instalação do java necessário (root)
```[user@host /home/user/Downloads]$ sudo mkdir /usr/java```

* Mova a pasta do java para o local da instalação
```[user@host /home/user/Downloads]$ sudo mv -v jdk1.7.0_80 /usr/java```

## 3º Configurações Globais de Ambiente

**-- obrigatório --**

* ### java
```[user@host /home/user/Downloads]$ alternatives --install /usr/bin/java java /usr/java/jdk1.7.0_80/jre/bin/java 200000```


* ### javac
```[user@host /home/user/Downloads]$ alternatives --install /usr/bin/javac javac /usr/java/jdk1.7.0_80/jre/bin/javac 200000```


* ### jar
```[user@host /home/user/Downloads]$ alternatives --install /usr/bin/jar jar /usr/java/jdk1.7.0_80/jre/bin/jar 200000```

-- opcional --

* ### javaws
```[user@host /home/user/Downloads]$ alternatives --install /usr/bin/javaws javaws /usr/java/jdk1.7.0_80/jre/bin/javaws 200000```

* ### Plugin Browser (Mozilla Firefox) 32-bits
```[user@host /home/user/Downloads]$ alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so libjavaplugin.so /usr/java/jdk1.7.0_80/jre/lib/i386/libnpjp2.so 200000```

* ### Plugin Browser (Mozilla Firefox) 64-bits
```[user@host /home/user/Downloads]$ alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so libjavaplugin.so.x86_64 /usr/java/jdk1.7.0_80/jre/lib/amd64/libnpjp2.so 200000```


## 4º Definindo a versão do java a ser utilizada (em caso de mais de uma versão instalada)

```[user@host /home/user/Downloads]$ alternatives --config java```

* As informações do menu de configuração vão variar em cada caso, selecione com a tecla + a linha que contenha o caminho para jdk1.7.0_80:

There are 4 programs which provide 'java'.

  Selection    Command
-----------------------------------------------
*+ 1         /usr/lib/jvm/jre-1.6.0-openjdk/bin/java
   2         /usr/java/jdk1.7.0_55/jre/bin/java
   3         /usr/java/jdk1.7.0_80/jre/bin/java

Enter to keep the current selection[+], or type selection number: 3

* Repita o passo anterior para com os seguintes comandos:

**-- obrigatório --**
```[user@host /home/user/Downloads]$ alternatives --config javac```
```[user@host /home/user/Downloads]$ alternatives --config jar```

**--opcional --**
```[user@host /home/user/Downloads]$ alternatives --config javaws```
```[user@host /home/user/Downloads]$ alternatives --config libjavaplugin.so (caso 32 bits)```
```[user@host /home/user/Downloads]$ alternatives --config libjavaplugin.so.x86_64 (caso 64 bits)```

## 5º Testando a versão escolhida

* Digite o comando abaixo e veja se a saída estar de acordo com a versão definida no passo anterior:

```[user@host /home/user/Downloads]$ java -version```

* Verifique se a saída é semelhante a esta:
```java version "1.7.0_80"```

```[user@host /home/user/Downloads]$ javac -version```
```[user@host /home/user/Downloads]$ jar -version```

## 6º Definição da Variável JAVA_HOME 

* Caso você deseje que a variável esteja definida apenas para a sessão atual (ao reiniciar será perdido) digite:

```[user@host /home/user/Downloads]$ JAVA_HOME=/usr/java/jdk1.7.0_80```
```[user@host /home/user/Downloads]$ export JAVA_HOME```
```[user@host /home/user/Downloads]$ PATH=$JAVA_HOME=/bin:$PATH```
```[user@host /home/user/Downloads]$ export PATH```

* Caso você deseje que a configuração carregue para o usuário sempre que iniciar o sistema vá para a pasta home do usuário

```[user@host /home/user/Downloads]$ cd ~/```

* Usando um editor de texto, edite o arquivo .bash_profile (oculto), use o vim ou um editor de sua preferência 

```[user@host /home/user]$ vim .bash_profile```

* Insira abaixo dessa linha (User specific environment and startup programs) a seguinte especificação:

```JAVA_HOME=/usr/java/jdk1.7.0_80```
```export JAVA_HOME```

* Modifique a linha do PATH de ```PATH=$PATH:$HOME/.local/bin:$HOME/bin``` para ```PATH=$JAVA_HOME/bin:$PATH:$HOME/.local/bin:$HOME/bin```

* Salve as alterações e feche o arquivo .bash_profile, recarrege as alteraçõesdo bash_profile

```[user@host /home/user]$ source .bash_profile```

* Caso queira que todos os usuários carregem as mesma especificações, faça as alterações no /etc/profile (root)

Fontes:
David Ghedini - http://www.davidghedini.com/pg/entry/install_tomcat_7_on_centos
JR - https://www.if-not-true-then-false.com/2014/install-oracle-java-8-on-fedora-centos-rhel/
