<!DOCTYPE html>
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
  <p>Clicca il pulsante qui sotto per estrarre il tuo premio. Ogni partecipante riceve un premio di consolazione!</p>
  <button onclick="estraiPremio()">Estrai!</button>
  <div id="risultato"></div>

  <script>
    function estraiPremio() {
      const r = Math.random();
      let premio = "Premio di Consolazione";
      let link = "https://drive.google.com/uc?id=LINK_CONSOLAZIONE";
      let password = "2415";

      if (r < 0.10) {
        premio = "Premio Rarissimo";
        link = "https://drive.google.com/uc?id=LINK_RARISSIMO";
        password = "9099";
      } else if (r < 0.30) {
        premio = "Premio Raro";
        link = "https://drive.google.com/uc?id=LINK_RARO";
        password = "7234";
      } else if (r < 0.60) {
        premio = "Premio Non Comune";
        link = "https://drive.google.com/uc?id=LINK_NON_COMUNE";
        password = "5176";
      } else if (r < 1.00) {
        premio = "Premio Comune";
        link = "https://drive.google.com/uc?id=LINK_COMUNE";
        password = "3982";
      }

      document.getElementById("risultato").innerHTML =
        `<p><strong>Hai vinto: ${premio}!</strong></p>
         <p>Scarica il tuo premio qui: <a href="${link}" target="_blank">Scarica PDF</a></p>
         <p><em>Password per aprirlo:</em> <strong>${password}</strong></p>`;
    }
  </script>
</body>
</html>

