# Verificador de integridade de arquivo

## Descrição
Você foi encarregado de criar um sistema simples que verifica a integridade de arquivos, comparando o hash fornecido pelo usuário com o hash real do arquivo. Na função verificar_hashes que irá receber uma lista de hashes e compará-los com os valores esperados para cada arquivo. Seu objetivo é verificar se o hash calculado é igual ao hash esperado.

## Entrada
Uma lista de pares de hashes (hash calculado e hash esperado), separados por vírgulas, e cada par separado por ponto e vírgula.

## Saída
Para cada par de hashes fornecido, o código imprime o resultado "Correto" ou "Inválido".

## Exemplos:
| Entrada     | Saída       |
| ----------- | ----------- | 
| abc123, abc123 | Correto | 
| def456, def789 | Inválido |
| 123abc, 123abc | Correto |
| 456def,456def | Correto |

## Código
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

```

# Enumerador de serviços em um servidor

## Descrição
Desenvolva um sistema que simule a enumeração de serviços em um servidor, dado um conjunto de portas e serviços associados. Você deve receber uma lista de números de portas e, para cada porta, retornar o serviço associado. Se a porta não estiver no dicionário, retorna "Desconhecido".

## Entrada
Uma lista de números de portas separados por vírgula.

## Saída
Uma lista de serviços correspondentes a essas portas.

## Exemplos:
| Entrada     | Saída       |
| ----------- | ----------- | 
| 22, 80, 443 | ['SSH', 'HTTP', 'HTTPS'] | 
| 21, 53, 3306 | ['FTP', 'DNS', 'MySQL'] |
| 23, 443, 8080 | ['Telnet', 'HTTPS', 'Desconhecido'] |

## Código
```python
port_services = {
    21: "FTP",      # Serviço de transferência de arquivos
    22: "SSH",      # Secure Shell (acesso remoto seguro)
    23: "Telnet",   # Protocolo de acesso remoto inseguro
    25: "SMTP",     # Serviço de envio de emails
    53: "DNS",      # Serviço de tradução de nomes de domínio
    80: "HTTP",     # Protocolo de transferência de hipertexto (web)
    110: "POP3",    # Serviço de recebimento de emails
    143: "IMAP",    # Serviço de recebimento de emails com suporte a pastas
    443: "HTTPS",   # Protocolo seguro de transferência de hipertexto
    3306: "MySQL",  # Banco de dados MySQL
    3389: "RDP",    # Remote Desktop Protocol (Acesso remoto no Windows)
    5432: "PostgreSQL", # Banco de dados PostgreSQL
    6379: "Redis"   # Banco de dados Redis
}

# Função que realiza a enumeração de serviços
def enumerate_services(ports):
    # Inicializamos uma lista para armazenar os serviços correspondentes
    services = []
    
    # Iteramos sobre cada porta fornecida na lista de portas
    for port in ports:
        # Verificamos se a porta existe no dicionário de serviços
        if port in port_services:
            # Se existir, adicionamos o serviço correspondente à lista de serviços
            services.append(port_services[port])
        else:
            # Se a porta não estiver mapeada, adicionamos "Desconhecido"
            services.append("Desconhecido")
    
    # Retornamos a lista de serviços
    return services

# Função principal que lida com a entrada do usuário e exibe o resultado
def main():
    # Solicitamos a entrada do usuário
    ports_input = input()
    
    # Convertendo a string de entrada para uma lista de inteiros (números de portas)
    ports = []
    for port in ports_input.split(","):
        # Removemos espaços em branco e convertimos para inteiro
        ports.append(int(port.strip()))
    
    # Chamamos a função de enumeração para obter a lista de serviços correspondentes
    services = enumerate_services(ports)
    
    # Exibimos os serviços encontrados
    print(services)

# Certificamos que o código seja executado apenas se este arquivo for executado diretamente
if __name__ == "__main__":
    main()
```

# Verificador de Phishing

## Descrição
Crie uma solução para analisar uma lista de e-mails recebidos, verificando padrões comuns de phishing nas mensagens. Se um e-mail contiver palavras suspeitas como "ganhe", "prêmio", "urgente", "desconto", "click" e "promoção" ele deve ser classificado como "Phishing" e "Seguro".

## Entrada
Uma String contendo um conteúdo único representando o corpo do e-mail.

## Saída
"Phishing" ou "Seguro" para cada e-mail.

## Exemplos:
| Entrada     | Saída       |
| ----------- | ----------- | 
| Ganhe um prêmio incrível hoje! | Classificação: Phishing | 
| Não perca esta promoção exclusiva! | Classificação: Phishing |
| Você está convidado para a reunião amanhã! | Classificação: Seguro |

## Código
```python
import sys

