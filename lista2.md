# PPGBIOINFO – UTFPR Campus Cornélio Procópio
## **Disciplina:** Programação para Bioinformática I
## **Docente:** Marcella Scoczynski Ribeiro Martins
## **Discente:** Madson A. de Luna Aragão

---

### **Lista 2 (7 pts)**

---

#### **Questão 1**
*Escreva um programa em Python para gerar estatísticas sobre sequências de DNA. O programa deve fazer o seguinte:*
*a. Ler o nome da sequência, o tamanho (número de nucleotídeos), o valor do conteúdo GC (percentual de G e C) até que no nome da sequência seja informado a palavra "pare".*
*b. Imprimir:*
*i. O nome, tamanho e conteúdo GC da maior sequência*
*ii. O nome, tamanho e conteúdo GC da menor sequência*
*iii. A média de tamanho das sequências*
*iv. A média de conteúdo GC*
*v. A lista de nome das sequências com tamanhos menores que a média*
*vi. A média de conteúdo GC somente das sequências com tamanho maiores que a média.*

**Resolução:**
```python
# Inicializa uma lista vazia para armazenar os dados de cada sequência.
# Cada item na lista será um dicionário contendo as informações da sequência.
lista_sequencias = []

# Loop infinito para coletar os dados das sequências. O loop será interrompido quando o usuário digitar "pare".
while True:
    # Solicita o nome da sequência ao usuário.
    nome_seq = input("Informe o nome da sequência (ou 'pare' para encerrar): ")
    
    # Verifica a condição de parada. .lower() torna a verificação insensível a maiúsculas/minúsculas.
    if nome_seq.lower() == 'pare':
        break
    
    # Solicita o tamanho e o conteúdo GC, convertendo as entradas para os tipos numéricos corretos (inteiro e float).
    tamanho_seq = int(input(f"Informe o tamanho da sequência '{nome_seq}': "))
    gc_seq = float(input(f"Informe o conteúdo GC (%) da sequência '{nome_seq}': "))
    
    # Cria um dicionário para organizar os dados da sequência atual.
    dados_sequencia = {
        "nome": nome_seq,
        "tamanho": tamanho_seq,
        "gc": gc_seq
    }
    
    # Adiciona o dicionário com os dados da sequência à lista principal.
    lista_sequencias.append(dados_sequencia)
    print("-" * 20) # Linha separadora para melhor visualização.

# Após o loop, verifica se alguma sequência foi de fato inserida.
if not lista_sequencias:
    print("\nNenhuma sequência foi inserida para análise.")
else:
    # --- Início dos Cálculos ---

    # Encontra a maior e a menor sequência com base na chave 'tamanho'.
    # A função 'lambda' cria uma pequena função anônima para indicar qual valor do dicionário usar na comparação.
    maior_sequencia = max(lista_sequencias, key=lambda seq: seq['tamanho'])
    menor_sequencia = min(lista_sequencias, key=lambda seq: seq['tamanho'])
    
    # Itera sobre a lista de sequências para somar todos os tamanhos e conteúdos GC.
    total_tamanho = sum(seq['tamanho'] for seq in lista_sequencias)
    total_gc = sum(seq['gc'] for seq in lista_sequencias)
    
    # Calcula as médias dividindo os totais pelo número de sequências.
    num_sequencias = len(lista_sequencias)
    media_tamanho = total_tamanho / num_sequencias
    media_gc = total_gc / num_sequencias
    
    # Filtra os nomes das sequências com tamanho menor que a média.
    seqs_menores_media = [seq['nome'] for seq in lista_sequencias if seq['tamanho'] < media_tamanho]
    
    # Filtra as sequências inteiras (dicionários) com tamanho maior que a média.
    seqs_maiores_media = [seq for seq in lista_sequencias if seq['tamanho'] > media_tamanho]
            
    # Calcula a média de GC somente das sequências maiores que a média de tamanho.
    media_gc_maiores = 0
    if seqs_maiores_media: # A verificação evita uma divisão por zero se nenhuma sequência for maior que a média.
        total_gc_maiores = sum(seq['gc'] for seq in seqs_maiores_media)
        media_gc_maiores = total_gc_maiores / len(seqs_maiores_media)

    # --- Impressão dos Resultados ---
    print("\n" + "="*30)
    print("      RELATÓRIO FINAL      ")
    print("="*30)
    
    print(f"\ni. Maior Sequência:\n   - Nome: {maior_sequencia['nome']}\n   - Tamanho: {maior_sequencia['tamanho']} nucleotídeos\n   - Conteúdo GC: {maior_sequencia['gc']:.2f}%")
    print(f"\nii. Menor Sequência:\n   - Nome: {menor_sequencia['nome']}\n   - Tamanho: {menor_sequencia['tamanho']} nucleotídeos\n   - Conteúdo GC: {menor_sequencia['gc']:.2f}%")
    print(f"\niii. Média de Tamanho das Sequências: {media_tamanho:.2f} nucleotídeos")
    print(f"\niv. Média de Conteúdo GC Geral: {media_gc:.2f}%")
    print("\nv. Sequências com Tamanho Menor que a Média:")
    if seqs_menores_media:
        for nome in seqs_menores_media:
            print(f"   - {nome}")
    else:
        print("   - Nenhuma.")
    print(f"\nvi. Média de GC das Sequências Maiores que a Média de Tamanho: {media_gc_maiores:.2f}%")
    print("\n" + "="*30)
```

