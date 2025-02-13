<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz CPA-20</title>
    <style>
        body { 
            font-family: Arial, sans-serif; 
            text-align: center; 
            margin: 50px; 
            background: linear-gradient(to right, #141E30, #243B55); 
            color: white;
        }
        #quiz { 
            max-width: 600px; 
            margin: auto; 
            background: #2D3E50;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(255, 255, 255, 0.2);
        }
        ul { list-style-type: none; padding: 0; }
        li { 
            background: #4CAF50; 
            padding: 15px; 
            margin: 10px; 
            cursor: pointer; 
            border-radius: 5px;
            transition: 0.3s;
        }
        li:hover { background: #45A049; }
        h2 { color: #FFD700; }
        #feedback { font-weight: bold; }
    </style>
</head>
<body>
    <div id="quiz"></div>
    <script>
        const quizData = [
            { question: "O que é o CDI?", options: ["Certificado de Depósito Interbancário", "Conta de Depósito Imediato", "Cálculo de Desconto de Investimentos", "Crédito Direto ao Investidor"], answer: 0, explanation: "O CDI é um título emitido entre instituições financeiras para empréstimos de curto prazo." },
            { question: "Qual é o órgão responsável por regulamentar o mercado financeiro no Brasil?", options: ["Banco Central do Brasil", "CVM", "B3", "ANBIMA"], answer: 0, explanation: "O Banco Central do Brasil regulamenta e fiscaliza o sistema financeiro nacional." },
            { question: "O que significa SELIC?", options: ["Sistema Especial de Liquidação e Custódia", "Serviço de Empréstimos de Liquidez", "Sistema Estatístico de Liquidez", "Solução Estratégica de Crédito"], answer: 0, explanation: "A SELIC é a taxa básica de juros da economia brasileira." },
            { question: "O que são debêntures?", options: ["Títulos de dívida emitidos por empresas", "Ações preferenciais", "Títulos do governo", "Derivativos financeiros"], answer: 0, explanation: "As debêntures são títulos de dívida emitidos por empresas para captar recursos." },
            { question: "Qual índice mede a inflação oficial no Brasil?", options: ["IPCA", "IGP-M", "INPC", "IGP-DI"], answer: 0, explanation: "O IPCA é o índice oficial de inflação no Brasil." },
            { question: "Qual ativo é considerado de renda variável?", options: ["Ações", "CDB", "Tesouro Direto", "LCI"], answer: 0, explanation: "As ações são ativos de renda variável, pois seu preço pode oscilar no mercado." },
            { question: "O que é um fundo multimercado?", options: ["Fundo que investe em diversos tipos de ativos", "Fundo focado em renda fixa", "Fundo de previdência privada", "Fundo exclusivo para bancos"], answer: 0, explanation: "Fundos multimercado investem em diversos ativos, como renda fixa, ações e câmbio." },
            { question: "Quem pode emitir um CDB?", options: ["Bancos", "Empresas", "O governo", "Investidores individuais"], answer: 0, explanation: "Os CDBs são emitidos por bancos para captar recursos." },
            { question: "O que é liquidez?", options: ["Facilidade de conversão de um ativo em dinheiro", "Rentabilidade de um investimento", "Risco de mercado", "Prazo de vencimento de um título"], answer: 0, explanation: "Liquidez representa a facilidade com que um ativo pode ser convertido em dinheiro." },
            { question: "Qual é a principal bolsa de valores do Brasil?", options: ["B3", "NASDAQ", "NYSE", "CVM"], answer: 0, explanation: "A B3 (Brasil, Bolsa, Balcão) é a principal bolsa de valores do Brasil." }
        ];

        let currentQuestion = 0;
        let score = 0;

        function loadQuestion() {
            const quizContainer = document.getElementById("quiz");
            const questionData = quizData[currentQuestion];

            quizContainer.innerHTML = `
                <h2>${questionData.question}</h2>
                <ul>
                    ${questionData.options.map((option, index) => `
                        <li onclick="selectAnswer(${index})">${option}</li>
                    `).join('')}
                </ul>
                <p id="feedback"></p>
            `;
        }

        function selectAnswer(selectedIndex) {
            const feedback = document.getElementById("feedback");
            const questionData = quizData[currentQuestion];

            if (selectedIndex === questionData.answer) {
                score++;
                feedback.innerHTML = `<span style='color: #32CD32;'>Correto! ${questionData.explanation}</span>`;
            } else {
                feedback.innerHTML = `<span style='color: #FF4500;'>Errado! ${questionData.explanation}</span>`;
            }

            setTimeout(() => {
                currentQuestion++;
                if (currentQuestion < quizData.length) {
                    loadQuestion();
                } else {
                    showResult();
                }
            }, 2000);
        }

        function showResult() {
            const quizContainer = document.getElementById("quiz");
            quizContainer.innerHTML = `<h2>Você acertou ${score} de ${quizData.length} perguntas!</h2>`;
        }

        document.addEventListener("DOMContentLoaded", loadQuestion);
    </script>
</body>
</html>
