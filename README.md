# my_api
A Simple REST API built with Express.js in Node.js
const express = require('express');
const cors = require('cors');
const app = express();
const PORT = 3000;

app.use(cors());
app.use(express.json());

let teams = [
  { id: 1, name: "تیم A", owner: "فەرهاد", location: "هەولێر" }
];
let players = [
  { id: 1, name: "یاریزان A", number: 10, pos: "dmf", teamId: 1 }
];

app.get('/teams', (req, res) => {
  res.json(teams);
});

app.post('/teams', (req, res) => {
  const { name, owner, location } = req.body;
  const newTeam = { id: Date.now(), name, owner, location };
  teams.push(newTeam);
  res.json({ success: true, team: newTeam });
});

app.get('/players', (req, res) => {
  res.json(players);
});

app.post('/players', (req, res) => {
  const { name, number, pos, teamId } = req.body;
  const newPlayer = { id: Date.now(), name, number, pos, teamId };
  players.push(newPlayer);
  res.json({ success: true, player: newPlayer });
});

app.listen(PORT, () => console.log(`✅ API server running at http://localhost:${PORT}`));