#### **Questão 2**
*Em um experimento serão utilizados dois organismos, denominados org1 e org2, respectivamente. Fazer um programa em Python que:
a. Leia ID (número de identificação) do organismo até que o usuário digite zero (0).
b. Se for org1: i. Se for filhote: 1. Leia peso 2. Leia altura ii. Se for adulto: 1. Se for macho: a. Leia tipo sanguíneo (A ou B) 2. Se for fêmea a. Leia tipo sanguíneo (A o B) b. Leia número de ovos que botou (valor inteiro)
c. Se for org2: i. Leia número de folhas ii. Leia total de frutos
d. Ao final mostre: i. Número de indivíduos do org1 ii. Percentual de filhotes do org1 iii. Total de indivíduos do tipo sanguíneo A iv. Proporção de fêmeas com tipo sanguíneo B em relação ao total de indivíduos (machos e fêmeas) v. Média do número de ovos das fêmeas do tipo sanguíneo A vi. Número de indivíduos do org2 vii. ID do indivíduo com maior número de folhas do org2 viii. Média de frutos do org2*

**Resolução:**
```python
# Inicialização de todas as variáveis que servirão como contadores e acumuladores para as estatísticas.
# Variáveis para o Organismo 1
total_org1 = 0
filhotes_org1 = 0
adultos_tipo_A = 0
femeas_adultas_B = 0
total_adultos_org1 = 0
ovos_femeas_A = 0
contador_femeas_A = 0 # Contador específico para calcular a média de ovos.

# Variáveis para o Organismo 2
total_org2 = 0
total_frutos_org2 = 0
maior_num_folhas = -1 # Inicia com -1 para garantir que o primeiro número de folhas lido seja o maior.
id_maior_folhas = 0

# Loop principal para coletar dados dos indivíduos. Continua até o ID 0 ser digitado.
while True:
    id_organismo = int(input("\nDigite o ID do indivíduo (ou 0 para finalizar): "))
    if id_organismo == 0:
        break # Encerra o loop.
        
    tipo_organismo = input("Qual o organismo (org1 ou org2)? ").lower()
    
    # Bloco de processamento para o organismo 1.
    if tipo_organismo == 'org1':
        total_org1 += 1 # Incrementa o total de indivíduos do org1.
        estagio = input("O indivíduo é filhote ou adulto? ").lower()
        if estagio == 'filhote':
            filhotes_org1 += 1
            # Lê os dados do filhote, mas não precisa armazená-los para as estatísticas finais.
            input("Digite o peso do filhote: ")
            input("Digite a altura do filhote: ")
        elif estagio == 'adulto':
            total_adultos_org1 += 1 # Incrementa o total de adultos, base para a proporção.
            sexo = input("Qual o sexo (macho ou femea)? ").lower()
            tipo_sanguineo = input("Qual o tipo sanguíneo (A ou B)? ").upper()
            if tipo_sanguineo == 'A':
                adultos_tipo_A += 1
            if sexo == 'femea':
                if tipo_sanguineo == 'B':
                    femeas_adultas_B += 1
                num_ovos = int(input("Número de ovos que botou: "))
                if tipo_sanguineo == 'A':
                    ovos_femeas_A += num_ovos
                    contador_femeas_A += 1

    # Bloco de processamento para o organismo 2.
    elif tipo_organismo == 'org2':
        total_org2 += 1 # Incrementa o total de indivíduos do org2.
        num_folhas = int(input("Digite o número de folhas: "))
        num_frutos = int(input("Digite o total de frutos: "))
        total_frutos_org2 += num_frutos # Acumula o total de frutos para a média.
        # Verifica se o indivíduo atual tem mais folhas que o maior já registrado.
        if num_folhas > maior_num_folhas:
            maior_num_folhas = num_folhas
            id_maior_folhas = id_organismo

# --- Impressão dos Resultados Finais ---
print("\n" + "="*30)
print("      RELATÓRIO DO EXPERIMENTO      ")
print("="*30)

if total_org1 == 0 and total_org2 == 0:
    print("\nNenhum dado foi inserido.")
else:
    # Cálculo e impressão das estatísticas. A verificação 'if > 0' previne divisão por zero.
    print(f"\ni. Número de indivíduos do org1: {total_org1}")
    percentual_filhotes = (filhotes_org1 / total_org1) * 100 if total_org1 > 0 else 0
    print(f"ii. Percentual de filhotes do org1: {percentual_filhotes:.2f}%")
    print(f"iii. Total de adultos org1 com tipo sanguíneo A: {adultos_tipo_A}")
    proporcao_femeas_B = (femeas_adultas_B / total_adultos_org1) * 100 if total_adultos_org1 > 0 else 0
    print(f"iv. Proporção de fêmeas adultas com tipo B (em relação aos adultos de org1): {proporcao_femeas_B:.2f}%")
    media_ovos_femeas_A = ovos_femeas_A / contador_femeas_A if contador_femeas_A > 0 else 0
    print(f"v. Média de ovos de fêmeas adultas com tipo A: {media_ovos_femeas_A:.2f}")
    print(f"\nvi. Número de indivíduos do org2: {total_org2}")
    print(f"vii. ID do indivíduo org2 com mais folhas: {id_maior_folhas} ({maior_num_folhas} folhas)")
    media_frutos_org2 = total_frutos_org2 / total_org2 if total_org2 > 0 else 0
    print(f"viii. Média de frutos por indivíduo do org2: {media_frutos_org2:.2f}")

print("\n" + "="*30)
```

