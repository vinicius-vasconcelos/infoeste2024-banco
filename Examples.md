# Exemplos: Consultas no MongoDB 🔍

Neste arquivo, você encontrará exemplos progressivos para praticar consultas no MongoDB. Para mais exemplos, consulte a [documentação oficial do MongoDB](https://www.mongodb.com/pt-br/docs/manual/reference/operator/query/#query-selectors).

## Criando a Base de Dados e Inserindo Dados 📂

### Criando a base de dados `onlineStore`

```bash
use onlineStore
```

### Inserindo documentos na coleção `customers`

```bash
db.customers.insertMany([
  { name: "Maria", age: 28, city: "São Paulo", purchases: 5, status: "ativo", interests: ["eletrônicos", "moda"] },
  { name: "João", age: 35, city: "Rio de Janeiro", purchases: 2, status: "inativo", interests: ["livros", "esportes"] },
  { name: "Ana", age: 22, city: "Curitiba", purchases: 12, status: "ativo", interests: ["moda", "beleza"] },
  { name: "Carlos", age: 40, city: "São Paulo", purchases: 8, status: "ativo", interests: ["tecnologia", "esportes"] },
  { name: "Lucas", age: 30, city: "Brasília", purchases: 3, status: "inativo", interests: ["eletrônicos", "livros"] },
  { name: "Fernanda", age: 26, city: "Salvador", purchases: 6, status: "inativa", interests: ["viagem", "moda"] },
  { name: "Pedro", age: 29, city: "Recife", purchases: 10, status: "ativo", interests: ["viagem", "esportes"] },
  { name: "Roberta", age: 31, city: "São Paulo", purchases: 4, status: "inativo", interests: ["beleza", "moda"] }
])
```

---

## Operadores Básicos 🔧

### 1. Buscar documentos com pessoas com idade igual a 28 usando `$eq`:

```bash
db.customers.find({ age: { $eq: 28 } })
```

### 2. Buscar documentos com pessoas que tiveram compras maiores que 5 usando `$gt`:

```bash
db.customers.find({ purchases: { $gt: 5 } })
```

### 3. Buscar documentos com pessoas com idade maior ou igual a 30 usando `$gte`:

```bash
db.customers.find({ age: { $gte: 30 } })
```

### 4. Buscar documentos com pessoas que tiveram menos de 5 compras usando `$lt`:

```bash
db.customers.find({ purchases: { $lt: 5 } })
```

### 5. Buscar documentos com pessoas com idade menor ou igual a 25 usando `$lte`:

```bash
db.customers.find({ age: { $lte: 26 } })
```

---

## Consultas com Operadores Lógicos 🔍

### 6. Combinar condições para buscar clientes ativos com mais de 5 compras usando `$and`:

```bash
db.customers.find({ $and: [ { status: "ativo" }, { purchases: { $gt: 5 } } ] })
```

### 7. Combinar condições para buscar clientes que moram em São Paulo ou no Rio de Janeiro usando `$or`:

```bash
db.customers.find({ $or: [ { city: "São Paulo" }, { city: "Rio de Janeiro" } ] })
```

### 8. Buscar documentos de clientes que têm interesses em moda e beleza usando `$all`:

```bash
db.customers.find({ interests: { $all: ["moda", "beleza"] } })
```

### 9. Consultar clientes que têm "esportes" entre seus interesses usando `$elemMatch`:

```bash
db.customers.find({ interests: { $elemMatch: { $eq: "esportes" } } })
```

---

## Limitar Resultados 🚦

### 10. Limitar a quantidade de resultados a 3 clientes usando `limit()`:

```bash
db.customers.find().limit(3)
```

### 11. Pular os dois primeiros clientes e retornar os próximos 3 usando `skip()` e `limit()`:

```bash
db.customers.find().skip(2).limit(3)
```

---

## Projeções 🎯

### 12. Projeção para incluir apenas os campos nome e cidade dos clientes:

```bash
db.customers.find({}, { name: 1, city: 1, _id: 0 })
```

### 13. Projeção para excluir o campo idade dos clientes:

```bash
db.customers.find({}, { age: 0 })
```

### 14. Projeção com filtro para incluir apenas clientes ativos e mostrar nome e compras:

```bash
db.customers.find({ status: "ativo" }, { name: 1, purchases: 1, _id: 0 })
```

---

## Exercícios 📝

Agora é a sua vez de praticar! 🚀

Para testar seus conhecimentos, confira o arquivo [Exercise.md](Exercise.md) para exercícios práticos.

---

Esses exemplos te ajudarão a praticar e entender progressivamente as consultas no MongoDB. À medida que você avança, pode adicionar mais complexidade às suas buscas ou explorar novos operadores na [documentação oficial do MongoDB](https://www.mongodb.com/pt-br/docs/manual/reference/operator/query/#query-selectors).
