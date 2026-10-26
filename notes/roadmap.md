# Scala Roadmap

Um guia prático e progressivo para aprender Scala, dominar a programação funcional e construir aplicações de backend.

## 🧱 1. Fundamentos de Programação

### Lógica de Programação

- Algoritmos e resolução de problemas
- Pseudocódigo
- Linguagens compiladas vs interpretadas

### Conceitos básicos

- Variáveis e constantes
- Tipos de dados
- Comentários
- Entrada e saída no terminal

### Controle de fluxo

- Condicionais
- Estruturas de repetição
- Funções

## 🔺 2. Primeiros Passos com Scala

### Ambiente

- JDK e a JVM
- Instalação com o Coursier
- Scala CLI: `run`, `compile`, `test`, `fmt`, `repl`
- sbt
- Editor com Metals ou IntelliJ

### Sintaxe do Scala 3

- `val` e `var`
- Tipos básicos e inferência de tipos
- Strings interpoladas (`s`, `f`, `raw`)
- Indentação significativa e chaves opcionais
- `if`, `while` e `for` como expressões
- Funções, parâmetros nomeados e valores padrão
- `@main` e argumentos de linha de comando

## 🧩 3. Modelagem de Dados

- Classes e objetos (`object`)
- Companion objects
- Case classes
- Traits e mixins
- Enums e ADTs (algebraic data types)
- Opaque types
- Extension methods

## 🔀 4. Pattern Matching

- `match` e exaustividade
- Desestruturação de case classes e tuplas
- Guards
- Extractors (`unapply`)
- Pattern matching em `val` e `for`

## 📦 5. Coleções

- `List`, `Vector`, `Set` e `Map` imutáveis
- Funções de ordem superior: `map`, `filter`, `flatMap`, `fold`
- `groupBy`, `groupMapReduce`, `sortBy`, `zip`
- `for comprehensions`
- `Iterator` e `LazyList`
- Coleções mutáveis e quando usar

## ⚠️ 6. Tratamento de Erros

- `Option`
- `Either`
- `Try`
- Exceções e quando usar
- Encadeando falhas com `for`

## λ 7. Programação Funcional

- Funções puras e efeitos colaterais
- Imutabilidade
- Funções como valores, currying e composição
- Recursão e `@tailrec`
- Funções parciais

## 🧬 8. Sistema de Tipos

- Generics
- Variância (`+A`, `-A`)
- Type bounds
- Union e intersection types
- Givens, `using` e type classes
- Context bounds
- Inline e metaprogramação (conceitual)

## 🗂️ 9. Organização de Projetos

- Pacotes e imports
- sbt: `build.sbt`, dependências e plugins
- Projetos multi-módulo
- Mill (alternativa ao sbt)

## 🧪 10. Testes e Qualidade

- MUnit
- ScalaTest
- Testes baseados em propriedades (ScalaCheck)
- scalafmt
- Scalafix e opções de alerta do compilador

## 🐱 11. Programação Funcional com Typelevel

- Cats: `Functor`, `Monad`, `Applicative`, `Semigroup`, `Monoid`
- Validação com `Validated`
- Cats Effect: `IO`, `Resource`, `Ref`, fibers
- fs2 (streams)

## 🌀 12. ZIO

- `ZIO[R, E, A]`
- Tratamento de erros tipado
- Injeção de dependências com `ZLayer`
- Fibers e concorrência
- ZIO HTTP

## ⚡ 13. Concorrência

- `Future` da biblioteca padrão
- Concorrência com Cats Effect ou ZIO
- Modelo de atores com Pekko
- Virtual threads da JVM

## 🌐 14. Desenvolvimento Web e APIs

- http4s
- Tapir (endpoints tipados e OpenAPI)
- Play Framework
- JSON com circe, upickle ou jsoniter-scala
- Cliente HTTP com sttp

## 🗄️ 15. Banco de Dados

- Doobie (JDBC funcional)
- Skunk (PostgreSQL)
- Quill
- Migrações com Flyway

## 📊 16. Dados e Streaming

- Apache Spark com Scala
- Kafka com fs2-kafka ou ZIO Kafka
- Pekko Streams

## ☁️ 17. Deploy e Produção

- Empacotamento (`scala package`, sbt-assembly, sbt-native-packager)
- Imagens Docker
- GraalVM Native Image e Scala Native
- CI/CD com GitHub Actions
- Observabilidade com OpenTelemetry

## 🎯 18. Tópicos Avançados

- Macros e metaprogramação no Scala 3
- Derivação de type classes
- Scala.js para o front-end
- Performance na JVM

## 🚀 Próximos Passos - Da Sintaxe à Produção

1. Domine a base do Scala 3: case classes, enums, pattern matching e coleções
2. Trate erros com `Option` e `Either` e escreva testes com MUnit
3. Aprenda os fundamentos de programação funcional e de type classes
4. Construa uma API com http4s ou ZIO HTTP, banco de dados e JSON
5. Empacote com Docker, publique com CI/CD e observe com OpenTelemetry

## 🧠 Dica

> Foque em **projetos reais** ao invés de só teoria.

Sugestões:

- CLI útil para o seu dia a dia
- Processador de arquivos grandes com streams
- API REST funcional com http4s, Doobie e PostgreSQL
- Job de dados com Apache Spark

🔥 **Regra de ouro:**
Aprenda - Aplique - Ensine - Repita
