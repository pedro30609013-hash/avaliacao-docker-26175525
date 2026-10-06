# Respostas · Avaliação Prática de Docker · ViaSerra Transportes (Turma C)

Nome:
Matrícula:
Usuário do GitHub:
Usuário do Docker Hub:

Responda com as suas palavras e com o que aconteceu na SUA máquina. Resposta curta e certa vale mais
do que texto longo copiado. Resposta que contradiz o seu próprio Dockerfile vale zero.

## Parte 1 · Dockerfile do portal

1. Qual imagem base você usou e qual o tamanho final da imagem do portal (saída de `docker images`)? 

A imagem utilizada como base foi a imagem oficial do Nginx nginx:1.27-alpine. O conteúdo do portal foi copiado para /usr/share/nginx/html/, que é o diretório utilizado pelo Nginx para disponibilizar a página.

2. Em qual pasta do container o Nginx procura os arquivos do site? Mostre o comando que você usou para conferir que o `index.html` está lá dentro.

   O Nginx procura os arquivos do site na pasta /usr/share/nginx/html/. Para verificar se o index.html estava dentro do container, utilizei o comando docker exec teste-portal ls /usr/share/nginx/html/.

## Parte 2 · Docker Hub

3. Nome completo da imagem publicada e link público do repositório no Docker Hub.

pedrohenriquesantos7/viaserra-portal:1.0-26175525

https://hub.docker.com/r/pedrohenriquesantos7/viaserra-portal?utm_source=chatgpt.com

4. Se você mudar o HTML, quais comandos precisa rodar para que a versão nova chegue ao Docker Hub?

Para mudar o html, precisei usar os comandos:

docker build -t pedrohenriquesantos7/viaserra-portal:1.0-26175525 ./portal
docker push pedrohenriquesantos7/viaserra-portal:1.0-26175525

## Parte 3 · Página de manutenção

5. Preencha uma linha por defeito encontrado. Defeito inexistente listado aqui desconta pontos.

5. Preencha uma linha por defeito encontrado. Defeito inexistente listado aqui desconta pontos.

| # | Instrução | O que estava errado | O que você viu acontecer | Como corrigiu |
|---|---|---|---|---|
| 1 | COPY pagina/ . | A pasta pagina não existia. A pasta correta era site |O docker build apresentou erro informando que a pasta /pagina não foi encontrada. | Alterei para COPY site/ .|
| 2 |WORKDIR /usr/share/nginx |O diretório estava incorreto para os arquivos que deveriam ser servidos pelo Nginx. |A página de manutenção não era carregada corretamente. |Alterei para WORKDIR /usr/share/nginx/html |
| 3 | CMD ["nginx"]| O Nginx não estava configurado para permanecer em primeiro plano no container.|O container não permanecia em execução corretamente. |Alterei para CMD ["nginx", "-g", "daemon off;"] |

6. Qual a diferença entre `-p 7042:80` e `-p 80:7042` no `docker run`? Qual dos dois números é a porta do container?

No comando -p 7042:80, o primeiro número (7042) é a porta do computador (host) e o segundo número (80) é a porta do container. Já em -p 80:7042, a porta do computador seria 80 e a porta do container seria 7042.

## Parte 4 · Primeiro docker-compose

7. Escreva os dois comandos `docker run` que fariam o mesmo que o seu `docker-compose.yml`.

8. Qual comando derruba os dois containers de uma vez?

## Verificador

9. Código de conclusão impresso pelo verificador:

```
(cole aqui)
```
