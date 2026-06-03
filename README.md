# Desafio Técnico: Analista de Suporte a Infraestrutura Junior - Sensedia
## Candidato: Flávio Zini


## Objetivo

Este repositório contém a entrega do desafio técnico, demonstrando conhecimentos básicos em Containers, Versionamento com Git, Consumo de APIs REST e Documentação. A aplicação `httpbin` foi disponibilizada via Docker e seus endpoints foram validados.


## Processo Utilizado


1\. Infraestrutura Cloud: Foi provisionada uma instância EC2 (Ubuntu) na AWS para hospedar a aplicação, com liberação de tráfego HTTP.

2\. Containerização (Docker):Acesso à instância via SSH, instalação do serviço Docker e execução da imagem pública solicitada (`kennethreitz/httpbin`).

3\. Mapeamento de Rede: O container foi configurado para mapear a porta 80 do servidor para a porta 80 do container.


## Etapa 1 - Criar a instância EC2 (Free Tier)

AWS EC2 Ubuntu 26.04:

![CriaçãoEC2](evidencias/instancia-aws.png)


## Etapa 2 - Conexão via PowerShell

Acessar a instância via SSH

![AcessarEC2](evidencias/ssh.png)


## Etapa 3 - Atualizar servidor

Comandos utilizados:

`sudo apt update`
`sudo apt upgrade -y`

![Atualizar](evidencias/atualiza-sv.png)


## Etapa 4 - Instalar Docker

Comandos utilizados:

`sudo apt install docker.io -y`
`docker --version`

![Versão Docker](evidencias/docker-version.png)


## Etapa 5 - Habilitar Docker

Comandos utilizados:

`sudo systemctl enable docker`
`sudo systemctl start docker`
`sudo systemctl status docker`

![Habilitar Docker](evidencias/habilitar-docker.png)


## Etapa 6 - Baixar a imagem

Comandos utilizados:

`sudo docker pull kennethreitz/httpbin`

![Imagem Docker](evidencias/docker-pull.png)


## Etapa 7 - Validar imagem

Comandos utilizados:

`sudo docker images`

![Validar Imagem Docker](evidencias/docker-image.png)


## Etapa 8 - Subir o Docker

Comando de Execução:

`sudo docker run -d -p 80:80 kennethreitz/httpbin`

![Subir Docker](evidencias/subir-docker.png)

![Docker PS](evidencias/docker-ps.png)


## Etapa 9 - Testar API (Consumo de APIs REST)


### Abaixo estão as capturas de tela/saídas dos comandos executados validando os endpoints da aplicação através do IP público da AWS.


1. Teste de Método GET (`/get`)

Comando: `curl http://18.229.163.17/get`

Evidência:

![Teste GET](evidencias/get.png)


2. Teste de Método POST (`/post`)

Comando: `curl -X POST "http://18.229.163.17/post" -d "Vaga: Analista de Suporte..." -d "Candidato: Flavio Zini"`

Resultado: Os dados enviados no payload foram refletidos no bloco `form` da resposta.

Evidência:

![Teste POST](evidencias/post.png)


3. Teste de Cabeçalhos e IP (`/headers` e `/ip`)

Evidência Headers:

![Teste Headers](evidencias/headers.png)

Evidência IP:

![Teste IP](evidencias/ip.png)


## Etapa 10 - Coleta de evidências extras

### Logs:

![Logs](evidencias/docker-logs.png)

### Inspect:

![Inspect](evidencias/docker-inspect.png)

### Processos:

![Processos](evidencias/docker-top.png)
