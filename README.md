# Verificador de integridade de arquivo

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

```

# Enumerador de serviços em um servidor

## Descrição
Desenvolva um sistema que simule a enumeração de serviços em um servidor, dado um conjunto de portas e serviços associados. Você deve receber uma lista de números de portas e, para cada porta, retornar o serviço associado. Se a porta não estiver no dicionário, retorna "Desconhecido".

## Entrada
Uma lista de números de portas separados por vírgula.

## Saída
Uma lista de serviços correspondentes a essas portas.

```python
import sys

ports_services = {
    20: 'FTP (Data Transfer)',
    21: 'FTP',
    22: 'SSH',
    23: 'Telnet',
    25: 'SMTP',
    53: 'DNS',
    67: 'DHCP (Server)',
    68: 'DHCP (Client)',
    69: 'TFTP',
    80: 'HTTP',
    110: 'POP3',
    123: 'NTP',
    143: 'IMAP',
    161: 'SNMP',
    162: 'SNMP Trap',
    179: 'BGP',
    443: 'HTTPS',
    445: 'SMB',
    465: 'SMTP over SSL',
    514: 'Syslog',
    587: 'SMTP (Mail Submission)',
    636: 'LDAPS',
    989: 'FTPS (Data)',
    990: 'FTPS (Control)',
    993: 'IMAPS',
    995: 'POP3S',
    2049: 'NFS',
    2083: 'cPanel (Secure)',
    3306: 'MySQL',
    3389: 'RDP',
    5432: 'PostgreSQL',
    6379: 'Redis',
    8080: 'Desconhecido'
}

def enumerate_services(ports):
    services = []
    for port in ports:
        if port in ports_services:
            services.append(ports_services[port])
        else:
            services.append("DESCONHECIDO!")
    return services

def main():
    ports_input = sys.stdin.readline().strip()
    ports = [int(port.strip()) for port in ports_input.split(',')]
    services = enumerate_services(ports)
    print(services)

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
``
