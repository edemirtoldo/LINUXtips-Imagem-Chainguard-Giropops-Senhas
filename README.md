# LINUXtips-Imagem-Chainguard-Giropops-Senhas

Repo com o desafio Day3 utlizando imagens da Chainguard

Utilizamos para o desafio a aplicação Giropops-Senhas

https://github.com/badtuxx/Giropops-Senhas


docker build -t edemirtoldo/redis-server:1.0 -f Dockerfile.redis .


docker build -t edemirtoldo/edemirtoldo/linuxtips-imagem-chainguard-giropops-senhas:1.0 -f Dockerfile.app .

 
 
 
docker network create app_network

docker run -d --name redis-server --network app_network edemirtoldo/redis-server:1.0


docker run -itd --rm -p 5000:5000 --network app_network --name app edemirtoldo/edemirtoldo/linuxtips-imagem-chainguard-giropops-senhas:1.0




 
trivy image edemirtoldo/edemirtoldo/linuxtips-imagem-chainguard-giropops-senhas:1.0
 
trivy image edemirtoldo/redis-server:1.0

