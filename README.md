<html lang="it">
<head>
  <meta charset="UTF-8">
  <title>Estrai il tuo premio!</title>
  <style>
    body { font-family: "Trebuchet MS", sans-serif; text-align: center; padding-top: 80px; background: #fafafa; }
    button { padding: 12px 25px; font-size: 1.2em; border-radius: 8px; cursor: pointer; }
    #risultato { margin-top: 25px; font-size: 1.1em; }
  </style>
</head>
<body>
  <h1>🎁 Scopri il tuo premio!</h1>
  <p>Clicca il pulsante qui sotto per estrarre il tuo premio.</p>
   <button onclick="estraiPremio()">Estrai!</button>
  <div id="risultato"></div>

  <script>
    function estraiPremio() {
      const r = Math.random();      

      if (r < 0.10) {
        premio = "Premio Rarissimo";
        link = "https://drive.google.com/uc?id=LINK_RARISSIMO";
        
      } else if (r < 0.30) {
        premio = "Premio Raro";
        link = "https://drive.google.com/uc?id=LINK_RARO";
        
      } else if (r < 0.60) {
        premio = "Premio Non Comune";
        link = "https://drive.google.com/uc?id=LINK_NON_COMUNE";
        
      } else if (r < 1.00) {
        premio = "Premio di Consolazione";
        link = "https://drive.google.com/uc?id=LINK_COMUNE";
        
        premioSalvato = premio;
        linkSalvato = link;

        // Salva nel browser
        localStorage.setItem("premioEstratto", premioSalvato);
        localStorage.setItem("linkPremio", linkSalvato);
      }

      document.getElementById("risultato").innerHTML =
        `<p><strong>Hai vinto: ${premio}!</strong></p>
         <p>Scarica il tuo premio qui: <a href="${link}" target="_blank">Scarica PDF</a></p>         
    }
  </script>
</body>
</html>

