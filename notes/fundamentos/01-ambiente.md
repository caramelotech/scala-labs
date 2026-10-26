# Configurando o Ambiente

Antes de escrever qualquer código Scala, você precisa de três coisas:

1. **JDK** - Scala roda na JVM, então precisa de um Java instalado
2. **Ferramentas do Scala** - o comando `scala` (Scala CLI) para scripts e projetos pequenos, e o **sbt** para projetos maiores
3. **Editor com suporte a Scala** - para ter autocompletar, erros em tempo real e formatação automática

A forma recomendada de instalar tudo isso de uma vez é o **Coursier**, o instalador oficial do Scala.

## Instalando com o Coursier

O comando `cs setup` instala um JDK (se você ainda não tiver um), o comando `scala`, o `sbt` e outras ferramentas, e configura o `PATH`.

### Windows

1. Baixe o instalador do Coursier pelo link indicado em [scala-lang.org/download](https://www.scala-lang.org/download/)
2. Execute o instalador e responda `Y` quando ele perguntar se deve atualizar o `PATH`
3. Feche e reabra o terminal

### macOS

```bash
brew install coursier
coursier setup
```

### Linux

```bash
curl -fL https://github.com/coursier/coursier/releases/latest/download/cs-x86_64-pc-linux.gz | gzip -d > cs
chmod +x cs
./cs setup
```

Em computadores com processador ARM, troque `x86_64` por `aarch64` no nome do arquivo.

## Verificando a instalação

```bash
java -version
scala version
sbt --version
```

A saída de `scala version` deve ser algo como:

```
Scala CLI version: 1.X.Y
Scala version (default): 3.X.Y
```

Desde o Scala 3.5, o comando `scala` **é** o Scala CLI: a mesma ferramenta compila, executa, testa, formata e empacota código Scala.

## Scala CLI ou sbt?

| Ferramenta    | Quando usar                                                                                          |
| ------------- | ---------------------------------------------------------------------------------------------------- |
| **Scala CLI** | Estudos, scripts, exemplos e projetos pequenos. Sem arquivo de build: a configuração vai no código    |
| **sbt**       | Projetos maiores, com vários módulos e plugins. É a ferramenta de build mais usada no ecossistema    |

Neste lab, os exemplos usam o Scala CLI. Você vai encontrar o sbt (e alternativas como o Mill) quando trabalhar em projetos reais.

## Escolhendo um editor

| Editor               | Como configurar                                                                                                        |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **VS Code**          | Instale a extensão [Scala (Metals)](https://marketplace.visualstudio.com/items?itemName=scalameta.metals)              |
| **IntelliJ IDEA**    | Instale o plugin Scala (disponível também na edição Community)                                                         |
| **Neovim / Vim**     | Configure o Metals pelo cliente LSP de sua preferência                                                                 |

O **Metals** é o language server do Scala. Com o Scala CLI, gere a configuração da IDE na pasta do projeto antes de abrir o editor:

```bash
scala setup-ide .
```

Ative a opção de **formatar ao salvar**: o formatador oficial é o **scalafmt**.

## Primeiro programa

Crie uma pasta `ola-scala` e, dentro dela, um arquivo `ola.scala`:

```scala
//> using scala 3

@main def ola(): Unit =
  println("Olá, Caramelo Tech!")
```

- **`//> using scala 3`** - uma **diretiva** do Scala CLI dizendo qual versão do Scala usar. Dependências também são declaradas assim (`//> using dep ...`).
- **`@main`** - marca a função como ponto de entrada do programa.

Execute:

```bash
scala run .
```

```
Compiling project (Scala 3.X.Y, JVM (21))
Compiled project (Scala 3.X.Y, JVM (21))
Olá, Caramelo Tech!
```

A primeira execução demora mais porque o Scala CLI baixa o compilador e as bibliotecas. As próximas são bem mais rápidas.

## O REPL

O REPL executa cada linha assim que você aperta Enter - ótimo para testar ideias:

```bash
scala repl
```

```
scala> val nome = "Caramelo"
val nome: String = Caramelo

scala> nome.toUpperCase
val res0: String = CARAMELO

scala> :quit
```

## Comandos essenciais do Scala CLI

| Comando              | O que faz                                                      |
| -------------------- | -------------------------------------------------------------- |
| `scala run .`        | Compila e executa o projeto da pasta atual                     |
| `scala compile .`    | Só compila, para verificar erros                               |
| `scala test .`       | Executa os testes (arquivos `*.test.scala`)                    |
| `scala fmt .`        | Formata o código com o scalafmt                                |
| `scala repl`         | Abre o REPL                                                    |
| `scala package .`    | Gera um executável ou um `.jar` do projeto                     |
| `scala setup-ide .`  | Gera a configuração para o Metals ou o IntelliJ                |
| `scala clean .`      | Remove os arquivos gerados na compilação (`.scala-build/`)     |

## Sem instalar nada: Scastie

Para testar um trecho rápido, use o [Scastie](https://scastie.scala-lang.org/), o playground online oficial. Ele roda o código no navegador e permite compartilhar o resultado por link.

## Problemas comuns

### `scala: command not found` ou `'scala' não é reconhecido`

O diretório de binários do Coursier não está no `PATH`. Reabra o terminal depois da instalação; se continuar, rode `cs setup` de novo e confirme a atualização do `PATH`.

### `scala -version` mostra uma versão antiga ou o REPL antigo do Scala 2

Há uma instalação antiga do Scala no sistema (por exemplo, por um gerenciador de pacotes) aparecendo antes no `PATH`. Remova a instalação antiga ou ajuste a ordem do `PATH` para a pasta do Coursier vir primeiro.

### O Metals não reconhece o projeto

Rode `scala setup-ide .` na pasta do projeto e reabra o editor. Para projetos sbt, abra a pasta que contém o `build.sbt` e aceite a importação do build.

## Referências

- [Install Scala - site oficial](https://www.scala-lang.org/download/)
- [Getting Started - Scala Documentation](https://docs.scala-lang.org/getting-started/install-scala.html)
- [Scala CLI - documentação](https://scala-cli.virtuslab.org/)
- [Metals](https://scalameta.org/metals/)
- [sbt - documentação](https://www.scala-sbt.org/)
