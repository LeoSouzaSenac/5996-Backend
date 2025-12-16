# 📘 ATIVIDADE – CRUD de Pokémons (Node.js + MySQL + Front-end)

## 👥 Organização

* A atividade pode ser feita **em duplas**
* Todos os integrantes devem entender e conseguir explicar o código

---

## 🎯 OBJETIVO

Criar uma **API** do zero utilizando **Node.js + Express**, conectada a um banco de dados, permitindo o **cadastro, leitura, atualização e exclusão de Pokémons**.
Após isso, desenvolver um **front-end simples** para consumir essa API.

---

## 🧩 PARTE 1 – BACK-END (Servidor)

### 📌 O que deve ser feito

1. Criar um projeto Node.js do zero
2. Instalar as bibliotecas necessárias
3. Criar um servidor usando Express
4. Conectar o servidor a um banco de dados MySQL
5. Criar rotas para:

   * Criar um pokémon
   * Listar todos os pokémons
   * Buscar um pokémon por ID
   * Atualizar um pokémon
   * Deletar um pokémon
6. Testar todas as rotas utilizando o **Thunder Client**

---

### 📦 Bibliotecas obrigatórias

* express
* mysql2
* cors

---

### 📂 Estrutura mínima do projeto

```
pokemon-api
├── node_modules
├── package.json
└── src/server.js
```

---

### 🚀 Inicialização do projeto (comandos)

```bash
npm init -y
npm install express mysql2 cors
```

---

## 🔀 ROTAS OBRIGATÓRIAS

```js
// Criar um pokémon
app.post("/pokemons", (req, res) => {

});
```

```js
// Listar todos os pokémons
app.get("/pokemons", (req, res) => {
  // sua lógica aqui
});
```

```js
// Buscar um pokémon por ID
app.get("/pokemons/:id", (req, res) => {
  // sua lógica aqui
});
```

```js
// Atualizar um pokémon
app.put("/pokemons/:id", (req, res) => {
  // sua lógica aqui
});
```

```js
// Deletar um pokémon
app.delete("/pokemons/:id", (req, res) => {
  // sua lógica aqui
});
```

---

## 🧪 Testes obrigatórios

Cada rota deve ser testada no **Thunder Client**, utilizando o método HTTP correto:

| Ação          | Método |
| ------------- | ------ |
| Criar         | POST   |
| Listar        | GET    |
| Buscar por ID | GET    |
| Atualizar     | PUT    |
| Deletar       | DELETE |

---

## 🌐 PARTE 2 – FRONT-END

### 📌 O que deve ser feito

Criar uma interface simples em **HTML + JavaScript** que consuma a API criada.

O sistema deve permitir:

* Cadastrar novos pokémons
* Listar os pokémons cadastrados
* Deletar pokémons
* (Opcional) Atualizar informações de um pokémon

---

### 📂 Estrutura mínima do front-end

```
frontend
├── index.html
└── script.js
```

---

### 🌍 URL da API

```js
const API_URL = "http://localhost:3000";
```

---

### 🔁 Chamadas à API (somente estrutura)

```js
// Criar pokémon
fetch(`${API_URL}/pokemons`, {
  method: "POST"
});
```

```js
// Listar pokémons
fetch(`${API_URL}/pokemons`);
```

```js
// Deletar pokémon
fetch(`${API_URL}/pokemons/id`, {
  method: "DELETE"
});
```

```js
// Atualizar pokémon
fetch(`${API_URL}/pokemons/id`, {
  method: "PUT"
});
```
