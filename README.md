# Projeto-validacao-de-cadeia-em-automato
Projeto validação de cadeia em autômato

#Aqui mesmo no repertório segue também em arquivo PDF com a apresentação do contexto geral, confira!

Link para acesso do notebook do google COLAB: https://colab.research.google.com/drive/1jIJZUGzg3gL-GxZohi8SDtipMTQosyKQ?usp=sharing

# Código de: Jhonathan de Moura Santos

# Autômato finito que reconhece cadeias sobre {a, b, c} de comprimento >= 1
# Definição do autômato:
# Estados = {q0 (inicial), q1 (aceitação)}
# Alfabeto = {a, b, c}
# Função de transição:
#   δ(q0, x) = q1, para x ∈ {a, b, c}
#   δ(q1, x) = q1, para x ∈ {a, b, c}
# Estado inicial = q0
# Estado de aceitação = {q1}

def validar_cadeia(cadeia: str) -> bool:
    estado = "q0"

    # Se a cadeia for vazia, rejeita imediatamente
    if cadeia == "":
        return False

    for simbolo in cadeia:
        if simbolo not in {"a", "b", "c"}:
            # Se encontrar símbolo fora do alfabeto, rejeita
            return False

        if estado == "q0":
            estado = "q1"  # ao ler o primeiro símbolo, vai para estado de aceitação
        elif estado == "q1":
            estado = "q1"  # permanece em aceitação

    return estado == "q1"


# -------------------------------
# Entrada das cadeias para validação
while True:
    cadeia = (input("Digite uma cadeia (ou 'sair' para encerrar): ")).strip()

    if cadeia.lower() == "sair":
        print("Encerrando o validador. Até mais!")
        break

    if validar_cadeia(cadeia):
        print(f"Cadeia '{cadeia}' -> ACEITA ✅\n")
    else:
        print(f"Cadeia '{cadeia}' -> REJEITA ❌\n")
