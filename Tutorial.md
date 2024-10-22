# Tutorial: Explorando MongoDB 🍃

Bem-vindo ao tutorial do curso **Explorando MongoDB: Um Guia Prático para Iniciantes**. Aqui você encontrará os principais conceitos e comandos utilizados no MongoDB, conforme apresentados durante as aulas.

## O que é MongoDB? 🤔

MongoDB é um banco de dados orientado a documentos, projetado para facilitar o desenvolvimento e o dimensionamento de aplicativos. Em vez de utilizar tabelas como nos bancos relacionais, o MongoDB armazena dados em documentos JSON-like, permitindo flexibilidade no armazenamento.

- Documentação oficial: [MongoDB Manual](https://www.mongodb.com/pt-br/docs/manual/introduction/)

## Estrutura do MongoDB 🗂️

- **people**: Agrupam documentos semelhantes, análogo às tabelas em bancos relacionais.
- **Document**: Um documento é um registro que contém pares de campo-valor (semelhante a um objeto JSON).

## Comandos CRUD no MongoDB 🔄

### Criando um Banco de Dados 📂

Para criar ou acessar um banco de dados no MongoDB, utilize o comando `use`. Se o banco de dados não existir, ele será criado automaticamente quando você inserir dados.

```bash
use people
```

### Inserindo Documentos 📝

O MongoDB permite inserir documentos em coleções usando os métodos abaixo:

- **Inserir um documento:**
  ```bash
  db.people.insertOne({ name: "Maria", age: 25 })
  ```

- **Inserir múltiplos documentos:**
  ```bash
  db.people.insertMany([{ name: "João", age: 30 }, { name: "Ana", age: 22 }])
  ```

### Pesquisando Documentos 🔍

Para buscar documentos em uma coleção, utilize o método `find()`. Você pode aplicar filtros para refinar os resultados.

- **Buscar todos os documentos:**
  ```bash
  db.people.find()
  ```

- **Buscar com critérios:**
  ```bash
  db.people.find({ age: { $gt: 22 } })
  ```

### Atualizando Documentos ✏️

Para modificar documentos existentes, use os métodos `updateOne()` ou `updateMany()`.

- **Atualizar um documento:**
  ```bash
  db.people.updateOne({ name: "Maria" }, { $set: { age: 56 } })
  ```

- **Atualizar múltiplos documentos:**
  ```bash
  db.people.updateMany({ age: { $lt: 30 } }, { $set: { status: "ativo" } })
  ```

### Deletando Documentos 🗑️

Para remover documentos de uma coleção, utilize os métodos `deleteOne()` ou `deleteMany()`.

- **Deletar um documento:**
  ```bash
  db.people.deleteOne({ name: "João" })
  ```

- **Deletar múltiplos documentos:**
  ```bash
  db.people.deleteMany({ status: "inativo" })
  ```

## Operadores de Consulta e Projeção 🔧

O MongoDB oferece uma vasta gama de operadores para construir consultas complexas. Abaixo estão alguns dos principais operadores:

- **Comparação**: `$eq`, `$ne`, `$gt`, `$lt`, `$gte`, `$lte`
- **Lógica**: `$and`, `$or`, `$not`, `$nor`
- **Elementos**: `$exists`, `$type`
- **Avaliação**: `$regex`, `$expr`, `$mod`, `$text`
- **Arrays**: `$all`, `$elemMatch`, `$size`
- **Projeção**: `$`, `$elemMatch`, `$meta`, `$slice`

Para mais detalhes, consulte a [documentação oficial de operadores do MongoDB](https://www.mongodb.com/pt-br/docs/manual/reference/operator/query/#query-selectors).

## Exemplos Práticos 🔍

Para ver mais exemplos práticos de como aplicar esses operadores de consulta no MongoDB, acesse o arquivo [Examples.md](./Examples.md), onde você poderá praticar consultas com base em uma base de dados simulada.

---

Esse tutorial fornece uma visão geral dos principais comandos usados no curso. Para mais exemplos, explore o [Examples.md](./Examples.md), ou pergunte ao instrutor se tiver dúvidas específicas!