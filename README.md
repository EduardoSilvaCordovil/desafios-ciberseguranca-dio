# Verifica a integridade de arquivo

## Descrição
Você foi encarregado de criar um sistema simples que verifica a integridade de arquivos, comparando o hash fornecido pelo usuário com o hash real do arquivo. Na função verificar_hashes que irá receber uma lista de hashes e compará-los com os valores esperados para cada arquivo. Seu objetivo é verificar se o hash calculado é igual ao hash esperado.

## Entrada
Uma lista de pares de hashes (hash calculado e hash esperado), separados por vírgulas, e cada par separado por ponto e vírgula.

## Saída
Para cada par de hashes fornecido, o código imprime o resultado "Correto" ou "Inválido".

## Resultado:

```python

def verificar_hashes(lista_hashes):
    for hash_comparacao in lista_hashes:
        hash_calculado, hash_esperado = hash_comparacao.split(",")
        
        # Remove espaços em branco que possam estar no início ou no final
        hash_calculado = hash_calculado.strip()
        hash_esperado = hash_esperado.strip()
        
        # Verifique se os hashes são iguais
        if hash_calculado == hash_esperado:
            print("Correto")
        else:
            print("Inválido")

# Entrada do usuário
hashes_usuario = input()

# Dividir os pares de hashes pelo ponto e vírgula
lista_hashes = hashes_usuario.split(";")

# Chamar a função para verificar os hashes
verificar_hashes(lista_hashes)
