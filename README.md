# PayPal-website
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Login - Your Bank</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="login-container">
    <h2>Bank Login</h2>
    <form id="loginForm">
      <label for="username">Username:</label>
      <input type="text" id="username" name="username" required>
      
      <label for="password">Password:</label>
      <input type="password" id="password" name="password" required>
      
      <button type="submit">Login</button>
    </form>
    <div class="error-message" id="errorMessage"></div>
  </div>

/* styles.css */
body {
  font-family: Arial, sans-serif;
  background-color: #f4f4f4;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
}

.login-container {
  background-color: white;
  padding: 20px;
  border-radius: 8px;	




  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  width: 300px;
}

h2 {
  text-align: center;
}

input {
  width: 100%;
  padding: 8px;
  margin: 10px 0;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  width: 100%;
  padding: 10px;
  background-color: #0078d4;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #005bb5;
}

.error-message {
  color: red;
  text-align: center;
  margin-top: 10px;
}


// app.js
document.getElementById('loginForm').addEventListener('submit', function(event) {
  event.preventDefault();

  // Simulate basic login logic (replace with actual API request)
  const username = document.getElementById('username').value;
  const password = document.getElementById('password').value;

  if (username === 'user123' && password === 'password123') {
    alert('Login successful!');
    // Redirect to the dashboard or next page
    window.location.href = 'dashboard.html';
  } else {
    document.getElementById('errorMessage').innerText = 'Invalid username or password';
  }
});

// server.js (Node.js with Express)
const express = require('express');
const bcrypt = require('bcrypt');
const app = express();
const port = 3000;

// Simulated user data (you would store this in a database)
const users = [
  { username: 'user123', passwordHash: '$2b$10$somehashedpasswordvalue' } // Example hashed password
];

app.use(express.json());
app.use(express.static('public')); // Serve static files (HTML, CSS, JS)

// Endpoint to handle login request
app.post('/login', async (req, res) => {
  const { username, password } = req.body;

  const user = users.find(u => u.username === username);
  if (user && await bcrypt.compare(password, user.passwordHash)) {
    res.send({ message: 'Login successful!' });
  } else {
    res.status(401).send({ message: 'Invalid username or password' });
  }
});

app.listen(port, () => {
  console.log(`Server running at http://localhost:${port}`);
});







  <
script src="app.js"></script>
</body>
</html>



