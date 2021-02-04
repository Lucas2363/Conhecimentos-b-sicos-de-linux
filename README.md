# Conhecimentos-b-sicos-de-linux

## Objetivo

Este repositório tem como objetivo demonstrar os conhecimentos básciso adquiridos na escola SENAI de informática, por meio de um projeto apresentado pelos mesmos, onde foi configurado do zero um sistema de uma empresa no linux com as seguintes caracteristicas:

* Ip estático para acesso a internet;
* Criação de grupos e úsuarios da empresa ficticia;
* Criação de pastas para cada grupo e úsuarios dentro de uma pasta central;
* Mudar a permissão dos úsuarios e grupos para cada pasta apresentada aos mesmos;
* Habilitar o acesso via SSH somente para o grupo do TI.

Segue abaixo uma representação do projeto:

![Alt Text](https://ibb.co/QPm9fsB)https://ibb.co/QPm9fsB

## Comando utilizados

* cd - Acessa e muda o diretório recorrente;
* mkdir - Cria uma pasta;
* adduser - Adiciona um usuário;
* addgroup - Adiciona um grupo ao Linux;
* adduser [usuario] [grupo] - Adiciona um usuário a um grupo;
* chown - Troca o usuário dono da pasta/arquivo;
* chgrp - Troca o grupo dono da pasta/arquivo;
* chmod - Troca as permissões	de pasta/arquivo;
* vim - editor de texto.
* ip add

## Instalações necessárias 

* Tree - Lista o contéudo de um diretório usando um formato de árvore;
* Openssh-server - Instala o SSH no linux

## Configuração do ip

Para configurar um ip estático precisamos entrar no arquivo que contém as configurações das Interfaces de Rede que fica em "/etc/network/interfaces"  após entrar no arquivo 
devemos edita-lo com um editor de texto de preferencia o nano ou o vim, após isso foi acrescentado as seguintes informações:

* auto enp0s8
* iface enp0s8 inet static
* address 172.16.0.10/255.255.255.0

Após isso foi utilizado o comando ip add para checar se o ip estava ativo, conforme a imagem a seguir: 

![Alt Text](https://i.ibb.co/3yV3PFW/PRINT-1.png)

## Grupos e úsuarios 

Com o ip configurado foi feita a criação dos grupos e úsuarios da empresa ficticia usando os comandos adduser e addgroup conforme a imagem abaixo: 

![Alt Text](https://i.ibb.co/mB8MW9Z/PRINT-3.png)

Feita a criação dos úsuarios e grupos foi criado uma sessão de pastas para cada setor da empresa com seus respectivos grupos e úsuarios, usando o comando tree temos as seguintes pastas: 

![Alt Text](https://i.ibb.co/5FBCCRZ/PRINT-4.png)

Após isso cada pasta foi desginada ao seus respectivos grupos e úsuarios usando os comandos chown e chgrp conforme a imagem a seguir: 

![Alt Text](https://i.ibb.co/bsDnCx9/PRINT-5-1.png)


## Serviço de SSH 

Para instalar o serviço de ssh precisamos passar o comando apt install Openssh-server, após isso usamos o comando systemctl status ssh para ver o status do ssh se ele está funcional, apresentado na imagem abaixo: 

![Alt Text](https://i.ibb.co/WBBvm0p/PRINT-6-1.png)

Feito isso foi preciso liberar o acesso do SSH apenas para o grupo do TI pois não queremos que outros setores da empresa acessem os equipamentos via SSH, para isso abrimos o seguinte diretório com um editor de texto: /etc/ssh/sshd_config e inserimos uma linha com os seguintes parâmetros : AllowUsers TI 
feito isto, reiniciamos o serviço de SSH  com o comando systemctl restart ssh.

![Alt Text](https://i.ibb.co/yRDGFqZ/PRINT-6-2.png)

Assim temos um sistema de SSH totalmento funcional sendo acessado apenas para o grupo do TI pelo putty.

![Alt Text](https://i.ibb.co/8M1YqPp/PRINT-6-3.png)


Autor: Lucas Silva Conrado

 

























