# Projetos

Mini projetos para aplicar o que foi aprendido de forma integrada.

## Como usar

1. Leia o enunciado do projeto
2. Planeje antes de codificar - modele os dados com case classes e enums antes de escrever a lógica
3. Implemente incrementalmente, compilando com frequência
4. Escreva testes com MUnit para as partes principais antes de avançar

## Projeto 01 - Jogo de Adivinhação

**Nível:** iniciante

**Objetivo:** Construir um jogo interativo no terminal.

**Descrição:**
O programa sorteia um número entre 1 e 100 e pede palpites até a pessoa acertar, dizendo se o palpite foi alto ou baixo.

**Requisitos:**

- [ ] Sorteia o número com `scala.util.Random`
- [ ] Lê os palpites com `scala.io.StdIn.readLine` e converte com `toIntOption`
- [ ] Ignora entradas inválidas sem encerrar o programa
- [ ] Implementa o laço do jogo com uma função recursiva (`@tailrec`), sem `var`
- [ ] Mostra quantas tentativas foram necessárias

**Exemplo de uso:**

```
Adivinhe o número (1 a 100): 50
Muito alto!
Adivinhe o número (1 a 100): 25
Muito baixo!
Adivinhe o número (1 a 100): 37
Acertou em 3 tentativas!
```

## Projeto 02 - Lista de Tarefas (CLI)

**Nível:** intermediário

**Objetivo:** Criar uma ferramenta de linha de comando que persiste dados em arquivo.

**Descrição:**
Construa um gerenciador de tarefas que recebe subcomandos pela linha de comando e salva as tarefas em um arquivo JSON.

**Requisitos:**

- [ ] Subcomandos `add`, `list`, `done` e `remove`, modelados como um `enum` de comandos
- [ ] Tarefas representadas por uma `case class` com `id`, `titulo` e `concluida`
- [ ] Persistência em `tarefas.json` com a biblioteca `upickle` e `os-lib` (declaradas com `//> using dep`)
- [ ] Erros representados com `Either`, sem exceções escapando para o usuário
- [ ] Testes com MUnit para a lógica dos comandos

**Exemplo de uso:**

```
$ scala run . -- add "Estudar pattern matching"
Tarefa 1 adicionada.

$ scala run . -- list
[ ] 1 - Estudar pattern matching

$ scala run . -- done 1
Tarefa 1 concluída.
```

## Projeto 03 - Analisador de Logs

**Nível:** intermediário

**Objetivo:** Processar um arquivo grande de forma funcional.

**Descrição:**
Leia um arquivo de log de servidor web (uma requisição por linha) e gere um relatório com o total de requisições, os status HTTP mais comuns e as 10 rotas mais acessadas.

**Requisitos:**

- [ ] Cada linha é convertida em uma `case class` com um parser que retorna `Option` (linhas inválidas são contadas e ignoradas)
- [ ] O arquivo é lido de forma preguiçosa (`Iterator`), sem carregar tudo na memória
- [ ] Agregações feitas com `groupMapReduce`, `sortBy` e `take`
- [ ] Nenhum `var` ou coleção mutável na lógica de agregação

**Exemplo de entregável:**

```
Total de requisições: 120543 (12 linhas inválidas)

Status:
  200  98211
  404  15022
  500   1310

Rotas mais acessadas:
  /api/produtos   40210
  /api/login      18773
  ...
```

## Projeto 04 - API REST de Livros

**Nível:** avançado

**Objetivo:** Construir uma API HTTP puramente funcional.

**Descrição:**
Crie uma API que permite cadastrar, listar, buscar e remover livros, guardando os dados em memória.

**Requisitos:**

- [ ] Servidor com `http4s` sobre o Cats Effect (ou com Tapir)
- [ ] Rotas `GET /livros`, `GET /livros/{id}`, `POST /livros` e `DELETE /livros/{id}`
- [ ] JSON com `circe`
- [ ] Estado compartilhado com `Ref` do Cats Effect
- [ ] Códigos de status corretos (`200`, `201`, `204`, `400`, `404`)
- [ ] Testes das rotas com MUnit e `munit-cats-effect`

**Exemplo de entregável:**

```
$ curl -X POST localhost:8080/livros -H 'Content-Type: application/json' \
    -d '{"titulo":"Programming in Scala","autor":"Martin Odersky"}'
{"id":1,"titulo":"Programming in Scala","autor":"Martin Odersky"}
```
