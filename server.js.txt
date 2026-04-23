const express = require('express');
const app = express();

app.use(express.json());
app.use(express.static('public'));

let leads = [];

app.get('/leads', (req, res) => {
  res.json(leads);
});

app.post('/leads', (req, res) => {
  const lead = { id: Date.now(), ...req.body };
  leads.push(lead);
  res.json(lead);
});

const PORT = process.env.PORT || 3000;

app.listen(PORT, () => {
  console.log("rodando");
});