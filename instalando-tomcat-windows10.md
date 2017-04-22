# Instalando Tomcat no Windows 10

Hoje vou ensinar para vocês mais um tutorial simples, porém bastante necessário que é a instalação do Tomcat no Windows 10.

Antes de tudo, certifique-se que já tenha instalado e configurado o Java em sua máquina.


**O que é Tomcat?**

Em resumo, Tomcat é um _servidor de aplicações web_ desenvolvido pela _Apache Software Fondation_, sendo mais especificamente um _container de servlet_, onde container pode ser entendido como um repositório para componentes de negócio.

Agora que já sabemos o motivo que precisamos dele, sigam os passo a passo para deixar tudo 100% na máquina.

## Passo 1

Acesse a página oficial de download do [Tomcat](http://tomcat.apache.org/download-90.cgi) e baixe o instalador .exe
* 32-bit/64-bit Windows Service Installer

## Passo 2

Após o download, vá clicando em Next normalmente. Na tela de "Tomcar basic configuration", na opção de "Tomcat Administrator Login" é opcional colocar um login e senha enquanto as demais opções não precisam ser modificadas.

## Passo 3

Na próxima tela certifique-se que o Tomcat esteja apontando corretamente para o **JRE** instalado em sua máquina.

## Passo 4

Não é necessário mudar o caminho que o Tomcat sugeriu, no meu caso foi:
```C:\Program Files\Apache Software Foundation\Tomcat 9.0```, porém há um padrão adotado de renomear e instalar nesse caminho, por exemplo: ```C:\Tomcat```, mas não há necessidade, apenas para facilitar. E continue com a instalação.

## Passo 5

Após concluir o processo, escolha rodar o apache, nesse momento um ícone próximo ao canto inferior direito aparecerá e o verde significa que o serviço está ativo e rodando. Com o serviço rodando basta digitar em seu navegador ```http://localhost:8080``` e pronto, o Tomcat já está devidamente instalado em sua máquina. Simples não?

### Nota

**Outras configurações**

Caso queira parar o processo do Tomcat ou escolher o tipo de inicialização clique com o botão direito no ícone que surgiu e clique na opção **Configure...**. Aqui você pode fazer diversas coisas além das citadas, como mudar o caminho padrão do Tomcat (não recomendo).

### Nota 2

**Instalação manual**

Vale lembrar também que a instalação do .exe já configura automaticamente as variáveis de ambiente. Caso queira instalar manualmente (baixando o .zip) é necessário colocar o Tomcat em C:\ (para facilitar), configurar a variável de ambiente **CATALINA_BASE** e apontar para o local do Tomcat da mesma forma como foi feita na instalação do Java. E também criar uma outra variável chamada **CLASSPATH** e apontar o caminho da lib servlet, por exemplo: ```C:\tomcat\common\lib\servlet-api.jar;```
E após tudo isso abrir prompt de comando, ir até o diretório ```C:\tomcat\bin``` e digitar ```startup.bat``` para iniciar o Tomcat e acessar pelo ```http://localhost:8080```. Bem mais trabalhoso não é mesmo?


É isso pessoal, a não ser que tenha um motivo maior, escolha a instalação automática quando se está em ambiente Windows. Um grande abraço!