---
layout: post
title: Interfaces funcionais java 8 – Expressões lambda
date: 2017-09-12 13:32:20 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: erro_interface_funcional.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Holidays, Hawaii]
---

Interfaces funcionais são o coração dos recursos do lambda, no java 8 qualquer interface que contenha um método abstrato pode ser invocado como uma expressão lambda.

Um exemplo de classe que podemos invocar no java 8 como expressões lambda é o Comparator, como no exemplo abaixo da sua escrita.

    interface Comparator,<T> {
        boolean compare(T t);
    }

A interface Comparator tem apenas um método abstrato e é isso que faz ele ter os recursos do lambda.
Só para lembrar, todo método em uma interface por padrão são Públicos e Abstratos.

Criando uma Interface Funcional 

Primeiro vamos criar nossa interface genérica e dar a ela apenas um método que vou chamar de transforma(T t), quem for usar esse método é quem vai determinar qual o comportamento do mesmo.

    public interface Transformador<T> {
            String transforma(T t);
    }

Agora que temos nossa interface, vamos implementar e determinar seu comportamento.

O comportamento do método transforma(T t) da interface Transformador vai ser receber uma String e retornar a mesma como maiúscula, apenas isso para exemplificar o uso da nossa Interface funcional.

Então abaixo podemos fazer assim:

    Transformador<String> transfNomeEmMaiusculo = valor -> {
              return valor.toUpperCase();
    };
    System.out.println(transfNomeEmMaiusculo.transforma("athos bonner"));

O que fiz foi apenas chamar a nossa interface e usar a expressão lambda: valor -> {} para determinar qual o comportamento do método, então apenas usei o toUpperCase para transformar toda a String passada para maiúscula e em seguida imprimir o retorno em um System.out passando meu nome.

Simples assim!

Ai você me pergunta…. Mas Athos, então quer dizer que uma interface funcional só pode ter apenas um método ? como assim, bial ???

Isso mesmo, uma interface funcional precisa ter apenas um método, Como exemplo as interfaces: java.util.Comparator, java.lang.Runnable , java.util.concurrent.Callable.

Mas e se eu criar dois métodos nesta mesma interface irá dar erro ?

Não, porém ela não irá ser mais uma interface funcional e você não vai poder usar as expressões lambda que nosso querido java 8 nos presenteou.

Mas Athos, eu posso impedir que o estagiário mude minha interface sem querer ???

Claro que sim!

Você pode usar a anotação @FunctionalInterface para impedir que essa interface não permita que criem mais de um método.

Exemplo, nossa Interface Transformador ficou assim.

    @FunctionalInterface
    public interface Transformador<T> {
            String transforma(T t);
    }

Apenas isso!

A partir de agora se você tiver usando alguma IDE e tentar criar mais um método nessa interface irá receber esse erro.

![I and My friends]({{site.baseurl}}/assets/img/erro_interface_funcional.png)

e se tentar compilar vai recer esse erro.

java: Unexpected @FunctionalInterface annotation
Transformador is not a functional interface multiple non-overriding abstract methods found in interface

 

Bom espero ter ajudado!

See you later….

 

Download dos exemplos disponível no meu GitHub. Acesse aqui

PARA SABER MAIS:

Java 8 Prático
Java 8 Prático: Lambdas, Streams e os novos recursos da linguagem

Package java.util.function
https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html