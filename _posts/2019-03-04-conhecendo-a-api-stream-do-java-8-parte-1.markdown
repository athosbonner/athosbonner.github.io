---
layout: post
title: Conhecendo a API Stream do java 8 – Parte 1
date: 2017-09-12 13:32:20 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: stream-parte-1.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Holidays, Hawaii]
---

Dentre as funcionalidades que o java 8 trouxe está a API Stream que nos permite trabalhar de forma diferente com fluxo de dados, proporcionando o desenvolvedor escrever um número menor de linha de código de forma mais simples.

Nesta série de post vamos falar um pouco sobre a API Stream que foi incorporada no java 8.

A API Stream do Java é responsável por manter a ordenação dos dados como está na fonte.

As operações agregadas ou operações em massa são operações que nos permitem expressar e manipular elementos de fluxo de maneira fácil e clara.

De princípio vamos entender melhor o que é uma Java Stream .
Java.util.Stream

Em java o pacote java.util.Stream representa um fluxo de dados onde poderá ser executado uma ou mais operações.

Os fluxos de uma Stream é criado a partir de uma origem, por exemplo, podemos usar o java.util.Collection como uma lista para termos um fluxo de Stream, uma vez criada a origem podemos explorar todo o recurso do mesmo.

Uma vantagem do Stream é que você pode fazer um fluxo sequencial ou paralelo.
Quais as características do Stream ?

Abaixo está listado 6 características do Stream.

    Não é uma estrutura de dados
    Foi projetado para o lamba com o surgimento no Java 8
    Não suporta o acesso indexado
    Podemos converter em matrizes ou listas
    Suporta lazy access
    Suporta paralelismo

Agora que já sabemos o que é o Stream vamos colocar a mão na massa.

A seguir vou mostrar algumas funcionalidade que podemos explorar do java.util.Stream. Todo o código implementado aqui está disponível no GitHub.
Criando fluxos com Stream

                public static void main(String[] args) {

                Stream<Integer> useStream = Stream.of(1,2,3,4,5);
                useStream.forEach(p -> System.out.println(p));

                }

Ou podemos passar um objeto em Stream.of() também.

                public static void main(String[] args) {

                Stream<Integer> useStream = Stream.of(new Integer[] {1,2,3,4,5});
                useStream.forEach(p -> System.out.println(p));

                }

Resultados:

1
2
3
4
5

Usando uma lista como origem de fluxo.
List.stream ()

                public static void main(String[] args) {

                List<String> lista = new ArrayList<>();
                lista.add("Homemerro");
                lista.add("Capitãoica");
                lista.add("Doutoranho");

                Stream<String> useStream = lista.stream();
                useStream.forEach(p -> System.out.println(p));

                }

A partir da lista podemos explorar todo os recursos do Stream.

Resultado:

Homem de Ferro
Capitão America
Doutor Estranho

                Stream.generate() ou Stream.iterate()

                public static void main(String[] args) {

                Stream<Date> useStream = Stream.generate(() ->
                {
                return new Date();
                });

                useStream.forEach(p -> System.out.println(p));
                }

O Stream.generate vai gerar várias vezes o que você mandar ele fazer, no meu caso mandei apenas ele imprimir a data atual, conforme a saída abaixo.

Mon Mar 04 15:01:35 BRT 2019
Mon Mar 04 15:01:35 BRT 2019
Mon Mar 04 15:01:35 BRT 2019
Mon Mar 04 15:01:35 BRT 2019
Mon Mar 04 15:01:35 BRT 2019
Mon Mar 04 15:01:35 BRT 2019
Mon Mar 04 15:01:35 BRT 2019
Mon Mar 04 15:01:35 BRT 2019
Mon Mar 04 15:01:35 BRT 2019

Outro recurso do Stream é o Stream.builder, ele nos fornece várias opções para trabalhar com o tipo que você escolher, no código abaixo estou explorando o Stream.builder do tipo String.
Stream.builder()

                public static void main(String[] args) {
                //Usando Stream Builder
                Stream.Builder<String> useStreamBuilder = Stream.builder();

                //adicionando elementos string ao Stream
                Stream<String> useStream = useStreamBuilder
                .add("Capitã marvel")
                .add("Avengers: Endgame")
                .build();

                //Listando os elementos adicionado e imprimindo
                useStream.forEach(System.out::println);

                }

Agora que você já sabe criar uma Stream e usar, vou mostrar alguns métodos do Stream que nos ajuda de forma simples.
Conhecendo e usando métodos do Stream

Vamos explorar o método filter() do Stream.
Método filter()

                List<Cliente> lista = new ArrayList<>();

                Stream<Cliente> stream = lista.stream().filter(item-> item.getNacionalidade().equals("Brasileira"));
                stream.forEach(System.out::println);

No código acima filtramos todos os clientes de nacionalidade brasileira.

Junto com o filter podemos usar outros método de agregação para melhorar ainda mais nosso filtro.

Abaixo estou usando o método avarege() que nos permite calcular a média dos valores dos elementos dentro da lista de Clientes que estamos percorrendo.

                double stream = lista.stream()
                .filter(item-> item.getNacionalidade().equals("Brasileiro"))
                .mapToInt(item-> item.getIdade()).average().getAsDouble();

Usei o método avarege(), mas também posso usar outros como o  count(),  sum(), min(), max() como mostrado abaixo.
Usando Min()

                double stream = lista.stream()
                .filter(item-> item.getNacionalidade().equals("Brasileiro"))
                .mapToInt(item-> item.getIdade()).min().getAsInt();

Usando Max()

                double stream = lista.stream()
                .filter(item-> item.getNacionalidade().equals("Brasileiro"))
                .mapToInt(item-> item.getIdade()).max().getAsInt();

Usando Count()

                double stream = lista.stream()
                .filter(item-> item.getNacionalidade().equals("Brasileiro"))
                .mapToInt(item-> item.getIdade()).count();

Usando Sum()

                double stream = lista.stream()
                .filter(item-> item.getNacionalidade().equals("Brasileiro"))
                .mapToInt(item-> item.getIdade()).sum();

Como podemos ver o Stream facilita muito nosso trabalho, ainda temos muito o que explorar nessa API, mas por hora é isso.

O que você achou, fácil, não ?

Isso é um pouquinho do que o Stream é capaz de nos proporcionar, em futuros artigos irei mostrar outras funcionalidades mais detalhadas do Stream, que já me salvou muitas vezes.

See you later…

Download dos exemplos desse post no meu GitHub. Acesse aqui

 

PARA SABER MAIS:

Java 8 Stream API
https://howtodoinjava.com/java8/java-streams-by-examples/

Java Code Examples for java.util.stream.Stream.builder();
https://www.programcreek.com/java-api-examples/?class=java.util.stream.Stream&method=builder