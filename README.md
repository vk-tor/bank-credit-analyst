# Sistema de Análise de Crédito Multi-Paradigma

Este projeto demonstra um sistema de análise de crédito implementado utilizando diferentes paradigmas de programação: Orientado a Objetos com Python, Lógico com SWI-Prolog e Funcional com Lisp (SBCL). O objetivo é comparar e contrastar as abordagens para um problema de negócio comum.

## Funcionalidades

O sistema realiza a análise de propostas de crédito baseando-se nos seguintes critérios:

1.  **Idade do Cliente**: O cliente deve ser maior de 18 anos.
2.  **Status de Negativação**: O cliente não deve possuir restrições no CPF (nome limpo).
3.  **Score de Crédito**: Determina a taxa de juros e pode levar à reprovação por alto risco.
4.  **Capacidade de Pagamento**: A parcela do empréstimo não pode exceder 30% da renda mensal do cliente.

## Tecnologias Utilizadas

*   **Python**: Implementação Orientada a Objetos para a análise de risco.
*   **SWI-Prolog**: Implementação Lógica baseada em regras para a análise de crédito.
*   **Common Lisp (SBCL)**: Implementação Funcional para o pipeline de validação de crédito.

## Configuração e Instalação

Para executar este projeto, você precisará ter Python, SWI-Prolog e SBCL instalados em seu ambiente. O projeto foi desenvolvido e testado no Google Colab, que já possui um ambiente Linux.

### 1. Clonar o Repositório

```bash
git clone <URL_DO_SEU_REPOSITORIO>
cd <NOME_DO_SEU_REPOSITORIO>
```

### 2. Instalação de Dependências

**Python:**

```bash
pip install pyswip
```

**SWI-Prolog:**

```bash
sudo apt-get update
sudo apt-get install swi-prolog
```

**SBCL (Steel Bank Common Lisp):**

```bash
sudo apt-get update
sudo apt-get install sbcl
```

## Como Executar

O projeto está organizado em um notebook Jupyter (Colab) que demonstra as três implementações.

### 1. Executar a Análise em Python

A implementação em Python está contida diretamente no notebook. As classes `Cliente`, `Proposta` e `AnaliseRisco` são definidas e testadas com cenários de exemplo. Basta executar as células Python relevantes.

### 2. Executar a Análise em Prolog

O notebook `main.ipynb` cria o arquivo `regras_credito.pl` e o executa utilizando comandos de terminal (`!swipl`). As consultas são feitas diretamente no script:

```prolog
% Exemplo de consulta no arquivo regras_credito.pl
analise_credito(joao, 5000, 12, Resultado).
```

Você pode executar os testes diretamente do notebook, que irá invocar o SWI-Prolog para cada consulta.

### 3. Executar a Análise em Lisp

Similarmente ao Prolog, o notebook cria o arquivo `analise_funcional.lisp`. O script Lisp define as funções e dados para a análise e, em seguida, é executado usando o interpretador SBCL através de um comando de terminal:

```bash
sbcl --noinform --non-interactive --load analise_funcional.lisp --quit
```

Os resultados da análise em Lisp serão impressos na saída do terminal.

## Estrutura do Projeto

*   `main.ipynb`: O notebook principal contendo as implementações em Python, a geração dos arquivos `.pl` e `.lisp`, e a execução dos testes para todas as linguagens.
*   `regras_credito.pl`: Arquivo Prolog com a base de fatos e regras para a análise de crédito.
*   `analise_funcional.lisp`: Arquivo Lisp com as funções puras para o pipeline de validação de crédito.

## Exemplos de Saída

### Python:

```
Análise João: {'status': 'Aprovado', 'categoria': 'Premium', 'taxa_juros': '2%', 'valor_parcela_final': 'R$ 425.00'}
Análise Maria: {'status': 'Reprovado', 'motivo': 'Cliente negativado no CPF'}
Análise Pedro: {'status': 'Reprovado', 'motivo': 'Parcela (R$2187.50) excede 30% da renda'}
```

### Prolog:

```
Consultando: analise_credito(joao, 5000, 12, Resultado)
APROVADO
...
Consultando: analise_credito(maria, 5000, 12, Resultado)
REPROVADO: Cliente Negativado
```

### Lisp:

```
Analisando cliente: Joao... 
(:APROVADO "APROVADO! Parcela: R$425.00 (Juros: 2%)") 
...
Analisando cliente: Maria... 
(:ERRO "Reprovado: Cliente Negativado")
```
