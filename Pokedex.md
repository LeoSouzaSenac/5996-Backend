# 📘 Projeto: Consumindo a PokeAPI (Pokédex)

Este material explica **passo a passo** como criar um projeto que consuma a **PokeAPI**, utilizando **dados e imagens oficiais da Pokédex**, de forma simples e didática para iniciantes.

O objetivo é que o aluno entenda:

* O que é uma API
* Como funcionam requisições HTTP
* Como consumir dados JSON
* Como usar imagens oficiais dos Pokémon
* Quais são as **regras da PokeAPI**

---

## 1️⃣ O que é a PokeAPI

A **PokeAPI** é uma API pública e gratuita que fornece informações sobre Pokémon, como:

* Nome
* Número (ID)
* Tipos
* Habilidades
* Status
* Imagens oficiais

📌 Site oficial:
[https://pokeapi.co](https://pokeapi.co)

Ela **não exige login, token ou chave de API**.

---

## 2️⃣ O que é uma API

Uma **API** é um endereço da internet que:

* Recebe um pedido (request)
* Retorna dados (response)

Esses dados vêm normalmente em **JSON**.

Exemplo de pedido:

```
https://pokeapi.co/api/v2/pokemon/1
```

Resposta (simplificada):

```json
{
  "id": 1,
  "name": "bulbasaur",
  "types": [...],
  "sprites": {...}
}
```

---

## 3️⃣ Estrutura base de um projeto simples

Você pode usar **HTML + CSS + JavaScript puro** ou React.

### 📥 O que baixar antes

* **Visual Studio Code** (editor de código):
  [https://code.visualstudio.com/](https://code.visualstudio.com/)

* **Google Chrome** (ou outro navegador moderno):
  [https://www.google.com/chrome/](https://www.google.com/chrome/)

* **Node.js** (opcional, mas recomendado):
  [https://nodejs.org/](https://nodejs.org/)

> Para projetos simples em HTML + JS, o navegador já é suficiente.

---

Estrutura mínima do projeto:

```
projeto-pokedex/
│
├── index.html
├── style.css
└── script.js
```

projeto-pokedex/
│
├── index.html
├── style.css
└── script.js

```

---

## 4️⃣ Endpoints da PokeAPI

Um **endpoint** é apenas um endereço da API que serve para um propósito específico.

A PokeAPI usa apenas **requisições GET** (somente leitura de dados).

---

### 🔹 Endpoint: Pokémon individual

📌 Para buscar **um Pokémon específico** pelo nome ou número.

URL base:
```

[https://pokeapi.co/api/v2/pokemon/{id-ou-nome}](https://pokeapi.co/api/v2/pokemon/{id-ou-nome})

```

Exemplos:
```

[https://pokeapi.co/api/v2/pokemon/1](https://pokeapi.co/api/v2/pokemon/1)
[https://pokeapi.co/api/v2/pokemon/pikachu](https://pokeapi.co/api/v2/pokemon/pikachu)

```

O que esse endpoint retorna:
- ID (número da Pokédex)
- Nome
- Tipos
- Habilidades
- Status
- Sprites (imagens)

---

### 🔹 Endpoint: Lista de Pokémon

📌 Para buscar **vários Pokémon de uma vez**.

```

[https://pokeapi.co/api/v2/pokemon?limit=20&offset=0](https://pokeapi.co/api/v2/pokemon?limit=20&offset=0)

```

Parâmetros:
- `limit`: quantos Pokémon retornar
- `offset`: a partir de qual Pokémon começar

Exemplo prático:
- `limit=10&offset=0` → primeiros 10 Pokémon
- `limit=10&offset=10` → próximos 10 Pokémon

---

### 🔹 Endpoint: Tipos

📌 Para buscar **tipos de Pokémon** (fire, water, grass, etc).

```

[https://pokeapi.co/api/v2/type](https://pokeapi.co/api/v2/type)

```

Ou um tipo específico:
```

[https://pokeapi.co/api/v2/type/fire](https://pokeapi.co/api/v2/type/fire)

```

---

### 🔹 Endpoint: Habilidades

📌 Para buscar habilidades.

```

[https://pokeapi.co/api/v2/ability/{id-ou-nome}](https://pokeapi.co/api/v2/ability/{id-ou-nome})

````

---

## 5️⃣ Como enviar requisições (regras da API)

### ✔ Método HTTP usado

A PokeAPI usa **APENAS GET**.

❌ Não existe POST, PUT ou DELETE.

---

### ✔ Forma correta de requisição

Sempre usando `fetch` com **async / await**.

```javascript
async function buscarPokemon(nome) {
  const resposta = await fetch(`https://pokeapi.co/api/v2/pokemon/${nome}`)
  const dados = await resposta.json()
  return dados
}
````

---

### ✔ Quantidade de requisições

Regras simples para alunos:

* Uma requisição por ação do usuário
* Não usar loops infinitos
* Não ficar recarregando dados automaticamente

---

### 🔹 Lista de Pokémon

```
https://pokeapi.co/api/v2/pokemon?limit=20&offset=0
```

* `limit`: quantos Pokémon carregar
* `offset`: de onde começar

---

## 6️⃣ Regras da PokeAPI

### ✅ O que a API permite

* Uso gratuito
* Sem autenticação
* Uso educacional
* Uso das imagens oficiais

### ❌ O que NÃO fazer

* Spam de requisições
* Atualizações automáticas constantes
* Uso comercial pesado sem cuidado

📌 Regra de ouro:

> Requisição só quando o usuário pedir.

---

## 6️⃣ Como fazer uma requisição (fetch com async / await)

Usaremos **async / await**, que é mais legível e moderno.

No `script.js`:

```javascript
async function buscarPokemon() {
  try {
    const resposta = await fetch('https://pokeapi.co/api/v2/pokemon/pikachu')
    const dados = await resposta.json()
    console.log(dados)
  } catch (erro) {
    console.error('Erro ao buscar o Pokémon:', erro)
  }
}
````

---

## 7️⃣ Principais dados que vamos usar

### 🔹 Nome

```javascript
dados.name
```

### 🔹 ID (número da Pokédex)

```javascript
dados.id
```

### 🔹 Tipos

```javascript
dados.types
```

### 🔹 Imagens oficiais

A PokeAPI fornece **sprites** (imagens).

A melhor imagem (oficial da Pokédex):

```javascript
dados.sprites.other['official-artwork'].front_default
```

ou

```javascript
dados.sprites.versions['generation-v']['black-white'].animated.front_default; // sprites animados
```

📌 Essa é a imagem grande usada na Pokédex moderna.

---

## 8️⃣ Exemplo: montar um Pokémon na tela

````javascript
async function mostrarPokemon(nome) {
  const resposta = await fetch(`https://pokeapi.co/api/v2/pokemon/${nome}`)
  const dados = await resposta.json()

  const nomePokemon = dados.name
  const imagem = dados.sprites.other['official-artwork'].front_default

  pokemonDiv.innerHTML = `
    <h2>${nomePokemon}</h2>
    <img src="${imagem}" />
  `
}

mostrarPokemon('bulbasaur')
```javascript
const nome = dados.name
const imagem = dados.sprites.other['official-artwork'].front_default

pokemonDiv.innerHTML = `
  <h2>${nome}</h2>
  <img src="${imagem}" />
`
````

---

## 9️⃣ Trabalhando com tipos

```javascript
dados.types.forEach(tipo => {
  console.log(tipo.type.name)
})
```

Tipos vêm em inglês:

* fire
* water
* grass
* electric

---

## 🔟 Criando uma Pokédex simples

Fluxo básico:

1. Usuário digita nome ou número
2. Você monta a URL
3. Faz `fetch`
4. Mostra nome, imagem e tipos

---

## 1️⃣1️⃣ Tratando erros

Sempre trate erros para evitar quebrar a aplicação.

````javascript
async function buscarPokemon(nome) {
  try {
    const resposta = await fetch(`https://pokeapi.co/api/v2/pokemon/${nome}`)

    if (!resposta.ok) {
      throw new Error('Pokémon não encontrado')
    }

    const dados = await resposta.json()
    console.log(dados)

  } catch (erro) {
    alert(erro.message)
  }
}
```javascript
if (!resposta.ok) {
  alert('Pokémon não encontrado')
}
````

---

## 1️⃣2️⃣ Boas práticas para alunos

* Não copiar e colar sem entender
* Sempre usar `console.log(dados)`
* Fazer testes com diferentes Pokémon
* Respeitar a API (não abusar)

---

## 1️⃣3️⃣ Ideias de exercícios

1. Buscar Pokémon pelo nome
2. Buscar Pokémon pelo número
3. Mostrar mais de um Pokémon
4. Criar lista com 10 Pokémon
5. Colorir o card conforme o tipo
6. Criar botão "Próximo" e "Anterior"

---

## 1️⃣4️⃣ Resumo final

* A PokeAPI é gratuita e aberta
* Usa HTTP + JSON
* Fornece dados e imagens oficiais
* Ideal para aprender consumo de API

Este projeto ensina **API, fetch, JSON, DOM e boas práticas** de forma prática e divertida.