def verificar_phishing(mensagem):
    # Lista de palavras que indicam possíveis e-mails de phishing
    palavras_suspeitas = ["ganhe", "prêmio", "urgente", "desconto", "click", "promoção"]
    
    # Converte a mensagem para minúsculas e verifica a presença de palavras suspeitas
    mensagem_lower = mensagem.lower()
    for palavra in palavras_suspeitas:
        if palavra in mensagem_lower:
            return "Phishing"
    return "Seguro"

def main():
    # Lê o conteúdo do e-mail da entrada padrão
    email_usuario = sys.stdin.readline().strip()
    
    # Verifica a classificação do e-mail
    resultado = verificar_phishing(email_usuario)
    
    # Imprime a classificação do e-mail
    print(f"Classificação: {resultado}")

if __name__ == "__main__":
    main()
```

# Detectar possíveis invasões

## Descrição
Você é responsável por implementar um sistema de monitoramento de segurança para um sistema de acesso. Seu objetivo é analisar registros de log de tentativas de acesso para detectar possíveis invasões. Cada registro contém um identificador de usuário e um status que indica se a tentativa de acesso foi bem-sucedida ou falhou.

A detecção de tentativas de invasão é essencial para a segurança do sistema, e a análise de logs é uma prática comum para identificar comportamentos suspeitos. O sistema deve emitir um alerta se detectar mais de 3 tentativas consecutivas de falha para o mesmo usuário.
## Entrada
Uma lista de registros de log no formato id_usuario:status, onde:

    id_usuario é uma string que representa o identificador do usuário (exemplo: "user1").

    status pode ser uma das seguintes strings:
    - "sucesso" – indica que a tentativa de acesso foi bem-sucedida.
    - "falha" – indica que a tentativa de acesso falhou.

A lista pode conter qualquer número de registros.

## Saída
O sistema deve retornar:

    O id_usuario que teve mais de 3 tentativas consecutivas de falha.

    Se nenhum usuário tiver mais de 3 tentativas de falha consecutivas, o sistema deve retornar a mensagem "Nenhum invasor detectado".

## Exemplos:
| Entrada     | Saída       |
| ----------- | ----------- | 
| user1:falha, user1:falha, user1:falha, user1:sucesso! | Nenhum invasor detectado | 
| user2:falha, user2:falha, user2:falha, user2:falha | user2 |
| user3:sucesso, user3:falha, user3:falha, user3:falha, user3:falha | user3 |

    
## Código
```python
import sys
a = int(sys.stdin.readline())
print(a);

def detectar_invasao(registros):
    # Variáveis para rastrear o ID do usuário atual e suas falhas consecutivas
    usuario_atual = None
    tentativas_consecutivas = 0
    invasor_detectado = None

    for registro in registros:
        # Separa o ID do usuário e o status do registro
        id_usuario, status = registro.split(":")

        # Verifica se o usuário atual é o mesmo da iteração anterior
        if id_usuario == usuario_atual:
            if status == "falha":
                tentativas_consecutivas += 1
                # Detecta o invasor se houver mais de 3 tentativas consecutivas
                if tentativas_consecutivas > 3:
                    invasor_detectado = id_usuario
            else:
                # Reseta o contador de falhas se a tentativa foi bem-sucedida
                tentativas_consecutivas = 0
        else:
            # Verifica se o usuário anterior teve mais de 3 falhas consecutivas
            if tentativas_consecutivas > 3:
                invasor_detectado = usuario_atual

            # Atualiza para o novo usuário e reseta a contagem
            usuario_atual = id_usuario
            tentativas_consecutivas = 1 if status == "falha" else 0

    # Verifica o último usuário no final da lista
    if tentativas_consecutivas > 3:
        invasor_detectado = usuario_atual

    # Retorna o resultado final
    return invasor_detectado if invasor_detectado else "Nenhum invasor detectado"

def main():
    # Lê os registros de log da entrada padrão
    entrada = input().strip()
    registros = [registro.strip() for registro in entrada.split(",")]

    # Detecta tentativas de invasão
    resultado = detectar_invasao(registros)

    # Imprime o resultado
    print(resultado)

if __name__ == "__main__":
    main()
