# PPGBIOINFO – UTFPR Campus Cornélio Procópio
## **Disciplina:** Programação para Bioinformática I
## **Docente:** Marcella Scoczynski Ribeiro Martins
## **Discente:** Madson A. de Luna Aragão

---

### **Lista 1 (3 pts)**

---

### **Estruturas Condicionais (IF)**

#### **Questão 1**
*Escrever um algoritmo que recebe 4 notas de um aluno e que calcula a média aritmética simples das notas. O algoritmo deve imprimir o valor da média e a palavra "aprovado", se a média é maior ou igual a 6,0 ou "reprovado", caso contrário.*

**Resolução:**
```python
# Inicia o programa com uma mensagem de boas-vindas.
print("Calculadora de Média Escolar")

# Solicita as quatro notas ao usuário. A função float() converte o texto digitado em número decimal.
nota1 = float(input("Digite a primeira nota: "))
nota2 = float(input("Digite a segunda nota: "))
nota3 = float(input("Digite a terceira nota: "))
nota4 = float(input("Digite a quarta nota: "))

# Soma as quatro notas e divide por 4 para calcular a média.
soma_das_notas = nota1 + nota2 + nota3 + nota4
media = soma_das_notas / 4

# Estrutura condicional para verificar o status do aluno.
# Se a média for 6.0 ou superior, o aluno está aprovado.
if media >= 6.0:
    # Imprime a média formatada com duas casas decimais e o resultado "APROVADO".
    print(f"Sua média é {media:.2f}. Resultado: APROVADO!")
else:
    # Caso contrário (se a média for menor que 6.0), o aluno está reprovado.
    print(f"Sua média é {media:.2f}. Resultado: REPROVADO!")

Questão 2
Escreva um algoritmo que recebe como entrada um caractere que representa um nucleotídeo (A, G, C, T) e retorna qual é o seu complementar. Caso o usuário informe um caractere que não é um nucleotídeo, o seu algoritmo deve retornar a mensagem: "Nucleotídeo inválido!"

Resolução:

# Solicita o nucleotídeo ao usuário. O método .upper() converte a entrada para maiúscula.
nucleotideo = input("Digite o caractere do nucleotídeo (A, C, G, T): ").upper()

# Inicia a verificação com uma série de condições.
# Se for 'A', o complementar é 'T'.
if nucleotideo == 'A':
    print("O complementar de Adenina (A) é Timina (T).")
# Senão, se for 'T', o complementar é 'A'.
elif nucleotideo == 'T':
    print("O complementar de Timina (T) é Adenina (A).")
# Senão, se for 'C', o complementar é 'G'.
elif nucleotideo == 'C':
    print("O complementar de Citosina (C) é Guanina (G).")
# Senão, se for 'G', o complementar é 'C'.
elif nucleotideo == 'G':
    print("O complementar de Guanina (G) é Citosina (C).")
# Se a entrada não for nenhuma das opções acima, é inválida.
else:
    print("Nucleotídeo inválido!")

Questão 3
Escreva um algoritmo que permite ao usuário executar ações a partir de dois números informados por ele. O seu algoritmo deve solicitar inicialmente ao usuário informe os dois números e depois exibir o seguinte menu em tela: 1- Soma de 2 números. 2- Diferença entre 2 números (maior pelo menor). 3- Produto entre 2 números. 4- Divisão entre 2 números (o denominador não pode ser zero). O seu programa deve retornar o resultado de acordo com a opção escolhida pelo usuário, obedecendo as restrições existentes em algumas das opções (caso sejam escolhidas).

Resolução:

# Solicita dois números e os converte para float para aceitar decimais.
print("Calculadora Simples")
num1 = float(input("Digite o primeiro número: "))
num2 = float(input("Digite o segundo número: "))

# Exibe o menu de opções para o usuário.
print("\nEscolha a operação:")
print("1 - Soma")
print("2 - Diferença (maior pelo menor)")
print("3 - Produto")
print("4 - Divisão")

# Lê a escolha do usuário e converte para inteiro.
opcao = int(input("Digite o número da opção desejada: "))

# Executa o bloco de código correspondente à opção escolhida.
if opcao == 1:
    # Se a opção for 1, realiza a soma.
    resultado = num1 + num2
    print(f"Resultado da Soma: {num1} + {num2} = {resultado}")
elif opcao == 2:
    # Se a opção for 2, calcula a diferença do maior pelo menor.
    if num1 > num2:
        resultado = num1 - num2
        print(f"Resultado da Diferença: {num1} - {num2} = {resultado}")
    else:
        resultado = num2 - num1
        print(f"Resultado da Diferença: {num2} - {num1} = {resultado}")
elif opcao == 3:
    # Se a opção for 3, calcula o produto.
    resultado = num1 * num2
    print(f"Resultado do Produto: {num1} * {num2} = {resultado}")
elif opcao == 4:
    # Se a opção for 4, verifica se o divisor é diferente de zero antes de dividir.
    if num2 != 0:
        resultado = num1 / num2
        print(f"Resultado da Divisão: {num1} / {num2} = {resultado:.2f}")
    else:
        print("Erro: Divisão por zero não é permitida.")
else:
    # Se a opção não for nenhuma das anteriores, é inválida.
    print("Opção inválida.")

Questão 4
Escrever um algoritmo que lê o sexo ("m" ou "M" ou "f" ou "F") e a idade de uma pessoa e que escreve o valor da entrada a ser pago, de acordo com a seguinte regra: a) Feminino ou masculino, com menos de 10 anos ou mais de 65, valor = R$ 0,50; b) Feminino ou masculino, com idade entre 10 e 17, valor = R$ 4,28; c) Feminino, com idade entre 18 e 65, valor = R$ 5,50; d) Masculino, com idade entre 18 e 65, valor = R$ 8,25.

Resolução:

# Lê o sexo e converte para minúsculo para facilitar a comparação.
sexo = input("Digite o sexo (M/F): ").lower()
# Lê a idade e converte para número inteiro.
idade = int(input("Digite a idade: "))

# Inicializa a variável do valor da entrada.
valor_entrada = 0

# Avalia as faixas de idade e sexo para definir o preço.
if idade < 10 or idade > 65:
    # Regra para menores de 10 ou maiores de 65 anos.
    valor_entrada = 0.50
elif 10 <= idade <= 17:
    # Regra para idade entre 10 e 17 anos (inclusive).
    valor_entrada = 4.28
elif 18 <= idade <= 65:
    # Para a faixa de 18 a 65 anos, o preço depende do sexo.
    if sexo == 'f':
        valor_entrada = 5.50
    elif sexo == 'm':
        valor_entrada = 8.25
    else:
        # Se o sexo for inválido, marca com -1 para indicar o erro.
        valor_entrada = -1 
else:
    # Se a idade não se encaixar em nenhuma regra (improvável), também marca como erro.
    valor_entrada = -1

# Verifica se o valor da entrada é válido antes de imprimir.
if valor_entrada != -1:
    # Imprime o valor formatado como moeda.
    print(f"O valor da entrada é R$ {valor_entrada:.2f}.")
else:
    # Informa ao usuário que a entrada de sexo foi inválida.
    print("Sexo inválido. Por favor, digite 'M' ou 'F'.")

Estruturas de Repetição (WHILE)
Questão 5
Um determinado material radioativo perde metade de sua massa a cada 50 segundos. Dada a massa inicial em gramas informada pelo usuário, fazer um programa que calcula o tempo necessário para que essa massa se torne menor que 0,5 grama. O programa deve escrever a massa inicial, a massa final e o tempo calculado em horas, minutos e segundos.

Resolução:

# Solicita ao usuário a massa inicial do material.
massa_inicial = float(input("Digite a massa inicial do material (em gramas): "))

# Armazena a massa inicial para cálculos e inicializa o contador de tempo.
massa_atual = massa_inicial
tempo_total_segundos = 0

# O loop executa enquanto a massa for 0.5g ou mais.
while massa_atual >= 0.5:
    # A cada iteração, a massa é dividida por 2.
    massa_atual /= 2
    # E o tempo decorrido aumenta em 50 segundos.
    tempo_total_segundos += 50

# Converte o tempo total de segundos para horas, minutos e segundos.
horas = tempo_total_segundos // 3600
segundos_restantes = tempo_total_segundos % 3600
minutos = segundos_restantes // 60
segundos = segundos_restantes % 60

# Apresenta os resultados finais.
print("\n--- Relatório de Decaimento ---")
print(f"Massa Inicial: {massa_inicial:.2f}g")
print(f"Massa Final: {massa_atual:.4f}g")
print(f"Tempo Decorrido: {horas}h {minutos}m {segundos}s")

Questão 6
A série de Fibonacci é formada pela sequência: 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, ... Escreva um algoritmo que gere a série de FIBONACCI até o N-ésimo termo, sendo esse informado pelo usuário.

Resolução:

# Solicita ao usuário o número de termos da série a serem gerados.
n = int(input("Quantos termos da série de Fibonacci você quer gerar? "))

# Inicializa os termos base da série e um contador.
termo_anterior = 0
termo_atual = 1
contador = 1

print(f"\nOs {n} primeiros termos da série de Fibonacci são:")

# O loop roda até que o número de termos gerados seja igual a 'n'.
while contador <= n:
    # Imprime o termo atual. 'end=" "' evita a quebra de linha.
    print(termo_atual, end=" ")
    
    # Calcula o próximo termo da série (soma dos dois anteriores).
    proximo_termo = termo_anterior + termo_atual
    
    # Atualiza os valores: o atual vira o anterior e o próximo vira o atual.
    termo_anterior = termo_atual
    termo_atual = proximo_termo
    
    # Incrementa o contador para controlar a repetição.
    contador += 1

# Imprime uma linha em branco no final para melhor formatação.
print()

Questão 7
Faça um programa que receba um conjunto de valores inteiros e positivos e que calcule e mostre o maior e o menor valor do conjunto. Considere que: a) Para encerrar a entrada de dados, deve ser digitado o valor zero; b) Para valores negativos, deve ser enviada uma mensagem informando que esses números não serão considerados na análise.

Resolução:

# Inicializa as variáveis de maior e menor como 'None' (nulo).
maior_valor = None
menor_valor = None

print("Digite valores inteiros positivos. Digite 0 para finalizar.")

# Cria um loop infinito que será interrompido pelo comando 'break'.
while True:
    # Lê um número do usuário.
    valor = int(input("Digite um número: "))
    
    # Se o valor for 0, encerra o loop.
    if valor == 0:
        print("Finalizando a entrada de dados.")
        break
        
    # Se o valor for negativo, ignora e pede o próximo.
    if valor < 0:
        print("Valor negativo ignorado. Por favor, insira apenas positivos.")
        continue
        
    # Se for o primeiro número válido, ele se torna o maior e o menor.
    if maior_valor is None:
        maior_valor = valor
        menor_valor = valor
    else:
        # Compara com os valores atuais e atualiza se necessário.
        if valor > maior_valor:
            maior_valor = valor
        if valor < menor_valor:
            menor_valor = valor

# Ao final do loop, exibe os resultados.
if maior_valor is not None:
    print("\n--- Análise Concluída ---")
    print(f"Maior valor inserido: {maior_valor}")
    print(f"Menor valor inserido: {menor_valor}")
else:
    print("\nNenhum valor positivo foi inserido para análise.")

Questão 8
Escreva um algoritmo que recebe uma sequência de DNA e que percorre essa sequência imprimindo, para cada posição, qual é o nome do nucleotídeo da posição. Por exemplo: dada a sequência AGGTC, o seu algoritmo deve imprimir a seguinte saída: 1- A: Adenina, 2- G: Guanina, 3- G: Guanina, 4- T: Timina, 5- C: Citosina. Caso a sequência possua algum caractere diferente dos descritos acima, o seu algoritmo deve escrever: "Nucleotídeo inválido!"

Resolução:

# Lê a sequência de DNA e converte para maiúsculas.
sequencia_dna = input("Digite a sequência de DNA: ").upper()

# 'posicao' controla o índice da string. 'sequencia_valida' é uma flag.
posicao = 0
sequencia_valida = True

print("\n--- Análise da Sequência de DNA ---")

# O loop percorre a string da posição 0 até o final.
while posicao < len(sequencia_dna):
    # Obtém o caractere na posição atual.
    nucleotideo = sequencia_dna[posicao]
    
    # Verifica qual é o nucleotídeo e imprime o nome correspondente.
    if nucleotideo == 'A':
        print(f"{posicao + 1} - A: Adenina")
    elif nucleotideo == 'G':
        print(f"{posicao + 1} - G: Guanina")
    elif nucleotideo == 'T':
        print(f"{posicao + 1} - T: Timina")
    elif nucleotideo == 'C':
        print(f"{posicao + 1} - C: Citosina")
    else:
        # Se encontrar um caractere inválido, avisa, muda a flag e para o loop.
        print(f"Erro na posição {posicao + 1}: Caractere '{nucleotideo}' é inválido.")
        sequencia_valida = False
        break
        
    # Avança para o próximo caractere.
    posicao += 1

# Ao final, se a flag foi alterada, exibe a mensagem de erro geral.
if not sequencia_valida:
    print("\nAnálise interrompida: Nucleotídeo inválido encontrado!")

Questão 9
Escreva um algoritmo que recebe uma sequência e um caractere do usuário, calcula e imprime a porcentagem da sequência composta pelo caractere informado. Ex: dada a sequência ACTAGGTTAG e o caractere G, podemos dizer que 30% da sequência é composta pelo caractere G.

Resolução:

# Lê a sequência e o caractere, convertendo ambos para maiúsculas.
sequencia = input("Digite a sequência: ").upper()
caractere_alvo = input("Digite o caractere a ser contado: ").upper()

# Inicializa o contador de ocorrências e o índice da sequência.
contagem = 0
posicao = 0

# O loop percorre toda a sequência.
while posicao < len(sequencia):
    # Se o caractere da posição atual for o alvo, incrementa o contador.
    if sequencia[posicao] == caractere_alvo:
        contagem += 1
    # Passa para o próximo caractere.
    posicao += 1

# Após o loop, calcula a porcentagem.
tamanho_total = len(sequencia)
# Verifica se a sequência não está vazia para evitar divisão por zero.
if tamanho_total > 0:
    porcentagem = (contagem / tamanho_total) * 100
    print(f"\nO caractere '{caractere_alvo}' compõe {porcentagem:.2f}% da sequência.")
else:
    print("\nA sequência está vazia. Não é possível calcular a porcentagem.")

Questão 10
De acordo com a wikipedia, o conteúdo GC (ou conteúdo de guanina-citosina) de uma sequência é a porcentagem de bases nitrogenadas em uma molécula de DNA ou RNA que são guanina ou citosina. Dessa forma, escreva um algoritmo que calcula o conteúdo GC de uma sequência informada pelo usuário.

Resolução:

# Lê a sequência de DNA e a padroniza para maiúsculas.
sequencia = input("Digite a sequência de DNA para cálculo do conteúdo GC: ").upper()

# Inicializa o contador para as bases G e C.
contagem_gc = 0
posicao = 0

# O loop percorre a sequência para contar as bases de interesse.
while posicao < len(sequencia):
    # Pega o nucleotídeo da posição atual.
    nucleotideo = sequencia[posicao]
    # Se for 'G' OU 'C', incrementa o contador.
    if nucleotideo == 'G' or nucleotideo == 'C':
        contagem_gc += 1
    # Move para a próxima posição.
    posicao += 1

# Calcula a porcentagem do conteúdo GC.
tamanho_total = len(sequencia)
# Evita erro de divisão por zero caso a sequência esteja vazia.
if tamanho_total > 0:
    conteudo_gc = (contagem_gc / tamanho_total) * 100
    print(f"\nO conteúdo GC da sequência é de {conteudo_gc:.2f}%.")
else:
    print("\nA sequência está vazia. Não é possível calcular o conteúdo GC.")
