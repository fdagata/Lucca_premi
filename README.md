<html lang="it">
<head>
  <meta charset="UTF-8">
  <title>Estrazione Premio</title>
  <style>
    body { font-family: sans-serif; text-align: center; padding-top: 50px; background: #f7f7f7; }    
    h1 { color: #333; }
    a {
      display: inline-block;
      margin-top: 20px;
      padding: 10px 20px;
      background: #007bff;
      color: white;
      text-decoration: none;
      border-radius: 8px;
      transition: background 0.3s;
    }
    a:hover { background: #0056b3; }
    button {
      padding: 10px 20px;
      border: none;
      border-radius: 8px;
      background: #28a745;
      color: white;
      cursor: pointer;
      font-size: 16px;
    }
    button:hover { background: #218838; }
  </style>
</head>
<body>
  <h1 id="titolo">🎁 Scopri il tuo premio!</h1>
  <p>Clicca il pulsante qui sotto per estrarre il tuo premio.</p>
  <div id="output"></div>
  <button id="bottone" onclick="estraiPremio()">Estrai Premio</button>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br> 
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br> 
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <script>
    // Elenco premi con link e probabilità (pesi)
    const premi = [
      { nome: "Capitan Avis - Premio super raro, fino ad esaurimento scorte. Ritira il tuo premio all'info point con presentando il pdf.", link: "https://drive.google.com/file/d/16V2DO7Au9V7fpGMY_v-gGKsMnXHhCIsV/view?usp=sharing", peso: 5 },
      { nome: "Playa Pirata - Premio super raro, fino ad esaurimento scorte. Ritira il tuo premio all'info point con presentando il pdf.", link: "https://drive.google.com/file/d/1hITJHwMFqpJo09r2G6gD20w2zrQnJAbv/view?usp=sharing", peso: 5 },
      { nome: "Un Lavoro d'Ufficio GdR neuroscienze - Premio raro", link: "[https://drive.google.com/file/d/1ZUWCLg7rYqHN3oanvd0qJlbYwC8GUHVf/view?usp=sharing](https://drive.google.com/file/d/15-6_lPFrHq65qMrMQctx-h1pT0uV6lvU/view?usp=sharing)", peso: 10 },
      { nome: "Gioco di Carte sull'Open Science - Premio non comune", link: "https://drive.google.com/file/d/11Vka_IfIriNlfbtSTuGbGXfHHAv1N4x4/view?usp=sharing", peso: 30 },
      { nome: "Cos'è un GdR, One-scene game - Premio comune", link: "https://drive.google.com/file/d/1aPhoaUZS7IYW4lsg3W7fWsllQFMwd0ai/view?usp=sharing", peso: 50 }
    ]; 

    function estraiPremio() {
      let premioSalvato = localStorage.getItem("premioEstratto");
      let linkSalvato = localStorage.getItem("linkPremio");

      if (!premioSalvato) {
        // Calcola somma totale dei pesi
        const pesoTotale = 100;
        let casuale = Math.random() * pesoTotale;
        let premioEstratto;

        for (const premio of premi) {
          if (casuale < premio.peso) {
            premioEstratto = premio;
            break;
          }
          casuale -= premio.peso;
        }

        premioSalvato = premioEstratto.nome;
        linkSalvato = premioEstratto.link;

        // Salva nel browser
        localStorage.setItem("premioEstratto", premioSalvato);
        localStorage.setItem("linkPremio", linkSalvato);
      }

      // Mostra risultato
      document.getElementById("titolo").textContent = "Hai vinto: " + premioSalvato;
      document.getElementById("output").innerHTML =
        `<a href="${linkSalvato}">Vai al tuo premio 🎁</a>`;
      document.getElementById("bottone").style.display = "none";
    }

    // Se già estratto, mostra direttamente
    if (localStorage.getItem("premioEstratto")) estraiPremio();
  </script>
</body>
<footer class="custom-footer">
  <p><span style="font-weight: 310;">Copyright © 2025</span></p>
</footer>
<style>
  footer:not(.custom-footer) {
    display: none;
  }
</style>
</html>
