# Simulador de Financiamento Imobiliário (SAC/PRICE)

Este projeto é uma ferramenta interativa desenvolvida em HTML5, CSS3 e JavaScript (React) para simular cenários de financiamento habitacional. O objetivo principal é permitir a análise do impacto de **amortizações extraordinárias** no saldo devedor e no tempo total de quitação.

---

## Funcionalidades Principais

- **Comparação de Sistemas:** Alternância dinâmica entre as tabelas **SAC** (parcelas decrescentes) e **PRICE** (parcelas fixas).
- **Simulação de Amortização Extra:** Inclusão de aportes anuais ou mensais para visualizar a redução drástica de juros e prazo.
- **Gráficos em Tempo Real:** Visualização da curva de decaimento do saldo devedor através da biblioteca Recharts.
- **Cálculo de Custo Efetivo:** Exibição do total de juros pagos e o valor final do imóvel ao final do período.

---

## Documentação das Funções

O núcleo da lógica reside no arquivo `index.html`. Abaixo estão as principais funções explicadas:

### 1. `calcularFinanciamento()`
A função principal que orquestra os cálculos matemáticos.
- **O que faz:** Recebe o valor financiado, taxa de juros e prazo. Dependendo da escolha do usuário (SAC ou PRICE), ela itera mês a mês calculando a parcela de juros ($Saldo \times Taxa$) e a amortização.
- **Retorno:** Um array de objetos contendo a evolução mensal completa.

### 2. `aplicarAmortizacaoExtra(fluxoCaixa)`
Gerencia a lógica de redução de saldo por pagamentos avulsos.
- **O que faz:** Verifica em quais meses existem aportes extras (ex: uso do FGTS anual ou economia mensal) e subtrai diretamente do saldo devedor antes do cálculo dos juros do mês seguinte.
- **Impacto:** Recalcula o tempo restante da dívida automaticamente.

### 3. `formatarMoeda(valor)`
Uma função utilitária para interface de usuário (UI).
- **O que faz:** Utiliza a API `Intl.NumberFormat('pt-BR')` para converter números brutos em strings formatadas como moeda brasileira (R$).

### 4. `toggleSistemaAmortizacao()`
Controla o estado da aplicação.
- **O que faz:** Alterna os algoritmos de cálculo entre o sistema de amortização constante e o sistema francês, atualizando os componentes de UI e o gráfico instantaneamente.

---

##Tecnologias Utilizadas

- **React (via CDN):** Para a reatividade da página sem necessidade de build complexo.
- **Tailwind CSS:** Para estilização rápida e responsiva.
- **Recharts:** Para a renderização dos gráficos de área e linhas.
- **Lucide Icons:** Conjunto de ícones para melhorar a experiência visual.

---

## Como Usar

1. Salve o código no arquivo `index.html`.
2. Abra o arquivo em qualquer navegador moderno.
3. Insira o **Valor do Imóvel**, o valor da **Entrada** e a **Taxa de Juros Anual**.
4. Adicione valores de amortização extra para ver em quanto tempo você pode antecipar a quitação.

---

> *Nota: Este simulador é uma ferramenta de auxílio à decisão e pode apresentar variações mínimas em relação aos sistemas bancários devido a taxas administrativas e seguros (MIP/DFI) não inclusos nesta versão simplificada.*
> 
