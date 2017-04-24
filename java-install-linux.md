# Tutorial para instalação do Java JDK 1.7 no Linux

## 1º - Faça o download do JDK 1.7 nesse link:

**Versão: 1.7**

[(64 ou 32) bits (Requer login) Oracle](http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase7-521261.html#jdk-7u80-oth-JPR) <br>
ou <br>
[(64 bits) (download direto) Dropbox](https://www.dropbox.com/s/2cs9k4cfhag5gm0/jdk-7u80-linux-x64.tar.gz?dl=0)  <br>

[(32 bits) (download direto) Dropbox](https://www.dropbox.com/s/qryvdq8uwfh8idq/jdk-7u80-linux-i586.tar.gz?dl=0) <br>

**Versão: 1.8**

[(última versão) Clique em Accept License Agreement (Aceitar o acordo da Licença) para liberar o download](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)<br>
  
* Se seu sistema operacional for de 64 bits<br>
escolha o pacote jdk-7u80-linux-x64.tar.gz<br>

* caso seja 32 bits <br>
escolha jdk-7u80-linux-i586.tar.gz<br>

## 2º - Instalação do Java JDK

Vá até a pasta aonde você baixou o pacote .tar.gz e execute os comandos abaixo:

* Descompacte a pasta do binário do jdk<br>
```[user@host /home/user/Downloads]$ tar -xvzf jdk-7u80-linux-x64.tar.gz```

* Crie a pasta para a instalação do java necessário (root)<br>
```[user@host /home/user/Downloads]$ sudo mkdir /usr/java```

* Mova a pasta do java para o local da instalação<br>
```[user@host /home/user/Downloads]$ sudo mv -v jdk1.7.0_80 /usr/java```

## 3º Configurações Globais de Ambiente

**-- obrigatório --**
* Crie os arquivos de script (caso não haja)

```[user@host /home/user/Downloads]$ sudo touch /usr/bin/java```<br>
```[user@host /home/user/Downloads]$ sudo touch /usr/bin/javac```<br>
```[user@host /home/user/Downloads]$ sudo touch /usr/bin/jar```<br>
----opcional-----<br>
```[user@host /home/user/Downloads]$ sudo touch /usr/bin/javaws```<br>

* ### java
```[user@host /home/user/Downloads]$ sudo alternatives --install /usr/bin/java java /usr/java/jdk1.7.0_80/jre/bin/java 200000```


* ### javac
```[user@host /home/user/Downloads]$ sudo alternatives --install /usr/bin/javac javac /usr/java/jdk1.7.0_80/jre/bin/javac 200000```


* ### jar
```[user@host /home/user/Downloads]$ sudo alternatives --install /usr/bin/jar jar /usr/java/jdk1.7.0_80/jre/bin/jar 200000```

-- opcional --

* ### javaws
```[user@host /home/user/Downloads]$ sudo alternatives --install /usr/bin/javaws javaws /usr/java/jdk1.7.0_80/jre/bin/javaws 200000```

* ### Plugin Browser (Mozilla Firefox) 32-bits
```[user@host /home/user/Downloads]$ sudo alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so libjavaplugin.so /usr/java/jdk1.7.0_80/jre/lib/i386/libnpjp2.so 200000```

* ### Plugin Browser (Mozilla Firefox) 64-bits
```[user@host /home/user/Downloads]$ sudo alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so libjavaplugin.so.x86_64 /usr/java/jdk1.7.0_80/jre/lib/amd64/libnpjp2.so 200000```


## 4º Definindo a versão do java a ser utilizada (em caso de mais de uma versão instalada)

```[user@host /home/user/Downloads]$ sudo alternatives --config java```

* As informações do menu de configuração vão variar em cada caso, selecione com a tecla + a linha que contenha o caminho para jdk1.7.0_80:

There are 4 programs which provide 'java'.<br>

  Selection    Command<br>
-----------------------------------------------<br>
\*+ 1         /usr/lib/jvm/jre-1.6.0-openjdk/bin/java<br>
    2         /usr/java/jdk1.7.0_55/jre/bin/java<br>
    3         /usr/java/jdk1.7.0_80/jre/bin/java<br>

Enter to keep the current selection[+], or type selection number: 3<br>

* Repita o passo anterior para com os seguintes comandos:

**-- obrigatório --**

```[user@host /home/user/Downloads]$ sudo alternatives --config javac```<br>
```[user@host /home/user/Downloads]$ sudo alternatives --config jar```<br>

**--opcional --**

```[user@host /home/user/Downloads]$ sudo alternatives --config javaws```<br>
```[user@host /home/user/Downloads]$ sudo alternatives --config libjavaplugin.so (caso 32 bits)```<br>
```[user@host /home/user/Downloads]$ sudo alternatives --config libjavaplugin.so.x86_64 (caso 64 bits)```<br>

## 5º Testando a versão escolhida

* Digite o comando abaixo e veja se a saída estar de acordo com a versão definida no passo anterior:<br>

```[user@host /home/user/Downloads]$ java -version```

* Verifique se a saída é semelhante a esta:
```java version "1.7.0_80"```<br>

```[user@host /home/user/Downloads]$ javac -version```<br>

```[user@host /home/user/Downloads]$ jar -version```<br>

## 6º Definição da Variável JAVA_HOME 

* Caso você deseje que a variável esteja definida apenas para a sessão atual (ao reiniciar será perdido) digite:

```[user@host /home/user/Downloads]$ JAVA_HOME=/usr/java/jdk1.7.0_80```<br>
```[user@host /home/user/Downloads]$ export JAVA_HOME```<br>
```[user@host /home/user/Downloads]$ PATH=$JAVA_HOME=/bin:$PATH```<br>
```[user@host /home/user/Downloads]$ export PATH```<br>

* Caso você deseje que a configuração carregue para o usuário sempre que iniciar o sistema vá para a pasta home do usuário

```[user@host /home/user/Downloads]$ cd ~/```

* Usando um editor de texto, edite o arquivo .bash_profile (oculto), use o vim ou um editor de sua preferência 

```[user@host /home/user]$ vim .bash_profile```

* Insira abaixo dessa linha (User specific environment and startup programs) a seguinte especificação:

```JAVA_HOME=/usr/java/jdk1.7.0_80```<br>
```export JAVA_HOME```<br>

* Modifique a linha do PATH de 
```PATH=$PATH:$HOME/.local/bin:$HOME/bin```<br>
para <br>
```PATH=$JAVA_HOME/bin:$PATH:$HOME/.local/bin:$HOME/bin```<br>

* Salve as alterações e feche o arquivo .bash_profile, recarrege as alteraçõesdo bash_profile

```[user@host /home/user]$ source .bash_profile```<br>

* Caso queira que todos os usuários carregem as mesma especificações, faça as alterações no /etc/profile (root)

Fontes:<br>

David Ghedini - http://www.davidghedini.com/pg/entry/install_tomcat_7_on_centos<br>

JR - https://www.if-not-true-then-false.com/2014/install-oracle-java-8-on-fedora-centos-rhel/<br>
