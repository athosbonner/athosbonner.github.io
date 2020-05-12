---
layout: post
title: Usando Classe Optional do java 8
date: 2017-09-12 13:32:20 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: capa_java_opcional.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Holidays, Hawaii]
---
O java 8 trouxe muitas mudanças, já vimos aqui algumas, como Interfaces Funcionais ou em Stream parte 1 e Stream parte 2.

Mas uma delas que pouco é comentada e que chamou muita minha atenção foi a classe Optional.

Essa classe, encapsula o retorno de métodos e verificar se um valor do tipo <T> existe ou não em um objeto.

Com isso podemos evitar o tão conhecido e chato NullpointerException.

Também não vamos mais precisar fazer verificações do tipo: if (client != null).

E o melhor o seu código irá ficar mais simples, limpo e fácil.

Abaixo mostro alguns métodos que ele possui.

    empty – Retorna uma instância vazia do Optional.

    Motódo: public static <T> Optional<T> empty​()

    Implemetação:

      Optional<String> op = Optional.empty();

    ofNullable – Se não for nulo, retorna o valor, caso contrário retorna um Optional vazio.

    Método:  public static <T> Optional<T> ofNullable​(T value)

    Implemetação:

    String conta = null;		
    Optional<String> receber = Optional.ofNullable(conta);

    of – Retorna um Optional com o valor se o mesmo não for nulo.

    Método: public static <T> Optional<T> of​(T value)

    Implementação:

     Optional<String> pegar = Optional.of(conta);

    isPresent – Retorna true se existir o valor, caso contrário retorna false.

    Método: public boolean isPresent​()

    Implementação:

    Optional<String> pegar = Optional.of(conta);		
    if(pegar.isPresent()) {
    	System.out.println("Haloo");
    }

    filter – Se existir valor e for correspondente a condição especificada é retornado um Optional com o valor, caso contrário retorna um Optional vazio.
    veja mais aqui sobre o filter.

    Método: public Optional<T> filter​(Predicate<? super T> predicate)

    Implementação:

    String numeroConta = pegar.filter((conta) -> conta.equals("123456")).get();

    ifPresent – Se existir valor executa a ação determinada com esse valor verificado, caso contrário, não faz nada.

    Método: public void ifPresent​(Consumer<? super T> action)

    Implementação:

    pegar.ifPresent((item)->item.replace("Guaraná", "barrio de chop"));

    get – Se o valor existir, retorna o valor, caso contrário é lançado uma exceção do tipo NoSuchElementException

    Método: public T get​()

    Implementação:

    Optional<String> heroi = Optional.of(homenDeFerro);
    String definirAcoes = heroi.get();

    map – Se existir o valor, retorna um Optional com o resultado da aplicação usada na condição do map, caso contrário, retorna um Optional vazio.
    Já mostrei como funciona o map aqui em outro post.

    Método: public <U> Optional<U> map​(Function<? super T,? extends U> mapper)

    implementação:

    Optional<String> pegar = Optional.of(homenDeFerro).map(String::toUpperCase);

Bom galera, esses são alguns dos métodos que a classe nos proporciona, mas usem com moderação, saiba tratar bem as validações e informar as mensagens dos erros corretos.

Quis mostrar um pouco do poder dessa classe implementada no java 8, espero que tenha ajudado.

Se tem alguma coisa a corrigir ou acrescentar, deixa nos comentários aqui que vai ser de boa ajuda.

 

Espero ter ajudado.

See you later…

 

PARA SABER MAIS:

https://docs.oracle.com/javase/8/docs/api/java/util/Optional.html#orElseGet-java.util.function.Supplier-