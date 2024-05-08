## Table of Contents
1. [Installation - en](#installation)
2. [Instalação - pt-br](#instalação)
3. [How to configure](#configuration)
4. [Como Configurar](#configuração)

---
# ShadowDomain  - en

This project consists of a tool aimed at automating the search and verification of subdomains on a target domain. The scripts included in this set perform specific functions to facilitate the collection of information about subdomains of a provided domain, thus assisting in cybersecurity activities and penetration testing.

This project is based on AI copilot and errors may occur.

## gerador.py

It is responsible for generating cryptographic keys for API tokens. The script securely generates keys, encrypts the tokens, and saves the information in the SQLite database `api_tokens.db`. This functionality ensures the protection of sensitive data, such as API keys, while they are stored in the database.

## shadowdomain.py

Performs an active search and verification of subdomains, using threads for efficiency in execution. It provides detailed information, including IP addresses, associated hosts, and HTTP status codes for each subdomain. This automated and fast search helps identify online assets, strengthening the system's security posture.

## telegram.py

Complements automation, enabling automatic sending of the obtained results to a channel or group on Telegram. The results include information about active subdomains, such as host, IP, and status code. This integration with Telegram allows efficient and immediate communication of relevant data to security professionals.

## Installation

Clone the project and follow the steps below

```bash
git clone https://github.com/tumilander/shadowdomain.git
cd shadowdomain
pip install -r requirements.txt
python3 shadowdomain.py -d domain.com -w wordlist -t 10 -o /home/teste/output.txt -v -s 200 -send
```
The project has a test bot `shadowdomain_bot` in the `api_tokens.db` database, meaning you can simply insert your `chat_id` or `group_id` and run it, and it will be sent via the shadowdomain chatbot.

For testing: don't forget to search for `shadowdomain_bot` on Telegram and start it by clicking /start, if not done, it will give error `HTTP Error 400: Bad Request`. Or follow the steps below to create your own bot.

## Configuration
## Telegram Token and Chat_ID / GROUP Creation

#### Telegram

If you don't have Telegram installed yet, download it from your device's app store.

#### BotFather:

In the search field, type "BotFather" and select BotFather from the results.

#### Start a Conversation with BotFather:

Click the "Start" button to start a conversation with BotFather.

#### Create a New Bot:

Type the /newbot command to create a new bot.

#### Provide a Name for the Bot:

BotFather will ask you to provide a name for your bot. Choose a unique name and confirm.

#### Provide a Username for the Bot:

After providing the name, BotFather will ask for a username. This username must be unique and end with "bot" (e.g., "example_bot"). Confirm the username.

#### Note the Token of the Bot:

After creating the bot, BotFather will provide a token. Note this token, as you will need it to authenticate and interact with the bot.

#### Additional Settings (Optional):

BotFather offers other optional settings, such as description and image for your bot. These steps are optional.
Conclusion:

Your bot is now created! Use the token to authenticate and interact with the bot through the Telegram API.
Open the `gerador.py` script and insert your token "Your_key_here", after that, run to create the `api_tokens.db` database that will be used to connect to the API and send the results.

#### Chat_ID

To find out your Chat_ID, search for "userinfobot" on Telegram and send a test message, and it will return your user, id, First name, and language.
For a group, you need to take a message sent in the group and "Forward" it to "userinfobot," which will show you the data.
Then simply insert the id within the `telegram.py` script where "YOUR_CHAT_OR_GROUP_ID" is.

```http
@USER / GROUP
Id: 1234567890
First: User
Lang: pt-br
```
## Usage/Examples
```Javascript
usage: shadowdomain.py [-h] -d DOMAIN -w WORDLIST [-o OUTPUT] [-t {1,2,3,4,5,6,7,8,9,10}] [-v] [-s STATUS_CODE] [-send]

Subdomain Search

options:
  -h, --help            show this help message and exit
  -d DOMAIN, --domain DOMAIN
                        Target domain
  -w WORDLIST, --wordlist WORDLIST
                        Path to the wordlist file
  -o OUTPUT, --output OUTPUT
                        Path to the output file
  -t {1,2,3,4,5,6,7,8,9,10}, --threads {1,2,3,4,5,6,7,8,9,10}
                        Number of threads (1-10)
  -v, --verbose         Enable verbose mode
  -s STATUS_CODE, --status-code STATUS_CODE
                        Filter subdomains with the specified status code
  -send                 Automatically send results after search
```
-h --help -> displays options

-d --domain -> Target domain

-w --wordlist -> subdomains wordlist / Path

-o --output -> path to save file (txt)

-v --verbose -> Verbose Mode

-s --status-code -> filter by status code

-send -> sends the result to telegram group/chat after finishing

## Reference
 - [Creating Telegram Bot ](https://core.telegram.org/bots/tutorial#getting-ready)
 - [Get Chat_id/Group_id](https://ik4.es/pt/como-obter-um-id-de-grupo-ou-chat-em-telegrama/)

 - [Assetnote Wordlists](https://wordlists.assetnote.io/)

## License

The creator is not responsible for any type of use and purposes of this project.

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)


#
#
# ShadowDomain - pt-br

Este projeto consiste em uma ferramenta destinada a automatizar a busca e verificação de subdomínios em um domínio-alvo. Os scripts incluídos neste conjunto desempenham funções específicas para facilitar a coleta de informações sobre subdomínios de um domínio fornecido, ajudando assim nas atividades de segurança cibernética e teste de penetração.

Esse projeto esta sendo baseado em copilot por inteligência artificial e pode ocorrer erros.


## gerador.py

É responsável por gerar chaves criptográficas para API tokens. O script realiza a geração segura de chaves, criptografa os tokens e salva as informações no banco de dados SQLite `api_tokens.db` . Essa funcionalidade assegura a proteção dos dados sensíveis, como chaves de API, enquanto são armazenados no banco de dados.

## shadowdomain.py

Realiza uma busca ativa e verificação de subdomínios, utilizando threads para eficiência na execução. Ele oferece informações detalhadas, incluindo endereços IP, hosts associados e códigos de status HTTP para cada subdomínio. Essa busca automatizada e rápida ajuda a identificar ativos online, fortalecendo a postura de segurança do sistema.

## telegram.py

Complementa a automação, possibilitando o envio automático dos resultados obtidos para um canal ou grupo no Telegram. Os resultados incluem informações sobre subdomínios ativos, como host, IP e código de status. Essa integração com o Telegram permite uma comunicação eficiente e imediata dos dados relevantes para os profissionais de segurança.


## Instalação

Faça o git do projeto e siga abaixo

```bash
git clone https://github.com/tumilander/shadowdomain.git
cd shadowdomain
pip install -r requirements.txt
python3 shadowdomain.py -d domain.com -w wordlist -t 10 -o /home/teste/output.txt -v -s 200 -send

```
O projeto esta com um bot de teste `shadowdomain_bot` no banco de dados `api_tokens.db` , ou seja, você pode apenas inserir seu `chat_id` ou `group_id` e rodar que será enviado via chatbot do shadowdomain.

Para testes: não se esqueça de procurar no telegram por `shadowdomain_bot` e inicia-lo clicando em /start, caso não seja feito, dará erro `HTTP Error 400: Bad Request`. ou siga os passos abaixo para criar seu próprio bot.

## Configuração
## Criação de token Telegram e Chat_ID / GROUP

#### Telegram

Se ainda não tiver o Telegram instalado, baixe-o da loja de aplicativos do seu dispositivo.

#### BotFather:

No campo de pesquisa, digite "BotFather" e selecione o BotFather nos resultados.

#### Inicie uma Conversa com o BotFather:

Clique no botão "Iniciar"/"start" para começar uma conversa com o BotFather.
#### Crie um Novo Bot:

Digite o comando /newbot para criar um novo bot.
#### Forneça um Nome para o Bot:

O BotFather pedirá que você forneça um nome para o seu bot. Escolha um nome único e confirme.
#### Forneça um Nome de Usuário para o Bot:

Após fornecer o nome, o BotFather pedirá um nome de usuário. Este nome de usuário deve ser único e terminar com "bot" (por exemplo, "exemplo_bot"). Confirme o nome de usuário.
#### Anote o Token do Bot:

Após criar o bot, o BotFather fornecerá um token. Anote este token, pois você precisará dele para autenticar e interagir com o bot.
#### Configurações Adicionais (Opcional):

O BotFather oferece outras configurações opcionais, como descrição e imagem para o seu bot. Essas etapas são opcionais.
Conclusão:

Seu bot está agora criado! Use o token para autenticar e interagir com o bot por meio da API do Telegram.
Abra o script `gerador.py` e insira seu token "Sua_chave_aqui", após isso, execute para criação do banco `api_tokens.db` que servirá para realizar a conexão com a API e enviar os resultados.

#### Chat_ID

Para descobrir seu Chat_ID, procure por "userinfobot" no telgram e mande uma mensagem teste que o mesmo devolverá seu usuário, id, First name e language.
Para grupo, precisa pegar uma mensagem enviada no grupo e dar um "Forward"\"encaminhar" para "userinfobot" que lhe mostrará os dados.
Depois basta inserir o id dentro do script `telegram.py` onde está "SEU_CHAT_OU_GRUPO_ID".
```http
@USER / GROUP
Id: 1234567890
First: User
Lang: pt-br
```

## Uso/Exemplos

```javascript
usage: shadowdomain.py [-h] -d DOMAIN -w WORDLIST [-o OUTPUT] [-t {1,2,3,4,5,6,7,8,9,10}] [-v] [-s STATUS_CODE] [-send]

Busca de Subdomínios

options:
  -h, --help            show this help message and exit
  -d DOMAIN, --domain DOMAIN
                        Domínio alvo
  -w WORDLIST, --wordlist WORDLIST
                        Caminho para o arquivo de wordlist
  -o OUTPUT, --output OUTPUT
                        Caminho para o arquivo de saída
  -t {1,2,3,4,5,6,7,8,9,10}, --threads {1,2,3,4,5,6,7,8,9,10}
                        Número de threads (1-10)
  -v, --verbose         Ativa o modo verboso
  -s STATUS_CODE, --status-code STATUS_CODE
                        Filtra subdomínios com o status code especificado
  -send                 Enviar resultados automaticamente após a busca
```

-h --help -> exibe as opções

-d --domain -> Dominio alvo

-w --wordlist -> wordlist de subdomínios / Caminho

-o --output -> caminho para salvar arquivo (txt)

-v --verbose -> Modo Verbose

-s --status-code -> filtra por status code

-send -> envia o resultado para grupo/chat do telegram apos finalizar


## Referência

 - [Criação de Bot Telegram ](https://core.telegram.org/bots/tutorial#getting-ready)
 - [Captura de Chat_id/Group_id](https://ik4.es/pt/como-obter-um-id-de-grupo-ou-chat-em-telegrama/)

 - [Assetnote Wordlists](https://wordlists.assetnote.io/)
## Licença

O criador não se responsabiliza por qualquer tipo de uso e fins desse projeto.

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)


