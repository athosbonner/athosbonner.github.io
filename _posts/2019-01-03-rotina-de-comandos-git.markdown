---
layout: post
title: Rotina de comandos GIT
date: 2017-09-12 13:32:20 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: capa-git.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Holidays, Hawaii]
---

Controle de versão hoje em dia é indispensável para o desenvolvimento de software, principalmente quando estamos em equipe.

Controle de versão serve para versionar seu código fonte e manter versões de códigos desenvolvido por toda equipe e caso tenha bug, erros, alguma anomalia no seu código a versão pode ser revertida para o estado anterior ou alguma outra versão que deseja.

Para que o controle de versão aconteca existe alguns softwares no mercado que você poderá usar.

Exemplos de softwares para controle de versão mais conhecido no mercado:

    SVN (Subversion)
    GIT
    Mercurial

O objetivo é implementar suas modificações e deixar o código em um lugar seguro onde todos da equipe possam ver e ter acesso.

Nesse post vou mostrar apenas comandos básicos do GIT.

Para iniciar o git no diretório da aplicação que você esta desenvolvendo digite em seu terminal após ter instalado em sua maquina.

git init

Isso mesmo, apenas isso vai tornar o seu diretório versionavél.

Se você já tem um repositório com algum projeto, você terá que fazer o clone desse projeto para sua maquina, então digite:

git clone [link do clone]
Exemplo :

    $ git clone https://github.com/libgit2/libgit2

Atualizando o seu projeto com as modificações do servidor.
Exemplo:

    $ git pull

Para você saber qual o status dos arquivos que foram modificados

    $ git status

Com esse comando você verá os arquivos em vermelhos, são arquivos que foram modificados e podem ser versionados.

    $ git add .

Com o comando git add . você está adicionando todos os arquivos para serem versionados, então os arquivos que você viu em vermelho com o git status agora vão está todos verdes.

Você pode dar um git status novamente para conferir.

Agora os arquivos estão prontos para realizar o commit e depois o push.

Quando você faz o commit o git prepara seus arquivos ainda em sua maquina com uma descrição colocada por você referenciando o que foi feito, essa descrição também vai ficar no servidor onde está hospedado seu código quando você fizer o push.

    $ git commit -m "Finalizando rotina de Cadastro de Cliente"

Comando git com a mensagem de identificação.

    $ git push 

Esse comando sobe todos os arquivos adicionados para o servidor, junto com sua descrição.

Pronto, agora você pode ir lá no seu servidor e ver a última modificação com sua descrição e todos da equipe também poderá ver e baixar.

Qualquer coisa, comenta ai.

Espero que tenha ajudado, até mais.