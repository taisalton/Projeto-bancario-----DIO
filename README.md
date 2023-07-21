# Projeto-bancario-----DIO
Criação de um sistema bancário simples em Python


menu = '''

[1] Depositar
[2] Sacar
[3] Extrato
[4] Sair

=> '''

saldo = 0
limite = 500
extrato = ''
numero_saques = 0
LIMITE_SAQUES = 3

while True:

    opcao = input(menu)
    saldo = saldo

    if opcao == '1':
        valor = float(input("Digite o valor do depósito: "))
        if valor >= 0:
            saldo = saldo + valor
            extrato = extrato + f'+ R$ {valor:.2f}\n'
            print('Depósito realizado.')
        else:
            print('Não é possível depositar um valor negativo. Tente novamente')

    elif opcao == '2':
        valor = float(input("Digite o valor de saque: "))
        if valor <= 500:
            numero_saques = numero_saques + 1
            if numero_saques <= 3:
                saldo = saldo - valor
                if saldo >= 0:
                    extrato = extrato + f'- R$ {valor:.2f}\n'
                    print('Saque realizado.')
                else:
                    print('Saldo indisponível')
            else:
                print('Limite de saques encerrados.')
        else:
            print('Não é possível sacar um valor maior que R$ 500 no mesmo saque. Tente novamente')

    elif opcao == '3':
        print('\n****************EXTRATO*****************')
        print('Não foram realizadas movimentações.' if not extrato else extrato)
        print(f'\nSaldo: R$ {saldo:.2f}')
        print('******************************************')
    
    elif opcao == '4':
        break

    else:
        print('Operação inválida, por favor, selecione novamente a operação desejada.')
