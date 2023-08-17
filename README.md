# venturi
def exibe_funcionarios(funcionarios):
    print('\n' + '-' * 50)
    print(f'{"NOME":^16}', end=' | ')
    print(f'{"SALÁRIO":^11}', end=' | ')
    print(f'{"TEMPO ":^7}', end=' | ')
    print('META')
    print('-' * 50)
    for funcionario in funcionarios:
        print(f'{funcionario[0]:16}', end=' | ')
        print(f'R$ {funcionario[1]:8.2f}', end=' | ')
        print(f'{funcionario[2]:2} {"ano" if funcionario[2] == 1 else "anos":4}', end=' | ')
        if funcionario[3]:
            print(f'{"😀":^4}')
        else:
            print(f'{"😔":^4}')
    print('-' * 50)

def exibe_bonus(bonus):
    print('\n' + '-' * 30)
    print(f'{"NOME":^16}', end=' | ')
    print(f'{"BÔNUS":^11}')
    print('-' * 30)
    for fncionario in bonus:
        print(f'{fncionario[0]:16}', end=' | ')
        print(f'R$ {fncionario[1]:8.2f}')
    print('-' * 30)

def coleta_funcionarios():
    funcionarios = []
    entrada = input('Dados do Funcionário: ')
    while entrada != '':
        funcionario = entrada.split(';')
        funcionario[1] = float(funcionario[1])
        funcionario[2] = int(funcionario[2])
        funcionario[3] = (funcionario[3]=='sim')
        funcionarios.append(funcionario)
        entrada = input('Dados do Funcionário: ')
    return funcionarios

def calcula_bonus(funcionarios):
    bonus = []
    for funcionario in funcionarios:
        valor = funcionario[1] + (0.05 * funcionario[2] * funcionario[1])
        if funcionario[3]:
            valor += 0.10 * valor
        bonus.append([funcionario[0], valor])
    return bonus

def main():
    funcionarios = coleta_funcionarios()
    exibe_funcionarios(funcionarios)
    bonus = calcula_bonus(funcionarios)
    exibe_bonus(bonus)

main()
