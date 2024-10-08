1) Observe o trecho de código abaixo: int INDICE = 13, SOMA = 0, K = 0;
Enquanto K < INDICE faça { K = K + 1; SOMA = SOMA + K; }
Imprimir(SOMA);
Ao final do processamento, qual será o valor da variável SOMA?


INDICE = 13
SOMA = 0
K = 0 
Loop: Enquanto K < INDICE:
Incrementa K em 1 (K = K + 1)
Adiciona o valor de K a SOMA (SOMA = SOMA + K)
Vamos calcular manualmente:

Iteração 1: K = 1, SOMA = 0 + 1 = 1
Iteração 2: K = 2, SOMA = 1 + 2 = 3
Iteração 3: K = 3, SOMA = 3 + 3 = 6
Iteração 4: K = 4, SOMA = 6 + 4 = 10
Iteração 5: K = 5, SOMA = 10 + 5 = 15
Iteração 6: K = 6, SOMA = 15 + 6 = 21
Iteração 7: K = 7, SOMA = 21 + 7 = 28
Iteração 8: K = 8, SOMA = 28 + 8 = 36
Iteração 9: K = 9, SOMA = 36 + 9 = 45
Iteração 10: K = 10, SOMA = 45 + 10 = 55
Iteração 11: K = 11, SOMA = 55 + 11 = 66
Iteração 12: K = 12, SOMA = 66 + 12 = 78
Iteração 13: K = 13, SOMA = 78 + 13 = 91
Ao final do processamento, o valor da variável SOMA será 91.



2) Dado a sequência de Fibonacci, onde se inicia por 0 e 1 e o próximo valor sempre será a soma dos 2 valores anteriores (exemplo: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34...), escreva um programa na linguagem que desejar onde, informado um número, ele calcule a sequência de Fibonacci e retorne uma mensagem avisando se o número informado pertence ou não a sequência.

Python
def fibonacci_sequence(n):
    fib_sequence = [0, 1]
    while fib_sequence[-1] < n:
        fib_sequence.append(fib_sequence[-1] + fib_sequence[-2])
    return fib_sequence

def is_fibonacci_number(num):
    fib_sequence = fibonacci_sequence(num)
    if num in fib_sequence:
        return f"O número {num} pertence à sequência de Fibonacci."
    else:
        return f"O número {num} não pertence à sequência de Fibonacci."

# Exemplo de uso
numero = int(input("Informe um número: "))
resultado = is_fibonacci_number(numero)
print(resultado)


3) Dado um vetor que guarda o valor de faturamento diário de uma distribuidora, faça um programa, na linguagem que desejar, que calcule e retorne:
• O menor valor de faturamento ocorrido em um dia do mês;
• O maior valor de faturamento ocorrido em um dia do mês;
• Número de dias no mês em que o valor de faturamento diário foi superior à média mensal.

IMPORTANTE:
a) Usar o json ou xml disponível como fonte dos dados do faturamento mensal;
b) Podem existir dias sem faturamento, como nos finais de semana e feriados. Estes dias devem ser ignorados no cálculo da média;

Json

{
    "faturamento_diario": [
        {"dia": 1, "valor": 1000.0},
        {"dia": 2, "valor": 1500.0},
        {"dia": 3, "valor": 0.0},
        {"dia": 4, "valor": 2000.0},
        {"dia": 5, "valor": 0.0},
        {"dia": 6, "valor": 3000.0},
        {"dia": 7, "valor": 0.0},
        {"dia": 8, "valor": 2500.0}
        // ... outros dias do mês
    ]
}

Python 
import json

def calcular_faturamento(faturamento_diario):
    valores = [dia["valor"] for dia in faturamento_diario if dia["valor"] > 0]
    
    menor_valor = min(valores)
    maior_valor = max(valores)
    media_mensal = sum(valores) / len(valores)
    
    dias_acima_da_media = sum(1 for valor in valores if valor > media_mensal)
    
    return menor_valor, maior_valor, dias_acima_da_media

# Leitura do arquivo JSON
with open('faturamento.json', 'r') as file:
    dados = json.load(file)

faturamento_diario = dados["faturamento_diario"]

menor_valor, maior_valor, dias_acima_da_media = calcular_faturamento(faturamento_diario)

print(f"Menor valor de faturamento: {menor_valor}")
print(f"Maior valor de faturamento: {maior_valor}")
print(f"Número de dias com faturamento acima da média: {dias_acima_da_media}")


4) Dado o valor de faturamento mensal de uma distribuidora, detalhado por estado:
• SP – R$67.836,43
• RJ – R$36.678,66
• MG – R$29.229,88
• ES – R$27.165,48
• Outros – R$19.849,53


Python

# Dados de faturamento mensal por estado
faturamento = {
    "SP": 67836.43,
    "RJ": 36678.66,
    "MG": 29229.88,
    "ES": 27165.48,
    "Outros": 19849.53
}

# Calcula o faturamento total
faturamento_total = sum(faturamento.values())

# Calcula o percentual de cada estado
percentuais = {estado: (valor / faturamento_total) * 100 for estado, valor in faturamento.items()}

# Exibe os resultados
for estado, percentual in percentuais.items():
    print(f"{estado}: {percentual:.2f}%")

print(f"Faturamento Total: R${faturamento_total:.2f}")


Saida: 
SP: 37.53%
RJ: 20.29%
MG: 16.18%
ES: 15.06%
Outros: 10.95%
Faturamento Total: R$180759.98


5) Escreva um programa que inverta os caracteres de um string.

def inverter_string(s):
    return s[::-1]

# Exemplo de uso
string_original = "Exemplo"
string_invertida = inverter_string(string_original)
print("String original:", string_original)
print("String invertida:", string_invertida)
