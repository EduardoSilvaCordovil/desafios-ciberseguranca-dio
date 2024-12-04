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

```

# Enumeração de serviços em um servidor

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
    137: 'NetBIOS-NS',
    138: 'NetBIOS-DGM',
    139: 'NetBIOS-SSN',
    143: 'IMAP',
    161: 'SNMP',
    162: 'SNMP Trap',
    179: 'BGP',
    389: 'LDAP',
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
    1433: 'Microsoft SQL Server',
    1521: 'Oracle Database',
    1723: 'PPTP',
    2049: 'NFS',
    2083: 'cPanel (Secure)',
    2087: 'WHM (Secure)',
    3306: 'MySQL',
    3389: 'RDP',
    5432: 'PostgreSQL',
    5900: 'VNC',
    5985: 'WinRM (HTTP)',
    5986: 'WinRM (HTTPS)',
    6379: 'Redis',
    8080: 'Desconhecido',
    8443: 'HTTPS Alternate',
    9000: 'SonarQube'
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

# Verificando Phishing

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
``
