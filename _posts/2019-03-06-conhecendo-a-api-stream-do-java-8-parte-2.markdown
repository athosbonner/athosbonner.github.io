---
layout: post
title: Conhecendo a API Stream do java 8 – Parte 2
date: 2017-09-12 13:32:20 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: stream-parte-2.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Holidays, Hawaii]
---

Esta é a segunda parte da nossa saga de posts sobre a API Stream, incorporada no Java 8.

Hoje vamos trabalhar com Coleções de dados e mostrar um pouco do que o Stream é capaz.

Vamos começar convertendo o Stream em lista com o Stream.collect().
Stream.collect( Collectors.toList() )
Usando .Collect para converver um Stream em Lista

        List<Integer> lista = new ArrayList<>();

        //Convertendo lista para Stream
        Stream<Integer> stream = lista.stream();

        //Convertendo Stream em Lista
        List<Integer> convertendoParaLista = stream.collect(Collectors.toList());

System.out.println(convertendoParaLista);

Agora vamos converter uma Stream em Array.
        Stream.toArray( )

        List<Integer> lista = new ArrayList<>();

        Stream<Integer> stream = lista.stream();

        //Convetendo Stream em Array com a classe toArray passando o tipo do array.
        Integer[] convetendoStreamEmArray = stream.toArray(Integer[]::new);

        System.out.println(convetendoStreamEmArray);

Não podemos negar que é muito simples e fácil.
Retornando lista sem dados repetidos – Stream.distinct()
Uma das funcionalidades que eu mais gosto é o distinct(), me salvou na primeira vez que precisei.

        List<Integer> lista = new ArrayList<>();
        lista.add(1);
        lista.add(2);
        lista.add(3);
        lista.add(4);
        lista.add(4);

        Stream<Integer> stream = lista.stream();

        //Converendo Stream em lista sem repetidos
        List<Integer> listaSemRepetidos = stream.distinct().collect(Collectors.toList());

        //Imprimindo todos os dados da lista.
        listaSemRepetidos.forEach(System.out::println);

Resultado:

1
2
3
4

Operações Intermediárias
Dentro do Stream temos algumas funções que nos ajuda a fazer uma pesquisa mais completa dentro de uma lista.
Stream.filter()

