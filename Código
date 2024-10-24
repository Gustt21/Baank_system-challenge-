from typing import List

menu = {
    "d": "Depositar",
    "s": "Sacar",
    "e": "Extrato",
    "q": "Sair"
}

saldo: float = 0.0
limite: float = 500.0
extrato: List[str] = []
numero_saques: int = 0
LIMITES_SAQUES: int = 3

def exibir_menu() -> str:
    """Exibe o menu e captura a opção do usuário."""
    print("\nOperações disponíveis:")
    for key, value in menu.items():
        print(f"[{key}] {value}")
    return input("\nEscolha uma operação: ").lower()

def depositar(valor: float) -> None:
    """Função para realizar um depósito."""
    global saldo
    if valor > 0:
        saldo += valor
        extrato.append(f"Depósito: R${valor:.2f}")
        print("Depósito realizado com sucesso!")
    else:
        print("Operação falhou! O valor informado é inválido.")

def sacar(valor: float) -> None:
    """Função para realizar um saque."""
    global saldo, numero_saques
    if valor > saldo:
        print("Operação falhou! Você não possui saldo suficiente.")
    elif valor > limite:
        print("Operação falhou! O valor excede o limite.")
    elif numero_saques >= LIMITES_SAQUES:
        print("Operação falhou! Você excedeu o limite de saques diários.")
    elif valor > 0:
        saldo -= valor
        extrato.append(f"Saque: R${valor:.2f}")
        numero_saques += 1
        print("Saque realizado com sucesso!")
    else:
        print("Operação falhou! O valor informado é inválido.")

def exibir_extrato() -> None:
    """Função para exibir o extrato."""
    print("\n================ EXTRATO ================")
    print(f"Saldo: R${saldo:.2f}")
    print("Operações realizadas:\n" + ("\n".join(extrato) if extrato else "Nenhuma operação realizada."))
    print("===========================================")

while True:
    opcao: str = exibir_menu()

    if opcao == "d":
        try:
            valor = float(input("Qual valor deseja depositar? "))
            depositar(valor)
        except ValueError:
            print("Por favor, insira um valor numérico válido.")

    elif opcao == "s":
        try:
            valor = float(input("Qual valor deseja sacar? "))
            sacar(valor)
        except ValueError:
            print("Por favor, insira um valor numérico válido.")

    elif opcao == "e":
        exibir_extrato()

    elif opcao == "q":
        print("Obrigado por utilizar nosso sistema!")
        break

    else:
        print("Operação inválida! Por favor, selecione uma operação válida.")
    
    # Pergunta ao cliente se deseja realizar mais operações
    if input("Deseja realizar outra operação? (s/n): ").lower() != "s":
        print("Obrigado por utilizar nosso sistema!")
        break
