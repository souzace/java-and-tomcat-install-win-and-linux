# Instalando Java no Windows 10 em 4 passos

Fala galera, blz? Hoje vou falar de uma coisa simples e básica, mas que no começo pode deixar muitos iniciantes com dúvidas: como instalar e configurar o Java em ambiente Windows. Para esse tutorial estarei usando o Windows 10 e Java em sua última versão (version 8 Update 121).

Antes de começar quero tirar uma dúvida sobre a diferença entre JRE e JDK.

**JRE (Java Runtime Environment)**

É utilizado para executar aplicações na plataforma Java. Composto pelas bibliotecas (APIs) e pela máquina virtual (JVM). O Java Runtime Environment não contém qualquer ferramenta para o desenvolvimento de aplicações, ou seja, você não vai conseguir compilar código fonte Java apenas com ele.

**JDK (Java Development Kit)**

É o pacote que contém toda a infraestrutura necessária para o desenvolvimento de aplicações Java. Ao ser instalado, o JRE é instalado automaticamente. As ferramentas incluem: compilador (javac.exe), depurador e outros utilitários.

Pronto, agora que sabemos disso, podemos seguir o passo a passo com a instalação e configuração do Java.

## Passo 1

**Download do Java JDK**

Acesse o link: [hhttp://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html?ssSourceSiteId=otnpt](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html?ssSourceSiteId=otnpt).
Aceite os termos de licença, escolha a versão *jdk-8u121-windows-x64.exe*, para sistemas de 64 bits, caso seu Windows seja de 32 bits escolha *jdk-8u121-windows-i586.exe*. Faça o download normalmente.

## Passo 2

**Instalando o Java**

Para instalar o JDK no Windows, basta executar o programa de instalação e clicar no botão Next em todas as telas apresentadas. O processo é simples e rápido.

## Passo 3

**Configurar variáveis de ambiente**

Essa é a parte inicial mais complicada do processo, mas vocês verão que não é nenhum bicho de sete cabeças. Para começar pressione _Windows + S_ para abrir a busca do Windows e digite "variáveis de ambiente". Clique em Enter.

Vá na opção *Variáveis de ambiente*. Aqui é preciso dizer para o computado qual o caminho de instalação do Java.

Aqui, no label Variáveis do sistema clique no botão Novo. No pop up que aparecer, no campo Nome da variável digite:
```JAVA_HOME```

No valor da variável digite o caminho em que o Java foi instalado em sua máquina. Exemplo:
```C:\Program Files\Java\jdk1.8.0_121```

Com isso o Java já será reconhecido pelo seu sistema, porém ainda não poderá ser compilado,pois ainda precisamos realizar um segundo passo que é editar o Path, que é o caminho para executar os comandos através do prompt.

Clique em Path, em Variáveis do sistema, e clique no botão Editar. No final do campo Valor da variável, digite:
```;%JAVA_HOME%\bin```

Clique em OK e pronto.  

## Passo 4

**Testando tudo**

Abra o cmd (prompt de comando do Windows) através do campo de busca do lado esquerdo ou pressionando em _Windows + S_ e digite cmg e aperte Enter.
Digite:
``` java -version```

E você vera a versão do Java seguido de outras informações.
Após isso digite:
```javac -version```

Caso tudo todas as variáveis de ambiente tenham sido configuradas corretamente será mostrada a versão do compilador na tela.

Caso mostre que esse comando não foi reconhecido, refaça o tutorial com mais detalhe e verifique o que foi feito.

É isso pessoal. Espero que tenham gostado, um tutorial simples, porém bastante necessário. Forte abraço!
