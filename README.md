# 🧮 Projeto Calculadora Interativa - Aula 06

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
