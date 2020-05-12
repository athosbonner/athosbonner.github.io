---
layout: post
title: Livro, Código Limpo – Mudando sua forma de escrever códigos
date: 2017-09-12 13:32:20 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: capa_codigo_limpo.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Holidays, Hawaii]
---
Fala galera.

Há um tempo li o livro Clean Code do autor Robert C. Martin também conhecido por Uncle Bob um cara indispensável, é co-autor do Manifesto Ágil e proprietário de uma consultoria de treinamentos.

Uncle Bob cita que “Aprender a criar códigos limpos é uma tarefa árdua e requer mais do que o simples conhecimentos dos princípios e padrões”

Fiquei fascinado,  mesmo depois de tantos anos de escrito o livro parece ser bem recente.

Abaixo, deixo um pouco do que li e aprendi, não esticarei tanta coisa para não tirar o gostinho de você ler também.

Um pouco de filosofia que faz total sentido. 

    Programadores experiente veem os sistemas como histórias a ser contadas, em vez de programas a serem escritos. 
    Posso lhe ensinar a mecânica para se andar de bicicleta, coisas como a matemática clássica é relativamente direta. Gravidade, atrito, momento angular, centro de massa, e assim por diante, podem ser demonstrados com menos de uma página cheia de equações, com isso eu poderia provar pra você que é prático andar de bicicleta e lhe dar todo o conhecimento necessário para que você consiga.
    E mesmo assim você cairá na primeira vez que tentar.
    Programar não é diferente.

 

Um código limpo

Um código limpo faz bem apenas uma coisa.
Um código ruim tenta fazer coisas de mais, ele está cheio de propósitos obscuros e ambíguos.

Powered by wordads.co
Seen ad many times
Not relevant
Offensive
Covers content
Broken
Report this ad

O código limpo é centralizado. Cada função, cada classe, cada modulo expõe uma única tarefa que nunca sofre interferência  de outros detalhes ou fica rodeados por eles.

Rom Jeffries, autor de Extreme Programming Installed and Extreme Programming Adventures in C# falou o seguinte:

    Efetue todos os testes;
    Sem duplicação de código
    Expressa todas as ideias do projeto que estão no sistema
    Minimiza o número de entidades, como classes, métodos, funções e outras do tipo

O campo @author de um javadoc nos diz quem somos.

Nós somos autores, e todo autor tem leitores, como os quais uma boa comunicação é de responsabilidade dos autores. Na próxima vez em que você escrever uma linha de código, lembre-se de que você é um autor, escrevendo para leitores que julgarão seus esforços.

Trabalhando com Funções

É essencial que o nome da função expresse o que queremos que ela faça, por isso temos que criar nomes significativos.

Se um nome requer um comentário, então ele não revela seu propósito.

É desnecessário criar uma variável chamada variável Número.
Para quê esse nome variável se ela já é uma variável, estaríamos violando a lei de nomes claros e objetivos.
Outro exemplo, Para quê criar uma variável String chamada stringNomePessoa ?
Hora o nome nunca pode ser de outro tipo, você criaria uma variável do tipo int chamada nome ? Não faz menor sentido.

Funções deve fazer APENAS UMA COISA.

Use sempre nomes descritivos, um bom nome é de uma fácil leitura com funções que fazem apenas uma função, quanto menor for uma função e mais centralizada, mais fácil será escolher um nome descritivo.

Não ter medo de criar nomes extensos, pois é melhor criar um nome descritivo do que um nome pequeno que não diz nada.

Parâmetros de Funções 

O ideal é que uma função não deva ter parâmetros algum, se possível nenhum, um ainda vai, dois é o máximo..

Se tem parâmetros que seja em conjunto com os nomes da função para se tornar uma leitura agradável,

Parâmetros Lógicos 

Uma má prática que o autor relata é que passar um parâmetro boolean para uma função é a pior coisa que você pode fazer, primeiro que mostra que a função não faz apenas uma coisa, além de ficar confuso, caso você não consiga dar um nome descritivo para a mesma.

Funções com dois parâmetros se torna mais complicado de entender e leva mais tempo para se lê, principalmente se um dos parâmetros precisam ser ignorado no fim das contas.

De modo geral deve-se evitar parâmetro de saída, caso sua função precise alterar o estado de algo, faça-a mudar o estado do objeto que a pertence.

Ou a função altera o estado de um objeto ou retorna informações sobre ele.

Duplicação pode ser a raiz de todo o mal do software.

Criar um software é como qualquer outro tipo de escrita.

Ao escrever um artigo, você primeiro coloca seus pensamentos no papel e depois os organiza de modo que fiquem fáceis de ler. O primeiro rascunho pode ficar desastroso e desorganizado, então você para, reestrutura e refina até que ele fique como você deseja.

Não insira comentários em códigos ruins, reescreva-o.

Comentário

Comentários pode ser um mal necessário, mas ao invés de inserir um comentário em um código ruim, que muitas vezes fazemos isso, é melhor reescreve-lo se expressando tão claro que não precise de comentários para explicar.

Comentários não compensam códigos ruins.

O segredo é colocar no código a mesma coisa que você colocaria no comentário.

Exemplo, qual código fica melhor de se entender?

Esse:

//Verifica se o funcionário está habito a todos os benefícios
if (employee.flag && hourly_flag && employee.age > 65){}

ou esse ?

if(employee.isElegivelParaTodosOsBeneficios()) {}

Uma forma de deixar o código mais fácil de ler é conversar com a equipe para definir um padrão levando em consideração as regras propostas principalmente do livro, mas a equipe tem que decidir e não apenas uma pessoa.

A melhor documentação é aquela que já está escrita no código.

A lei de Demeter

Um módulo não deve enxergar o interior dos objetos que ele manipula.

Mais precisamente, a Lei de Demeter diz que um método M de uma classe C só deve chamar os métodos de:

    C
    De um objeto criado por X
    De um objeto passado como parâmetro para M
    De um objeto dentro de uma instância da variável C

O Método não deve chamar os métodos em objetos retornados por qualquer outra das funções permitidas.

 

Conclusão

Uncle bob trás toda a sua experiência e de outros influenciadores no mundo da programação.

O livro te faz evoluir muito, pensar diferente, criar coragem para reescrever códigos legados ruim de ler (Evitando a fala.. “Vou mexer não, tá funcionando assim!” ) e coisas do tipo.

Quis deixar apenas uma “palinha” do que o livro ensina e propõe.
Existe muito mais coisas que poderei está escrevendo em um futuro, porém recomendo fortemente que leia, é uma leitura agradável no meu ponto de vista.

Espero ter ajudado.

See you later…