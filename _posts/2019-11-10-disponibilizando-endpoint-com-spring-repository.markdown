---
layout: post
title: Disponibilizando Endpoint com Spring Repository
date: 2017-09-12 13:32:20 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: capa_rest_spring.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Holidays, Hawaii]
---

Fala galera, tudo bem ?

Neste tutorial irei mostrar como disponibilizar um endpoint com os Framework:

    Spring web
    JPA
    Rest Repository

Para esse tutorial vamos usar o spring start io para criar um projeto no Spring com os Framework em questão.

O projeto criado nesse site vem com as classes de configuração do Spring, então não precisamos nos preocupar com isso.

Vamos começar acessando o site spring start io e criando um projeto como mostra a imagem abaixo.

Exportando do Spring IO 

![I and My friends]({{site.baseurl}}/assets/img/1-spring_boot.png)

Imagem 1

Para nosso exemplo foi escolhido um projeto com Maven, Java e as dependências do Spring Web, JPA, Rest Repository.

Para esse tutorial não vamos usar nenhum banco de dados, porém você pode usar qualquer um de sua preferência.

A versão que estou usando do java é a 8, mas temos a opção de usar até a 13 que nesse momento é a mais atual.

Feito isso, apenas iremos importar como um projeto Maven na sua IDE de preferência, no meu caso estou usando a do próprio Spring – Spring tools na versão 4 .

IDE_projeto_importado

![I and My friends]({{site.baseurl}}/assets/img/2-spring_boot.png)

Imagem 2

Esse é o projeto importado no Spring Tools 4.

A classe CrudApplication.java tem um método main() conforme abaixo.

public static void main(String[] args) {
       SpringApplication.run(CrudApplication.class, args);
}

Ele é o responsável por inicializar seu projeto.

Agora é hora de colocar a mão na massa.

Nosso projeto terá dois beans e duas interfaces que serão Autor e Livro.

Beans:

    Autor.java
    Livro.java

E iremos criar os repositórios dos beans.

    AutorRepository.java
    LivroRepository.java

E por fim, iremos criar nossa classe que será o Controller para disponibilizar o EndPoint.

Então nossos beans ficaram assim.

OsBens

![I and My friends]({{site.baseurl}}/assets/img/3-spring_boot.png)

Imagem 3

    import javax.persistence.Entity;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.validation.constraints.NotBlank;


O código para você copiar.

    @Entity //Indica que essa classe também é uma tabela no banco de dados
    public class Autor {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    @NotBlank
    private String nome;

 

    import java.util.HashSet;
    import java.util.Set;

    import javax.persistence.Entity;
    import javax.persistence.FetchType;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.ManyToMany;
    import javax.validation.Valid;
    import javax.validation.constraints.Min;
    import javax.validation.constraints.NotBlank;

    @Entity
    public class Livro {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @NotBlank
    private String titulo;

    @NotBlank
    private String descricao;

    @Min(30)
    private Integer numeroPagina;

    @Valid
    @ManyToMany(fetch = FetchType.EAGER)
    private Set<Autor> autores = new HashSet<>();

    public void add(Autor autor) {
    autores.add(autor);
    }

Agora que temos nossos beans criados, precisamos criar nossas interfaces e cada interface irá estender a Classe CrudRepository é com essa classe que o Spring saberá qual bean ele está tratando e poderá trabalhar “automagicamente” em qualquer operação de CRUD que queiramos usar.

interfaces

![I and My friends]({{site.baseurl}}/assets/img/4-spring_boot.png)

Imagem 4

    import org.springframework.data.repository.CrudRepository;
    import com.br.crud.rest.crud.model.Livro;

    public interface LivroRepository extends CrudRepository<Livro, Long>{

    }

    

    import org.springframework.data.repository.CrudRepository;

    import com.br.crud.rest.crud.model.Autor;

    public interface AutorRepository extends CrudRepository<Autor, Long> {
        
    }

 

Como podemos perceber é muito simples, estendendo a classe CrudRepository.java estamos avisando ao Spring que o bean que ele está tratando é o passado por parâmetro ao CrudRepository<Autor, Long>.

Agora que temos nossos beans e interfaces criadas é hora de criar a classe que irá disponibilizar o endpoint.

Aproveitei a classe de configuração do Spring para criar um método que irá ser anotado com o @PostController.

ProjetoFinal

![I and My friends]({{site.baseurl}}/assets/img/5-spring_boot.png)

Imagem 5

Depois de criado é só inicializar o servidor e acessar o endereço http://localhost:8080/ verá a imagem abaixo em seu navegador.

Perceba que ele disponibiliza os nossos beans criados e se você acessar um desses links verá o objeto que setamos na imagem 5.

localhost

![I and My friends]({{site.baseurl}}/assets/img/6-spring_boot.png)

Imagem 6

 

Livros

![I and My friends]({{site.baseurl}}/assets/img/7-spring_boot.png)

Imagem 7

Por padrão o RestRepository cria o profile/, mas o que tem nele ?

Se acessarmos o endereço http://localhost:8080/profile/autors verá toda as meta-informações do autors conforme exemplo na imagem abaixo.

profile

![I and My friends]({{site.baseurl}}/assets/img/8-spring_boot.png)

Imagem 8

 

Realmente foi muito fácil.

Criar um endpoint com Spring é muito fácil e rápido ajudando assim a vida do programador, para melhorar a segurança podemos usar o Spring Security, também adicionar um banco de dados e usar o Hibernate para mapear as tabelas.

Esse foi um pequeno exemplo do poder desta ferramenta que tem muito mais a ser explorada.

Se tem alguma coisa a corrigir ou acrescentar, deixa nos comentários aqui que vai ser de boa ajuda.

Todo o código está no gitHub acessa lá e baixa para testar.

Baixar o código no meu gitHub

Espero ter ajudado.

See you later….