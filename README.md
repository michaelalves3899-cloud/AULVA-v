# 🧮 Projeto Calculadora Interativa - Aula 06
1. CODIGO FEITO
   <!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Calculadora Interativa - Aula 06</title>
    <style>
        body {
            background-color: #f4f4f9;
            font-family: 'Segoe UI', Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .calculadora {
            background-color: #2b3748;
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0px 6px 15px rgba(0, 0, 0, 0.2);
            width: 300px;
        }
        /* Painel que junta os dois displays */
        .painel-display {
            background-color: #edf2f7;
            border-radius: 6px;
            padding: 10px;
            margin-bottom: 20px;
        }
        /* Display menor para a conta inteira */
        #historico {
            width: 100%;
            height: 20px;
            font-size: 14px;
            text-align: right;
            color: #718096;
            border: none;
            background: transparent;
            outline: none;
        }
        /* Display principal para o número atual */
        #display {
            width: 100%;
            height: 40px;
            font-size: 26px;
            text-align: right;
            border: none;
            background: transparent;
            color: #2d3748;
            outline: none;
        }
        .botoes {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
        }
        button {
            width: 22%;
            height: 55px;
            margin-bottom: 10px;
            font-size: 20px;
            font-weight: bold;
            cursor: pointer;
            background-color: #e2e8f0;
            border: none;
            border-radius: 6px;
        }
        button:hover { background-color: #cbd5e0; }
        .btn-limpar { width: 72%; background-color: #feb2b2; color: #9b2c2c; }
        .btn-limpar:hover { background-color: #fc8181; }
        .btn-zero { width: 47%; }
        .btn-igual { width: 47%; background-color: #ed8936; color: white; }
        .btn-igual:hover { background-color: #dd6b20; }
    </style>
</head>
<body>

    <div class="calculadora">
        <div class="painel-display">
            <input type="text" id="historico" readonly placeholder="">
            <input type="text" id="display" readonly placeholder="0">
        </div>

        <div class="botoes">
            <button onclick="limparDisplay()" class="btn-limpar">C</button>
            <button onclick="definirOperacao('/')">/</button>

            <button onclick="adicionarNumero('7')">7</button>
            <button onclick="adicionarNumero('8')">8</button>
            <button onclick="adicionarNumero('9')">9</button>
            <button onclick="definirOperacao('*')">×</button>

            <button onclick="adicionarNumero('4')">4</button>
            <button onclick="adicionarNumero('5')">5</button>
            <button onclick="adicionarNumero('6')">6</button>
            <button onclick="definirOperacao('-')">-</button>

            <button onclick="adicionarNumero('1')">1</button>
            <button onclick="adicionarNumero('2')">2</button>
            <button onclick="adicionarNumero('3')">3</button>
            <button onclick="definirOperacao('+')">+</button>

            <button onclick="adicionarNumero('0')" class="btn-zero">0</button>
            <button onclick="calcular()" class="btn-igual">=</button>
        </div>
    </div>

    <script>
        let valorAtual = '';
        let primeiroOperando = null;
        let operacaoPendente = null;
        
        // Pegando os dois elementos do DOM
        const display = document.getElementById('display');
        const historico = document.getElementById('historico');

        function adicionarNumero(numero) {
            valorAtual += numero;
            display.value = valorAtual;
        }

        function definirOperacao(operacao) {
            if (valorAtual === '') return;
            
            primeiroOperando = parseFloat(valorAtual);
            operacaoPendente = operacao;
            
            // Atualiza o histórico lá em cima mostrando o primeiro número e o sinal (ex: "5 + ")
            historico.value = primeiroOperando + " " + operacao;
            
            valorAtual = '';
            display.value = '';
        }

        function calcular() {
            if (operacaoPendente === null || valorAtual === '') return;
            let segundoOperando = parseFloat(valorAtual);
            let resultado = 0;

            switch (operacaoPendente) {
                case '+': resultado = primeiroOperando + segundoOperando; break;
                case '-': resultado = primeiroOperando - segundoOperando; break;
                case '*': resultado = primeiroOperando * segundoOperando; break;
                case '/': resultado = segundoOperando !== 0 ? primeiroOperando / segundoOperando : 'Erro'; break;
            }

            // Atualiza o histórico mostrando a conta inteira completa com o sinal de igual (ex: "5 + 5 =")
            historico.value = primeiroOperando + " " + operacaoPendente + " " + segundoOperando + " =";
            
            // Mostra o resultado final grandão no display de baixo
            display.value = resultado;
            
            valorAtual = resultado.toString();
            operacaoPendente = null;
        }

        function limparDisplay() {
            valorAtual = '';
            primeiroOperando = null;
            operacaoPendente = null;
            display.value = '';
            historico.value = '';
        }
    </script>
</body>
</html>
Repositório desenvolvido para a entrega da atividade prática da Aula 06 de Desenvolvimento de Sistemas (Front-End). A aplicação executa de forma dinâmica as quatro operações aritméticas básicas e renderiza o histórico completo de cada conta.

## 🚀 Estrutura e Lógica de Implementação
O projeto foi consolidado utilizando os conceitos de manipulação do DOM e gerenciamento de eventos apresentados em aula:
- **HTML (Estrutura):** Componentização dos botões numéricos e operacionais com gatilhos de eventos inline (`onclick`), além de um painel composto por dois displays (um para o histórico da equação e outro para o operando atual).
- **JavaScript (Inteligência):** Utilização de variáveis de escopo global para o gerenciamento de estados (`valorAtual`, `primeiroOperando`, `operacaoPendente`). O processamento aritmético é centralizado em uma estrutura de controle condicional `switch-case`.
- **CSS (Estilização):** Layout responsivo baseado em Flexbox para centralização na tela e organização dos botões em formato de grade (grid), simulando o design de uma calculadora física convencional.

## 📸 Demonstração das Quatro Operações (Evidências)

Abaixo estão os registros visuais do sistema processando cada uma das operações obrigatórias exigidas pelo enunciado:

### 1. Operação de Soma
Exemplo prático de adição aritmética entre dois termos.
![Soma](soma.png)

### 2. Operação de Subtração
Exemplo prático de subtração elementar no display da aplicação.
![Subtração](subtracao.png)

### 3. Operação de Multiplicação
Exemplo prático demonstrando o produto dos fatores calculados.
![Multiplicação](multiplicacao.png)

### 4. Operação de Divisão
Exemplo prático de divisão, contando com tratamento lógico para evitar erros por indeterminação ou divisão por zero.
![Divisão](divisao.png)
