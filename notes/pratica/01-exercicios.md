# Exercícios

Pratique o que aprendeu nos conteúdos e exemplos de código.

## Como usar

1. Leia o enunciado do exercício
2. Tente resolver por conta própria antes de buscar ajuda
3. Revise as notas de [Fundamentos](/labs/scala/fundamentos/01-ambiente/) se precisar relembrar algum conceito
4. Rode `scala fmt .` na sua solução antes de considerar o exercício concluído
5. Compare sua solução com a de outras pessoas da comunidade

## Exercício 01 - Olá, Scala

**Nível:** iniciante

**Objetivo:** Criar e executar o primeiro programa com o Scala CLI.

**Instrução:**

1. Crie uma pasta `ola-scala` com um arquivo `ola.scala`
2. Escreva uma função `@main` que imprima `Olá, Caramelo Tech!`
3. Execute com `scala run .`

**Critérios de sucesso:**

- [ ] O arquivo declara a versão com `//> using scala 3`
- [ ] Usa a sintaxe do Scala 3, sem chaves
- [ ] `scala run .` imprime a mensagem corretamente

## Exercício 02 - Valores e Interpolação

**Nível:** iniciante

**Objetivo:** Declarar valores de diferentes tipos e formatar a saída.

**Instrução:**

1. Declare um `val` com seu nome (`String`), outro com sua idade (`Int`) e outro com sua altura (`Double`)
2. Imprima uma frase combinando os três com interpolação de strings
3. Tente reatribuir um dos `val` e leia a mensagem de erro do compilador

Saída esperada:

```
Meu nome é Ana, tenho 25 anos e meço 1.68m.
```

**Critérios de sucesso:**

- [ ] Usa apenas `val`, sem `var`
- [ ] Usa o interpolador `f` para formatar a altura com duas casas decimais (`$altura%.2f`)
- [ ] Os tipos são inferidos, sem anotação explícita

## Exercício 03 - FizzBuzz

**Nível:** iniciante

**Objetivo:** Praticar ranges, expressões e pattern matching.

**Instrução:**
Imprima os números de 1 a 100. Para múltiplos de 3, imprima `Fizz` no lugar do número; para múltiplos de 5, `Buzz`; para múltiplos de ambos, `FizzBuzz`.

**Critérios de sucesso:**

- [ ] A lógica fica em uma função `fizzbuzz(n: Int): String`
- [ ] Usa `match` sobre a tupla `(n % 3, n % 5)`
- [ ] Gera a saída com `(1 to 100).map(fizzbuzz).foreach(println)`, sem laço com `var`

## Exercício 04 - Divisão Segura

**Nível:** iniciante

**Objetivo:** Representar falhas com tipos em vez de exceções.

**Instrução:**
Crie a função `dividir(a: Double, b: Double): Either[String, Double]` que retorna `Left` com uma mensagem quando `b` for zero e `Right` com o resultado caso contrário. Chame a função com valores válidos e inválidos e trate os dois casos.

**Critérios de sucesso:**

- [ ] A função nunca lança exceção
- [ ] Os dois casos são tratados com `match`
- [ ] Encadeia duas divisões com `for`/`yield` sobre `Either`

## Exercício 05 - Contador de Palavras

**Nível:** intermediário

**Objetivo:** Praticar coleções imutáveis e funções de ordem superior.

**Instrução:**
Escreva a função `contarPalavras(texto: String): Map[String, Int]` que conta quantas vezes cada palavra aparece (ignorando maiúsculas e minúsculas). Imprima as palavras em ordem alfabética com suas contagens.

**Critérios de sucesso:**

- [ ] Usa `split`, `toLowerCase` e `groupMapReduce` (ou `groupBy` + `map`)
- [ ] Não usa `var` nem coleções mutáveis
- [ ] Ordena o resultado com `toList.sortBy` antes de imprimir
- [ ] Tem ao menos um teste com MUnit (arquivo `*.test.scala`) rodando com `scala test .`