Abaixo estamos usando o método filter do Stream, estou trazendo uma contagem de quantos homens de ferro existem na lista.

        List<String> lista = new ArrayList<>();
        lista.add("Homemerro");
        lista.add("Doutoranho");
        lista.add("Capitãoica");
        lista.add("Viúvaa");
        lista.add("Homemerro");
        lista.add("ThorStream<String> stream = lista.stream();

        long hero = stream.filter((item) -> item.equals("Homem de Ferro")).count();

        System.out.println(hero);

Resultado:

2

Stream.map()
Com o map() podemos fazer manipulação dos dados em questão.
A seguir estou convertendo os objetos que estão sendo processados para maiúsculo, mas podemos fazer qualquer tipo de operação.

        List<String> lista = new ArrayList<>();
        lista.add("Homemerro");
        lista.add("Doutoranho");
        lista.add("Capitãoica");
        lista.add("Viúvaa");
        lista.add("ThorStream<String> stream = lista.stream();

        stream.filter((item) -> item.equals("Homem de Ferro")).map(String::toUpperCase).forEach(System.out::println);

Resultado:

HOMEM DE FERRO

Outro exemplo

        List<String> lista = new ArrayList<>();
        lista.add("Homemerro");
        lista.add("Doutoranho");
        lista.add("Capitãoica");
        lista.add("Viúvaa");
        lista.add("ThorStream<String> stream = lista.stream();

        stream.filter((item) -> item.equals("Homem de Ferro")).map((item) ->{

        //Se esse for o home de ferro então faça alguma coisa
        if (item.equals("Homem de Ferro")) {
        item += " - Esse é o Tony Stark";
        }

        //Retornando o dado tratado.
        return item;

        }).forEach(System.out::println);

        }

Resultado :

Homem de Ferro - Esse é o Tony Stark

Stream.sorted()
O Sorted() retorna os dados em ordem alfabética, mas você pode usar um comparator para personalizar essa ordenação se for o caso.

        List<String> lista = new ArrayList<>();
        lista.add("Homemerro");
        lista.add("Doutoranho");
        lista.add("Capitãoica");
        lista.add("Viúvaa");
        lista.add("ThorStream<String> stream = lista.stream();

        stream.sorted().map(String::toUpperCase).forEach(System.out::println);

Resultado:

CAPITÃO AMERICA
DOUTOR ESTRANHO
HOMEM DE FERRO
THOR
VIÚVA NEGRA

Terminal operations
Operações de terminal produzem um resultado não-fluxo, como valor primitivo, uma coleta ou nenhum valor.
As operações de terminal são normalmente precedidas por operações intermediárias que retornam outro fluxo que permite que as operações sejam conectadas em uma forma de consulta.
Stream.collect ()
Esse método retorna uma lista a partir de uma Stream, já usamos antes.

        List<Integer> lista = new ArrayList<>();

        //Convertendo lista para Stream
        Stream<Integer> stream = lista.stream();

        //Convertendo Stream em Lista
        List<Integer> convertendoParaLista = stream.collect(Collectors.toList());

        System.out.println(convertendoParaLista);

        Stream.forEach ()
O método forEach() percorre cada elemento da lista, você pode fazer operações dos objetos com a expressões lambda é uma forma simplificada de escrever um loop.

        List<Integer> lista = new ArrayList<>();
        lista.forEach(System.out::println);

Como podemos ver no java 8, dentro de cada coleção de dados temos um método forEach para percorrer todo os objetos da lista.
Stream.match ()
O método match() também é um dos meus preferidos, ele vai retornar boolean quando uma determinada operação for satisfatória, abaixo mostro três exemplos com os métodos, anyMatch(), allMatch(), nomeMatch()

        List<String> lista = new ArrayList<>();
        lista.add("HOMEMERRO");

        boolean retorno = true;
        //Usando anyMatch, retorna true se item for iqual a HOMEN DE FERRO
        retorno = lista.stream().anyMatch((item)-> item.equals(“HOMEM DE FERRO”));
        System.out.println(retorno);
        //Retorna true se item começar com a letra A
        retorno = lista.stream().allMatch((item) -> item.startsWith(“A”));
        System.out.println(retorno);
        //Retorna true se o item não corresponder a condição.
        retorno = lista.stream().noneMatch((item)-> item.endsWith(“g”));

        System.out.println(retorno);

Resultado:

true
false
true

Stream.count ()
O método count() também já usamos aqui, ele simplesmente retorna a quantidade de item de uma lista e estamos usando em conjunto com o método filter para fazer uma pesquisa mais completa dentro da lista.

        List<String> lista = new ArrayList<>();
        lista.add("HOMEMERRO");
        lista.add("HOMEMERRO");
        lista.add("HOMEMERRO");

        long resultado = lista.stream().filter((item) -> item.equals(“HOMEM DE FERRO”)).count();

        System.out.println(resultado);

Resultado:

    3

        Stream.reduce ()

O reduce() realiza uma redução dos elementos de um fluxo com uma função especificada e retorna um Optional()  com o valor reduzido.

 É equivalente a expressão:

        boolean foundAny = false;
            T result = null;
            for (T element : this stream) {
                if (!foundAny) {
                    foundAny = true;
                    result = element; } else result = accumulator.apply(result, element); } return foundAny ? Optional.of(result) : Optional.empty(); }

Exemplo de utilização do reduce(), estou usando para somar todos os valores da minha lista de tipo Integer.

        List<Integer> lista = new ArrayList<>();
        lista.add(1);
        lista.add(2);
        lista.add(3);

        //Somando todos os valores da lista.
        Optional<Integer> reduced = lista.stream().reduce((s1,s2) -> s1 + s2);

        //Imprimindo se for satisfatória
        reduced.ifPresent(System.out::println);

Resultado:

6


Como podemos ver, a API Stream do java 8 nos ajuda muito, com pouco código fazemos muito.

Essa foi a segunda parte da saga API Stream Java 8.

Espero ter ajudado.

See you later…

Download dos exemplos desse post e do primeiro no meu GitHub. Acesse aqui

PARA SABER MAIS:

Java 8 Stream API
https://howtodoinjava.com/java8/java-streams-by-examples/

Documentation java.util.Stream
https://docs.oracle.com/javase/8/docs/api/java/util/stream/package-summary.html

Java Code Examples for java.util.stream.Stream.builder();
https://www.programcreek.com/java-api-examples/?class=java.util.stream.Stream&method=builder