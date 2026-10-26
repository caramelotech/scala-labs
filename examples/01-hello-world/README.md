# 01 - Hello World

Este é o programa mais básico em Scala - o famoso "Olá, Mundo!"

## 📝 Sobre

Todo programador começa sua jornada com um programa Hello World. É uma tradição na computação e serve para:

- Verificar se o ambiente de desenvolvimento está configurado
- Entender a estrutura básica de um programa
- Fazer seu primeiro código funcionar!

## 📂 Arquivos

- `hello.scala` - código fonte do programa, com a diretiva que define a versão do Scala

## 🚀 Como Executar

Dentro desta pasta:

### 1. Execute com o Scala CLI

```bash
scala run .
```

A primeira execução baixa o compilador e pode demorar um pouco.

### 2. Ou gere um executável

```bash
scala package . -o hello
```

O comando gera um executável `hello` (que precisa de uma JVM para rodar) na pasta atual.

### 3. Saída Esperada

```
Olá, Mundo!
Bem-vindo ao Scala!
Este é meu primeiro programa.
```

## 🔍 Entendendo o Código

```scala
//> using scala 3
```

- Diretiva do Scala CLI: usa a versão estável mais recente do Scala 3
- Dependências também seriam declaradas aqui, com `//> using dep`

```scala
@main def hello(): Unit =
```

- `@main` - marca a função como ponto de entrada do programa
- `def` - palavra-chave para declarar uma função
- `Unit` - a função não retorna valor útil (equivalente ao `void`)
- `=` - o corpo da função vem a seguir, definido pela indentação

```scala
println("Olá, Mundo!")
```

- `println` - imprime o texto e pula linha

## 💡 Conceitos Importantes

### 1. Indentação no lugar de chaves

No Scala 3, o corpo da função é definido pela indentação. As chaves `{ }` continuam permitidas, mas o estilo novo dispensa.

### 2. Sem ponto e vírgula

O fim da linha encerra a instrução.

### 3. Sem classe obrigatória

Diferente do Java, não é preciso criar uma classe para ter um `main`: uma função com `@main` basta.

## 🎯 Experimente

1. **Mude a mensagem:**

   ```scala
   println("Seu nome aqui!")
   ```

2. **Use interpolação de strings:**

   ```scala
   val nome = "Caramelo"
   println(s"Olá, $nome!")
   ```

3. **Receba um argumento de linha de comando:**

   ```scala
   @main def hello(nome: String): Unit =
     println(s"Olá, $nome!")
   ```

   Execute com `scala run . -- Caramelo`.

## 🔗 Conceitos Relacionados

- [📖 Configurando o Ambiente](../../notes/fundamentos/01-ambiente.md)
- [📖 Introdução ao Scala](../../notes/fundamentos/02-introducao.md)

## ❓ Problemas Comuns

### Erro: "scala: command not found" / "'scala' não é reconhecido"

**Solução:** o Scala não está instalado ou a pasta do Coursier não está no `PATH`.
Veja: [Configurando o Ambiente](../../notes/fundamentos/01-ambiente.md)

### Erro: "No main class found"

**Solução:** confira se a função está anotada com `@main` e se você está executando o comando dentro desta pasta.

### Erro de compilação por indentação

**Solução:** as linhas do corpo da função precisam estar indentadas abaixo do `@main def hello(): Unit =`.

**[⬅️ Voltar aos Exemplos](../README.md)**
