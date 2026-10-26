# Introdução ao Scala

Scala é uma linguagem de programação de código aberto criada por Martin Odersky na EPFL, uma universidade da Suíça. O projeto começou em 2001 e a primeira versão pública saiu em 2004. O nome vem de *scalable language* - uma linguagem que cresce junto com as necessidades de quem a usa, do script pequeno ao sistema grande.

Em 2021 foi lançado o **Scala 3**, uma revisão grande da linguagem que simplificou a sintaxe e reforçou o sistema de tipos. Este lab usa Scala 3.

## Por que o Scala foi criado

Martin Odersky já tinha trabalhado no compilador do Java e na introdução de generics na linguagem. A ideia do Scala era mostrar que **orientação a objetos e programação funcional não são opostas**: dá para ter as duas em uma linguagem só, com tipos estáticos e rodando na JVM, aproveitando todo o ecossistema Java.

## Características principais

### Orientação a objetos e funcional ao mesmo tempo

Em Scala, todo valor é um objeto - e toda função também é um valor. Você modela o domínio com classes e traits, e transforma dados com funções:

```scala
case class Cachorro(nome: String, idade: Int)

val caramelos = List(Cachorro("Paçoca", 3), Cachorro("Biscoito", 1))

val adultos = caramelos.filter(_.idade >= 2).map(_.nome)
// List(Paçoca)
```

### Imutabilidade por padrão

`val` declara um valor que não pode ser reatribuído; `var`, uma variável que pode. As coleções padrão (`List`, `Vector`, `Map`, `Set`) são **imutáveis**: operações como `map` e `filter` retornam uma coleção nova em vez de alterar a original. Isso elimina uma classe inteira de bugs, principalmente em código concorrente.

```scala
val total = 10
// total = 20   // erro de compilação: reatribuição de val
```

### Tudo é expressão

Em Scala, `if`, `match` e blocos retornam valores. Isso deixa o código mais curto e evita variáveis temporárias:

```scala
val categoria = if idade >= 18 then "adulto" else "jovem"
```

### Pattern matching

O `match` compara um valor com padrões e extrai dados ao mesmo tempo. Combinado com `enum` e `case class`, o compilador avisa quando você esquece um caso:

```scala
enum Forma:
  case Circulo(raio: Double)
  case Retangulo(largura: Double, altura: Double)

def area(forma: Forma): Double = forma match
  case Forma.Circulo(r)       => math.Pi * r * r
  case Forma.Retangulo(l, a)  => l * a
```

### Tipagem estática com inferência

Os tipos são verificados em tempo de compilação, mas na maioria das vezes você não precisa escrevê-los: o compilador infere. O sistema de tipos do Scala é um dos mais expressivos entre as linguagens populares, e permite garantir muita coisa antes de o programa rodar.

### Sem `null` no dia a dia

Em vez de `null`, o código Scala idiomático usa `Option` para valores que podem estar ausentes, e `Either` ou `Try` para operações que podem falhar:

```scala
val numero: Option[Int] = "42".toIntOption

numero match
  case Some(n) => println(s"Número: $n")
  case None    => println("Não é um número")
```

### Interoperabilidade com Java

Scala compila para bytecode da JVM e usa bibliotecas Java diretamente, sem adaptadores. Também existem o **Scala.js**, que compila para JavaScript, e o **Scala Native**, que gera executáveis nativos.

## Onde o Scala é usado

- **Engenharia de dados** - o Apache Spark é escrito em Scala e é uma das ferramentas mais usadas para processar grandes volumes de dados
- **Sistemas distribuídos e backend** - serviços de alta concorrência com bibliotecas como Pekko (sucessor aberto do Akka), Cats Effect e ZIO
- **Programação funcional** - o ecossistema Typelevel (Cats, http4s, fs2) e o ZIO são referências em programação funcional na indústria
- **Empresas de tecnologia e fintechs** que precisam de código confiável e de alta performance

## Anatomia de um programa Scala

```scala
@main def ola(nome: String): Unit =
  val mensagem = s"Olá, $nome!"
  println(mensagem)
```

- **`@main`** - marca a função como ponto de entrada. Os parâmetros viram argumentos de linha de comando (`scala run . -- Caramelo`).
- **`def ola(nome: String): Unit`** - declara uma função com um parâmetro do tipo `String`. `Unit` é o equivalente ao `void`: a função não retorna valor útil.
- **`=` e a indentação** - no Scala 3, o corpo da função é definido pela indentação, sem chaves (que continuam permitidas).
- **`val mensagem = ...`** - declara um valor imutável. O tipo `String` é inferido.
- **`s"Olá, $nome!"`** - uma **string interpolada**: o `s` antes das aspas permite inserir valores com `$`.

Repare que não há ponto e vírgula: o fim da linha encerra a instrução.

## A curva de aprendizado

Scala é uma linguagem grande, e dá para escrever código muito diferente com ela. Algumas dicas para começar bem:

- **Comece pelo básico do Scala 3** - `val`, funções, case classes, coleções e `match` já levam longe
- **Prefira `val` e coleções imutáveis** - use `var` só quando realmente precisar
- **Não pule direto para bibliotecas funcionais avançadas** - Cats e ZIO fazem muito mais sentido depois de dominar a base
- **Use o REPL e o Scastie** para testar ideias rapidamente

## Referências

- [Scala 3 Book - documentação oficial](https://docs.scala-lang.org/scala3/book/introduction.html)
- [Tour of Scala](https://docs.scala-lang.org/tour/tour-of-scala.html)
- [A Brief History of Scala - Martin Odersky](https://www.artima.com/weblogs/viewpost.jsp?thread=163733)
- [Scala 3 - New in Scala 3](https://docs.scala-lang.org/scala3/new-in-scala3.html)
