# Sistema_bancario_V1
Sistema bancario basico para avaliação DIO



menu = """

[1] Depositar
[2] Sacar
[3] Extrato
[0] Sair

=> """

saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3

while True:
    opcao = input(menu)
  #Operação de deposito
    if opcao == "1":
        valor_deposito = float(input("Informe o valor a ser depositado: "))

        if valor_deposito > 0:
            saldo += valor_deposito
            extrato += f"Depósito: R$ {valor_deposito:.2f}\n"
            print(f"Depósito de R$ {valor_deposito:.2f} realizado com sucesso!")
        else:
            print("Depósito inválido! Somente valores positivos são permitidos.")

  #operação de saque
    elif opcao == "2":
        valor_saque = float(input("Informe o valor a ser sacado: "))

        excedeu_saldo = valor_saque > saldo
        excedeu_limite = valor_saque > limite
        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print("Saldo insuficiente para realizar o saque.")
        elif excedeu_limite:
            print(f"O limite máximo por saque é de R$ {limite:.2f}.")
        elif excedeu_saques:
            print("Número máximo de saques diários excedido.")
        elif valor_saque > 0:
            saldo -= valor_saque
            extrato += f"Saque: R$ {valor_saque:.2f}\n"
            numero_saques += 1
            print(f"Saque de R$ {valor_saque:.2f} realizado com sucesso!")
        else:
            print("O valor informado é inválido. Saques devem ser positivos.")

  #Operaçãode de extrato
    elif opcao == "3":
        print("\n========== EXTRATO ==========")
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f"\nSaldo atual: R$ {saldo:.2f}")
        print("==============================")

  #Operação de sair
    elif opcao == "0":
        print("Obrigado por utilizar nosso sistema bancário. Até logo!")
        break

    else:
        print("Opção inválida, por favor selecione novamente a operação desejada.")







