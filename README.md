<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Feliz Aniversário!</title>
    
    {{stander_hearder_includes}}

    <style>
        body { font-family: 'Arial', sans-serif; background-color: #f0f8ff; text-align: center; padding: 20px; display: flex; flex-direction: column; align-items: center; justify-content: center; min-height: 100vh; margin: 0; }
        .container { background: white; padding: 25px; border-radius: 15px; box-shadow: 0 4px 15px rgba(0,0,0,0.2); max-width: 400px; width: 100%; margin-bottom: 20px; }
        h1 { color: #ff6b6b; }
        p { font-size: 1.1em; color: #333; line-height: 1.6; }
        input { width: 80%; padding: 10px; margin: 10px 0; border: 2px solid #ddd; border-radius: 5px; font-size: 16px; }
        button { background-color: #4CAF50; color: white; padding: 12px 24px; border: none; border-radius: 5px; font-size: 16px; cursor: pointer; margin-top: 15px; width: 100%; }
        button:hover { background-color: #45a049; }
        .hidden { display: none; }
        .error { color: red; font-size: 0.9em; margin-top: 5px; display: none; }
        .confetti { font-size: 50px; }
    </style>
</head>
<body>

    <div id="welcome-screen" class="container">
        <div class="confetti">🙌🏽🎂🍰🎈</div>
        <h1>Feliz aniversário</h1>
        <p>Esse é o seu presente de aniversário. Antes, preciso que responda as perguntas abaixo.</p>
        <button onclick="showScreen('quiz-screen')">Começar Desafio</button>
    </div>

    <div id="quiz-screen" class="container hidden">
        <h3>Pergunta 1:</h3>
        <p>Quanto é 1 + 1?</p>
        <input type="number" id="q1" placeholder="Sua resposta">

        <h3>Pergunta 2:</h3>
        <p>Quanto é 10 x 10?</p>
        <input type="number" id="q2" placeholder="Sua resposta">

        <h3>Pergunta 3:</h3>
        <p>Quem é o amor do Jhon?</p>
        <input type="text" id="q3" placeholder="Nome">

        <p id="quiz-error" class="error">Ops! Alguma resposta está errada.</p>
        <button onclick="checkQuiz()">Verificar Respostas</button>
    </div>

    <div id="clue-screen" class="container hidden">
        <h1>Perfeito! 👏</h1>
        <p>A senha está em um retrato como um soldado de cabeça de papel.</p>
        <p><strong>Peça a senha:</strong></p>
        <input type="number" id="password-input" placeholder="Digite a senha aqui">
        
        <p id="pass-error" class="error">Senha incorreta!</p>
        <button onclick="checkPassword()">Destravar Presente</button>
    </div>

    <div id="final-screen" class="container hidden">
        <div class="confetti">🎁✨🗺️</div>
        <h1>Parabéns!</h1>
        <p style="font-weight: bold; background-color: #e8f5e9; padding: 15px; border-radius: 10px;">
            "Seu presente está perto onde há vários cheiros e conhecimento guardado e não usado. 
            Ao lado existe uma proteção de guia, alguém fica atiçada quando ouve a palavra, mas quanto mais conhecimento você procurar mais perto do presente estará."
        </p>
    </div>

    <script>
        function showScreen(screenId) {
            document.querySelectorAll('.container').forEach(div => div.classList.add('hidden'));
            document.getElementById(screenId).classList.remove('hidden');
        }
        function checkQuiz() {
            const a1 = document.getElementById('q1').value.trim();
            const a2 = document.getElementById('q2').value.trim();
            const a3 = document.getElementById('q3').value.trim().toLowerCase();
            if (a1 === "2" && a2 === "100" && (a3.includes("andré") || a3.includes("andre"))) {
                showScreen('clue-screen');
            } else { document.getElementById('quiz-error').style.display = 'block'; }
        }
        function checkPassword() {
            if (document.getElementById('password-input').value.trim() === "4523") {
                showScreen('final-screen');
            } else { document.getElementById('pass-error').style.display = 'block'; }
        }
    </script>

    {{footer_includes}}
</body>
</html>