#### **Questão 3**
*Escreva um programa em Python para administrar a votação do líder de turma de uma faculdade. Nessa votação, qualquer aluno da turma pode receber votos (ou seja, caso a turma seja composta de 30 alunos, os 30 alunos se tornam candidatos e podem ser votados). O seu programa deve receber os votos dos eleitores com base no nome do aluno e deve finalizar a eleição quando a palavra "fim" for digitada (em outras palavras, você também não sabe quantas pessoas irão votar). Ao finalizar a eleição, o seu programa deve imprimir os nomes dos candidatos que receberam votos e suas respectivas quantidade. O seu programa deve também imprimir o nome do candidato vencedor. OBS: para resolver essa questão, você deve utilizar dicionário de dados.*

**Resolução:**
```python
# Inicializa um dicionário vazio para funcionar como a urna.
# A chave será o nome do candidato e o valor será a sua contagem de votos.
urna_eletronica = {}

print("--- Eleição para Líder de Turma ---")
print("Digite o nome do candidato em quem você vota.")

# Loop infinito para registrar os votos.
while True:
    # Solicita o voto. .strip() remove espaços extras e .title() padroniza o nome (Ex: "joão" -> "João").
    voto = input("Informe o seu voto (ou 'fim' para encerrar): ").strip().title()

    # Define a condição de parada do loop.
    if voto.lower() == 'fim':
        break
    
    # Verifica se o candidato (voto) já existe como chave no dicionário.
    if voto in urna_eletronica:
        # Se o candidato já existe, incrementa sua contagem de votos.
        urna_eletronica[voto] += 1
    else:
        # Se é o primeiro voto para esse candidato, o adiciona ao dicionário com o valor 1.
        urna_eletronica[voto] = 1

# --- Apuração dos Votos ---
print("\n--- Resultado da eleição ---")

# Verifica se algum voto foi computado.
if not urna_eletronica:
    print("Nenhum voto foi registrado.")
else:
    # Itera sobre os itens do dicionário (pares de candidato-votos) para imprimir a contagem.
    for candidato, total_votos in urna_eletronica.items():
        print(f"{candidato}: {total_votos} voto(s)")

    # Encontra o vencedor. A função max() é usada no dicionário com um critério (key).
    # O critério 'urna_eletronica.get' diz à função para comparar os valores (contagem de votos) em vez das chaves (nomes).
    vencedor = max(urna_eletronica, key=urna_eletronica.get)
    
    print("\n-----------------------------")
    print(f"Vencedor da eleição: {vencedor}")
    print("-----------------------------")
```

