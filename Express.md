# O Que é o Express?

## Introdução

Express é um framework web minimalista e flexível para Node.js. Ele facilita a criação de servidores web. Quando falamos que o Express "cria um servidor web", estamos nos referindo ao fato de que ele fornece uma maneira fácil e rápida de configurar e gerenciar um servidor que pode responder a requisições HTTP.

## Como o Express Cria um Servidor Web

### Criação do Servidor
O Express permite criar um servidor web com apenas algumas linhas de código. Ele usa o módulo HTTP do Node.js por baixo dos panos, mas oferece uma API mais amigável e poderosa.

### Configuração de Rotas
Com o Express, você define rotas que determinam como o servidor deve responder a diferentes URLs e métodos HTTP (GET, POST, etc.). Essas rotas podem responder com dados específicos ou executar funções de backend.

### Uso de Middlewares
Middlewares são funções que processam requisições e respostas. Eles podem ser usados para tarefas como autenticação, validação de dados e logging. O Express facilita a integração de middlewares para adicionar funcionalidades adicionais ao servidor.

### Início do Servidor
O Express simplifica o processo de iniciar o servidor e escutar requisições em uma porta específica. Isso permite que o servidor fique disponível para receber e responder a requisições dos clientes.

## Principais Características

- **Minimalista**: Fornece apenas o essencial para criar servidores web, permitindo adicionar funcionalidades conforme necessário.  
- **Fácil de Usar**: Tem uma API simples e intuitiva, que torna o desenvolvimento rápido e eficiente.  
- **Middlewares**: Funções que processam requisições e respostas, podendo modificar dados ou finalizar o ciclo de requisição-resposta.  
- **Roteamento**: Sistema poderoso para definir rotas e responder a diferentes métodos HTTP (GET, POST, PUT, DELETE).  

## O Papel do Servidor Web e do Banco de Dados

### Servidor Web (Express)
- **Gerencia Requisições e Respostas**: Lida com requisições HTTP dos clientes e envia respostas de volta.  
- **Roteamento**: Define rotas (URLs) e métodos HTTP para determinar como responder a diferentes requisições.

### Banco de Dados
- **Armazena Dados**: Guarda informações como usuários, produtos, pedidos, etc.  
- **Executa Consultas**: Responde a consultas enviadas pelo servidor, como inserir, atualizar ou deletar dados.

## Por Que Iniciar o Servidor Express?

### Estabelecer Conexões com o Banco de Dados
Quando o servidor Express inicia, ele se conecta ao banco de dados para executar operações baseadas nas requisições dos clientes.

### Gerenciar Requisições e Operações de Banco de Dados
1. **Receber Requisições do Cliente**: Por exemplo, um cliente envia um POST para adicionar um novo usuário.  
2. **Interagir com o Banco de Dados**: O servidor executa a consulta SQL correspondente.  
3. **Enviar Resposta ao Cliente**: O servidor confirma que a operação foi realizada com sucesso.

### Exemplo de Fluxo
1. Cliente envia requisição HTTP POST para adicionar um usuário.  
2. Servidor Express recebe a requisição.  
3. Servidor Express conecta ao banco de dados e executa a consulta de inserção.  
4. Banco de dados processa a consulta.  
5. Servidor Express envia resposta ao cliente confirmando a operação.

---

## Exemplo Prático de Servidor Express

### Passo 1: Instalar Dependências
```bash
npm init -y
npm install express
````

### Passo 2: Criar o Arquivo `server.js`

```js
// Importa o Express
const express = require('express');

// Cria uma instância do Express
const app = express();

// Permite que o Express interprete JSON no corpo das requisições
app.use(express.json());

// Define a porta do servidor
const PORT = 3000;

// Rota GET simples
app.get('/', (req, res) => {
  res.send('Olá, mundo!');
});

// Rota POST para adicionar usuário (exemplo com dados fictícios)
app.post('/usuarios', (req, res) => {
  const novoUsuario = req.body; // Dados enviados pelo cliente
  console.log('Novo usuário:', novoUsuario);
  res.status(201).json({ mensagem: 'Usuário adicionado com sucesso!', usuario: novoUsuario });
});

// Inicia o servidor
app.listen(PORT, () => {
  console.log(`Servidor rodando em http://localhost:${PORT}`);
});
```

### Passo 3: Rodar o Servidor

```bash
node server.js
```

Agora você pode testar:

* Acesse `http://localhost:3000` para ver "Olá, mundo!".
* Use uma ferramenta como **Postman** ou **Insomnia** para enviar um POST para `http://localhost:3000/usuarios` com JSON:

```json
{
  "nome": "João",
  "email": "joao@email.com"
}
```

Você verá a resposta confirmando que o usuário foi adicionado.
