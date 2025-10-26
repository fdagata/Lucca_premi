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

  <script>
    // Elenco premi con link e probabilità (pesi)
    const premi = [
      { nome: "Libro RPG Studies", link: "https://drive.google.com/file/d/1Cru0krkBjbK3ZnaassQQlgXG7U7lYWG9/view?usp=sharing", peso: 1 },
      { nome: "Un Lavoro d'Ufficio - GdR neuroscienze", link: "https://drive.google.com/file/d/15-6_lPFrHq65qMrMQctx-h1pT0uV6lvU/view?usp=sharing", peso: 3 },
      { nome: "Bundle di Scenari per Le Avventure di Lombroso", link: "https://drive.google.com/file/d/1ZUWCLg7rYqHN3oanvd0qJlbYwC8GUHVf/view?usp=sharing", peso: 5 },
      { nome: "Gioco di Carte sull'Open Science", link: "https://drive.google.com/file/d/11Vka_IfIriNlfbtSTuGbGXfHHAv1N4x4/view?usp=sharing", peso: 10 },
      { nome: "Cos'è un GdR, One-scene game", link: "https://drive.google.com/file/d/1Gz_hPWnJMOXZplyc3UCT5j6tIoE-zmzf/view?usp=sharing", peso: 20 }
    ];

    function estraiPremio() {
      let premioSalvato = localStorage.getItem("premioEstratto");
      let linkSalvato = localStorage.getItem("linkPremio");

      if (!premioSalvato) {
        // Calcola somma totale dei pesi
        const pesoTotale = premi.reduce((somma, p) => somma + p.peso, 0);
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
</html>
