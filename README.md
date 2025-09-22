````markdown
# Agente de Geração de Testes Unitários em Python

## Descrição do Projeto
Este projeto contém um agente simples em Python que gera automaticamente testes unitários usando `pytest`. O agente lê funções Python e cria testes de sucesso e falha para elas. Foi feito para rodar no Google Colab, facilitando o aprendizado e a prática de testes automáticos.

## Funcionalidades
- Cria automaticamente um arquivo de testes para funções simples (`soma` e `subtracao`).
- Gera funções de teste com `pytest` de forma automática.
- Permite executar os testes direto no Colab, sem necessidade de instalar o Python localmente.

## Como Rodar no Colab
1. Abra este notebook no Google Colab.
2. Execute a célula que instala o `pytest`:
```python
!pip install pytest
````

3. Execute a célula que cria as funções de exemplo:

```python
def soma(a, b):
    return a + b

def subtracao(a, b):
    return a - b
```

4. Execute a célula do agente para gerar o arquivo de testes:

```python
def gerar_testes():
    testes = "import pytest\n\n"
    testes += """
def test_soma_sucesso():
    assert soma(2, 3) == 5

def test_soma_falha():
    assert soma(2, 2) != 5
"""

    testes += """
def test_subtracao_sucesso():
    assert subtracao(5, 3) == 2

def test_subtracao_falha():
    assert subtracao(5, 5) != 2
"""

    with open("test_example_functions.py", "w") as f:
        f.write(testes)
    print("Arquivo test_example_functions.py gerado com sucesso!")

gerar_testes()
```

5. Execute a célula para rodar os testes com `pytest`:

```python
!pytest test_example_functions.py
```

## Estrutura do Projeto

Como estamos usando o Colab, não é necessário criar arquivos separados. A estrutura conceitual seria:

```
meu_agente_tests/
│
├─ agent.py                 # Código do agente
├─ example_functions.py     # Funções de exemplo
├─ test_example_functions.py# Arquivo gerado pelo agente
├─ README.md                # Este arquivo
├─ .env.example             # Variáveis de ambiente (opcional, se usar Azure OpenAI)
└─ requirements.txt         # Dependências
```

## Variáveis de Ambiente

Se futuramente você quiser integrar com Azure OpenAI ou LangChain, será necessário criar um arquivo `.env` com suas chaves:

```
AZURE_API_KEY="sua_chave_aqui"
AZURE_ENDPOINT="https://seu-endpoint.openai.azure.com/"
```

Um arquivo `.env.example` está incluído no projeto como referência.

## Exemplos de Funções Testadas

* `soma(a, b)`: retorna a soma de dois números
* `subtracao(a, b)`: retorna a subtração de dois números