#### **Questão 4**
*Escreva um programa que recebe como entrada um conjunto de sequências de DNA como entrada (nome e sequência). O seu programa deve receber sequências enquanto o nome da sequência informada não for fim. Logo após, o seu programa deve calcular e imprimir o tamanho médio das sequências e imprimir quais sequências (nome e sequências) que tem tamanho maiores ou iguais à média. OBS: você deve utilizar dicionário de dados para resolver essa questão.*

**Resolução:**
```python
# Inicializa um dicionário para armazenar as sequências.
# A chave será o nome da sequência e o valor será a própria sequência de DNA.
banco_de_sequencias = {}

print("--- Análise de Sequências de DNA ---")

# Loop infinito para receber os dados das sequências.
while True:
    # Solicita o nome da sequência, que também serve como condição de parada.
    nome = input("\nNome da sequência (ou 'fim' para terminar): ")
    
    # Encerra o loop se o nome for 'fim'.
    if nome.lower() == 'fim':
        break
    
    # Solicita o conteúdo da sequência e o armazena em maiúsculas.
    conteudo = input("Conteúdo da sequência: ").upper()
    
    # Adiciona a nova sequência ao dicionário.
    banco_de_sequencias[nome] = conteudo

# Verifica se o dicionário não está vazio antes de fazer os cálculos.
if not banco_de_sequencias:
    print("\nNenhuma sequência foi inserida.")
else:
    # --- Início dos Cálculos ---

    # Soma os comprimentos (len) de todas as sequências armazenadas nos valores do dicionário.
    tamanho_total = sum(len(sequencia) for sequencia in banco_de_sequencias.values())

    # Calcula o tamanho médio dividindo o total pelo número de sequências.
    tamanho_medio = tamanho_total / len(banco_de_sequencias)
    print(f"\nTamanho médio das sequências: {tamanho_medio:.2f}")

    # --- Impressão das Sequências Maiores ou Iguais à Média ---
    print("\nSequências com tamanho maior ou igual à média:")
    
    # Itera sobre os pares chave-valor do dicionário.
    for nome, sequencia in banco_de_sequencias.items():
        # Verifica se o comprimento da sequência atual atende ao critério.
        if len(sequencia) >= tamanho_medio:
            # Imprime o nome e o conteúdo da sequência.
            print(f"> {nome}")
            print(f"  {sequencia}")
```
