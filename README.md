# bootcacamp
1º site para bootcamp
      HTML
<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Sono Ideal</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>Sono Ideal 😴</h1>
    <p>Regule seu sono com ciência e simplicidade.</p>
  </header>

  <main>
    <section id="calc">
      <h2>Calculadora de Ciclos de Sono</h2>
      <label for="wake-time">A que horas você precisa acordar?</label>
      <input type="time" id="wake-time">
      <button onclick="calculateSleep()">Calcular hora de dormir</button>
      <div id="results"></div>
    </section>

    <section id="tips">
      <h2>Dicas para dormir melhor</h2>
      <ul>
        <li>Evite telas 1 hora antes de dormir.</li>
        <li>Durma e acorde nos mesmos horários todos os dias.</li>
        <li>Evite cafeína após as 16h.</li>
        <li>Mantenha o quarto escuro e silencioso.</li>
      </ul>
    </section>
  </main>

  <footer>
    <p>© 2025 Sono Ideal. Todos os direitos reservados.</p>
  </footer>

  <script src="script.js"> </script>
</body>
</html>

        CSS
body {
    font-family: Arial, sans-serif;
    background: #f0f4f8;
    color: #333;
    margin: 0;
    padding: 0;
  }
  
  header {
    background: #3b5998;
    color: white;
    padding: 2rem;
    text-align: center;
  }
  
  main {
    padding: 2rem;
    max-width: 800px;
    margin: auto;
  }
  
  section {
    margin-bottom: 2rem;
    background: white;
    padding: 1.5rem;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
  
  button {
    background: #3b5998;
    color: white;
    padding: 0.6rem 1.2rem;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  button:hover {
    background: #2d4373;
  }
  
  footer {
    text-align: center;
    padding: 1rem;
    background: #f1f1f1;
    font-size: 0.9rem;
  }

          JAVASCRIPT
    function calculateSleep() {
    const wakeTimeInput = document.getElementById('wake-time').value;
    const resultDiv = document.getElementById('results');
    
    if (!wakeTimeInput) {
      resultDiv.innerHTML = "<p>Por favor, insira um horário de acordar.</p>";
      return;
    }
  
    const wakeTime = new Date(`1970-01-01T${wakeTimeInput}:00`);
    const sleepCycles = 6; // Cada ciclo = 90 min
    const sleepTimes = [];
  
    for (let i = sleepCycles; i >= 3; i--) {
      const sleepTime = new Date(wakeTime.getTime() - i * 90 * 60000);
      sleepTimes.push(sleepTime.toTimeString().substring(0, 5));
    }
  
    resultDiv.innerHTML = `
      <h3>Para acordar às ${wakeTimeInput}, tente dormir em um destes horários:</h3>
      <ul>${sleepTimes.map(t => `<li>${t}</li>`).join('')}</ul>
    `;
  }
