// Raw server.js (No NPM needed!)
const http = require('http'); // Built-in module

const server = http.createServer((req, res) => {
    // req: Incoming request (method, url, headers)
    // res: Outgoing response (write, end)

    if (req.method === 'GET' && req.url === '/') {
        // Manual route check
        res.writeHead(200, { 'Content-Type': 'text/plain' });
        res.end('Hello from Raw Node.js!');
    } else {
        res.writeHead(404, { 'Content-Type': 'text/plain' });
        res.end('Not Found :('); //Basic error
    }
});

const PORT = 3000;

server.listen(PORT, () => {
    console.log(`Raw server running on http://localhost:${PORT}`);
});



EXPRESS CODE


const express = require('express');
const app = express()
const port = 3000

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})


app.use(express.json()); // Parses JSON bodies automatically

app.post("/echo", (req, res) => {
    res.json({ echoed: req.body }); // req.body now available!
});

app.use((req, res, next) => { // Logs every request
    console.log(`${req.method} ${req.url} - ${new Date()}`);
    next(); // Pass to next handler (required!)
});

app.get("/protected", (req, res) => {
    res.send("This was logged!");
});





const express = require('express');
const path = require('path');

const app = express();
const PORT = 3000;

// Serve static files
app.use(express.static(path.join(__dirname, 'public')));

// Serve the main page
app.get('/', (req, res) => {
    res.sendFile(path.join(__dirname, 'views', 'index.html'));
});

app.listen(PORT, () => {
    console.log(`Server running on http://localhost:${PORT}`);
});