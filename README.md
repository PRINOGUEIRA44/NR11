<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz NR11</title>
    <script>
        let perguntas = [
            { pergunta: "Qual é o principal objetivo da NR11?", opcoes: ["Regular a jornada de trabalho dos operadores de empilhadeira.", "Estabelecer normas de segurança para o transporte, movimentação, armazenagem e manuseio de materiais.", "Definir regras para a organização de estoques.", "Determinar as sanções para empresas que descumprem normas trabalhistas."], resposta: 1 },
            { pergunta: "Qual equipamento exige habilitação específica para operação?", opcoes: ["Carrinho de mão.", "Paleteira manual.", "Empilhadeira.", "Prateleira deslizante."], resposta: 2 },
            { pergunta: "Qual é uma medida essencial para garantir a segurança na movimentação de materiais?", opcoes: ["Movimentar cargas sem avaliação prévia.", "Utilizar EPIs adequados e inspecionar os equipamentos antes do uso.", "Empilhar caixas de qualquer forma para otimizar espaço.", "Permitir que qualquer colaborador opere equipamentos sem treinamento."], resposta: 1 },
            { pergunta: "Como deve ser realizado o empilhamento seguro de materiais?", opcoes: ["Sem limite de altura, desde que bem equilibrado.", "De forma a respeitar os limites de peso e altura estabelecidos.", "Misturando diferentes tipos de materiais para ganhar espaço.", "Apenas com empilhadeiras automáticas."], resposta: 1 },
            { pergunta: "Qual dessas situações representa um risco no armazenamento de materiais?", opcoes: ["Utilizar sinalização adequada para corredores e áreas de carga.", "Manter a ordem e limpeza do local de armazenagem.", "Empilhar cargas de maneira irregular e sem fixação.", "Segregar materiais perigosos conforme normas específicas."], resposta: 2 }
        ];

        let index = 0;
        let score = 0;
        let startTime, endTime;

        function iniciarQuiz() {
            document.getElementById("inicio").style.display = "none";
            document.getElementById("quiz").style.display = "block";
            startTime = new Date();
            carregarPergunta();
        }

        function carregarPergunta() {
            if (index < perguntas.length) {
                let q = perguntas[index];
                document.getElementById("pergunta").innerText = q.pergunta;
                let opcoesHtml = "";
                q.opcoes.forEach((op, i) => {
                    opcoesHtml += `<button onclick="verificarResposta(${i})">${op}</button><br>`;
                });
                document.getElementById("opcoes").innerHTML = opcoesHtml;
            } else {
                finalizarQuiz();
            }
        }

        function verificarResposta(opcao) {
            if (opcao === perguntas[index].resposta) {
                score++;
            }
            index++;
            carregarPergunta();
        }

        function finalizarQuiz() {
            endTime = new Date();
            let tempoGasto = (endTime - startTime) / 1000;
            document.getElementById("quiz").style.display = "none";
            document.getElementById("resultado").style.display = "block";
            document.getElementById("pontuacao").innerText = `Você acertou ${score} de ${perguntas.length} perguntas.`;
            document.getElementById("tempo").innerText = `Tempo: ${tempoGasto.toFixed(2)} segundos.`;
        }
    </script>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; }
        button { margin: 10px; padding: 10px; cursor: pointer; }
    </style>
</head>
<body>
    <div id="inicio">
        <h1>Quiz NR11</h1>
        <button onclick="iniciarQuiz()">Iniciar</button>
    </div>
    <div id="quiz" style="display:none;">
        <h2 id="pergunta"></h2>
        <div id="opcoes"></div>
    </div>
    <div id="resultado" style="display:none;">
        <h2>Fim do Quiz!</h2>
        <p id="pontuacao"></p>
        <p id="tempo"></p>
    </div>
</body>
</html>

