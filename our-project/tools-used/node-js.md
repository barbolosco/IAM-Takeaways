# Node js

Node.js is an open-source JavaScript runtime environment that empowers you to create server-side applications, command-line tools, and more. This guide will equip you with the essentials of Node.js on Windows, enabling you to build dynamic and efficient applications.

**Installation (Windows-Specific):**

**Recommended Method: Official Node.js Installer**

1. **Download:** Visit the official Node.js download page ([https://nodejs.org/en/download](https://nodejs.org/en/download)) and choose the **latest LTS (Long-Term Support) version**. LTS versions provide extended security updates, ensuring project stability.
2. **Install:** Double-click the downloaded installer and follow the on-screen instructions. Crucially, **check the option to "Add Node.js to PATH"** during installation. This allows you to execute Node.js commands from any directory in your command prompt or PowerShell.

**Basic Usage and Beyond:**

**1. Hello World (with a Twist):**

Let's start with a simple example that incorporates user interaction:

```javascript
const readline = require('readline').createInterface({
  input: process.stdin,
  output: process.stdout
});

readline.question('What is your name? ', (name) => {
  console.log(`Hello, ${name}!`);
  readline.close();
});
```

* **Module Import:** We import the `readline` module to interact with the user's input.
* **User Input:** The `readline` interface creates an interactive prompt asking for the user's name.
* **Response:** Upon receiving the user's name, the script greets them by name.

**2. Building a Simple HTTP Server:**

Now, let's create a basic HTTP server that responds with dynamic content:

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  const url = req.url; // Get the requested URL
  if (url === '/') {
    res.writeHead(200, { 'Content-Type': 'text/plain' });
    res.end('Welcome to the Node.js server!');
  } else {
    res.writeHead(404, { 'Content-Type': 'text/plain' });
    res.end('404 Not Found');
  }
});

server.listen(3000, () => {
  console.log('Server listening on port 3000');
});
```

* **Handling Requests:** The server checks the requested URL (`req.url`) and responds accordingly.
* **Dynamic Content:** Depending on the URL, the server displays a welcome message or a 404 error.

**Running Node.js Scripts:**

1. **Create a Script:** Save your code in a file with the `.js` extension (e.g., `user_greeting.js` or `http_server.js`).
2. **Open Command Prompt:** Navigate to the directory containing your script using the `cd` command.
3. **Execute Script:** Type the following command and press Enter:

```bash
node user_greeting.js
```

### Introduction to Express.js and nodemon:

#### Express.js:

Express.js is a minimal and flexible Node.js web application framework that provides a robust set of features for building web and mobile applications. It facilitates the creation of powerful APIs and web servers with ease.

#### nodemon:

nodemon is a utility that monitors for changes in your Node.js application and automatically restarts the server when changes are detected. This eliminates the need to manually restart the server every time you make code modifications, thus streamlining the development process.

### Using npm for Package Management:

#### Installing Express.js and nodemon:

Before proceeding, ensure Node.js is installed on your system. Then, use npm (Node Package Manager) to install Express.js and nodemon globally or locally:

```bash
npm install -g express nodemon
```

### Building an Express.js Application:

Let's create a basic Express.js application that serves a simple web page:

1. **Create a directory for your project and navigate into it**:

```bash
mkdir my-express-app
cd my-express-app
```

2. **Initialize a new Node.js project**:

```bash
npm init -y
```

3. **Create a file named `app.js` and add the following code**:

```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello from Express!');
});

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
```

4. **Run the application using nodemon**:

```bash
nodemon app.js
```

### Understanding Modules in Node.js:

#### What are Modules?

In Node.js, modules are reusable blocks of code that encapsulate related functionality. They promote modularization, code organization, and maintainability in Node.js applications.

#### Types of Modules:

1. **Core Modules**: Built-in modules provided by Node.js such as `http`, `fs`, and `path`.
2. **Third-Party Modules**: Modules created by the Node.js community and available via npm, like Express.js and nodemon.
3. **Custom Modules**: Modules created by developers for specific project requirements, aiding in code reuse and maintainability.

#### Importing and Exporting Modules:

* **Importing**: Use the `require()` function to import modules. For example, `const express = require('express');`.
* **Exporting**: Use `module.exports` or `exports` to make functions, objects, or variables available to other modules.

### Further Exploration:

1. **Middleware**: Explore middleware in Express.js to handle requests, authentication, and error handling.
2. **Database Integration**: Learn how to integrate databases like MongoDB or MySQL with Express.js for persistent data storage.
3. **Authentication and Authorization**: Implement authentication and authorization mechanisms using libraries like Passport.js.
4. **RESTful APIs**: Explore building RESTful APIs using Express.js for client-server communication.
5. **Frontend Integration**: Integrate Express.js with frontend frameworks like React or Angular for full-stack development.
