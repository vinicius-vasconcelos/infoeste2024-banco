# Exercícios: Consultas no MongoDB 📝

Prepare-se para aplicar seus conhecimentos sobre MongoDB com exercícios práticos. Siga as instruções para criar uma base de dados, inserir produtos e realizar consultas!

## Criação de Base de Dados 📂

### Exercício 1: Inicie sua jornada com o MongoDB!

Crie a base de dados chamada `myStore` para armazenar informações de produtos.

<details>
<summary>Resposta</summary>

```bash
use myStore
```

</details>

---

### Exercício 2: Adicione produtos à sua coleção!

Crie uma coleção chamada `products` e insira os seguintes produtos:

- **Notebook**: R$ 2500, Categoria: Eletrônicos, Estoque: 10;
- **Smartphone**: R$ 1500, Categoria: Eletrônicos, Estoque: 20;
- **Camiseta**: R$ 50, Categoria: Moda, Estoque: 100;
- **Calça**: R$ 80, Categoria: Moda, Estoque: 50;
- **Fone de Ouvido**: R$ 200, Categoria: Eletrônicos, Estoque: 30;
- **Tênis**: R$ 120, Categoria: Moda, Estoque: 25;
- **Monitor**: R$ 700, Categoria: Eletrônicos, Estoque: 15;

> _Obs. Os campos devem ser em inglês: name(string), price(number), category(string) e stock(number)_

<details>
<summary>Resposta</summary>

```bash
db.products.insertMany([
  { name: "Notebook", price: 2500, category: "eletrônicos", stock: 10 },
  { name: "Smartphone", price: 1500, category: "eletrônicos", stock: 20 },
  { name: "Camiseta", price: 50, category: "moda", stock: 100 },
  { name: "Calça", price: 80, category: "moda", stock: 50 },
  { name: "Fone de Ouvido", price: 200, category: "eletrônicos", stock: 30 },
  { name: "Tênis", price: 120, category: "moda", stock: 25 },
  { name: "Monitor", price: 700, category: "eletrônicos", stock: 15 }
])
```

</details>

## Consultas e Alterações 🔍✏️

### Exercício 3: Recupere todos os produtos da loja!

Realize uma consulta para buscar todos os produtos cadastrados na sua coleção.

<details>
<summary>Resposta</summary>

```bash
db.products.find()
```

</details>

---

### Exercício 4: Mostre os dois primeiros produtos!

Recupere apenas os dois primeiros produtos da sua coleção.

<details>
<summary>Resposta</summary>

```bash
db.products.find().limit(2)
```

</details>

---

### Exercício 5: Ignorar os dois primeiros produtos!

Busque todos os produtos, mas ignore os dois primeiros da lista.

<details>
<summary>Resposta</summary>

```bash
db.products.find().skip(2)
```

</details>

---

### Exercício 6: Mostre apenas o nome dos produtos!

Recupere os produtos, mas exiba apenas os campos `_id` e `name`.

<details>
<summary>Resposta</summary>

```bash
db.products.find({}, { _id: 1, name: 1 })
```

</details>

---

### Exercício 7: Exiba nomes e preços dos produtos!

Recupere os produtos, mostrando apenas os campos `name` e `price`.

<details>
<summary>Resposta</summary>

```bash
db.products.find({}, { _id: 0, name: 1, price: 1 })
```

</details>

---

### Exercício 8: Exiba o nome e o estoque do produto "Monitor"!

Realize uma consulta para mostrar apenas os campos `name` e `stock` do produto cujo nome é "Monitor".

<details>
<summary>Resposta</summary>

```bash
db.products.find(
  { name: { $eq: "Monitor" } },
  { _id: 0, name: 1, stock: 1 }
)
```

</details>

---

### Exercício 9: Busque produtos com preço igual a R$ 50!

Realize uma consulta para encontrar os produtos que possuem o preço exatamente igual a R$ 50.

<details>
<summary>Resposta</summary>

```bash
db.products.find({ price: { $eq: 50 } })
```

</details>

---

### Exercício 10: Busque produtos com preço superior a R$ 100!

Recupere os produtos que têm preço superior a R$ 100.

<details>
<summary>Resposta</summary>

```bash
db.products.find({ price: { $gt: 100 } })
```

</details>

---

### Exercício 11: Busque produtos com estoque baixo!

Encontre os produtos cujo estoque é menor ou igual a 20.

<details>
<summary>Resposta</summary>

```bash
db.products.find({ stock: { $lt: 20 } })
```

</details>

---

### Exercício 12: Busque produtos da categoria Eletrônicos!

Recupere todos os produtos que pertencem à categoria "eletrônicos".

<details>
<summary>Resposta</summary>

```bash
db.products.find({ category: "eletrônicos" })
```

</details>

---

### Exercício 13: Busque produtos da categoria Moda com estoque acima de 50!

Realize uma consulta para encontrar todos os produtos da categoria "moda" que têm estoque maior que 50.

<details>
<summary>Resposta</summary>

```bash
db.products.find({
  $and: [
    { category: "moda" },
    { stock: { $gt: 50 } }
  ]
})
```

</details>



### Exercício 14: Busque produtos com estoque superior a 50 ou preço inferior a R$100!

Realize uma consulta no banco de dados para encontrar produtos que atendam a pelo menos uma das condições.

<details>
<summary>Resposta</summary>

```bash
db.products.find({
  $or: [
    { stock: { $gt: 50 } },
    { price: { $lt: 100 } }
  ]
})
```

</details>

---

### Exercício 15: Altere o preço do Smartphone para R$950!

Realize uma atualização para alterar o preço do produto chamado "Smartphone" para R$950.

<details>
<summary>Resposta</summary>

```bash
db.products.updateOne(
  { name: "Smartphone" },
  { $set: { price: 950 } }
)
```

</details>

---

### Exercício 16: Altere o estoque dos produtos com preço menor ou igual a R$950 para 0!

Atualize o estoque de todos os produtos cujo preço é menor ou igual a R$950, configurando o estoque para 0.

<details>
<summary>Resposta</summary>

```bash
db.products.updateMany(
  { price: { $lte: 950 } },
  { $set: { stock: 0 } }
)
```

</details>

---

### Exercício 17: Exclua produtos com estoque igual a 0!

Realize uma exclusão para remover todos os produtos cujo estoque está igual a 0.

<details>
<summary>Resposta</summary>

```bash
db.products.deleteMany(
  { stock: 0 }
)
```

</details>

---

Esses exercícios cobrem a criação da base de dados, inserção de produtos e várias consultas para solidificar o conhecimento sobre MongoDB. Boa sorte! 🍀