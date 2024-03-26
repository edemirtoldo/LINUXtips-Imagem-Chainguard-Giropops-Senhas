# LINUXtips-Imagem-Chainguard-Giropops-Senhas

Repo com o Desafio Day3 do PICK 2024, utilizando imagens da Chainguard

Utilizamos para o desafio a aplicação Giropops-Senhas

https://github.com/badtuxx/Giropops-Senhas


Build da imagem do Redis 
```bash
docker build -t edemirtoldo/redis-server:1.0 -f Dockerfile.redis .
```

Build da imagem da aplicação

```bash
docker build -t edemirtoldo/edemirtoldo/linuxtips-imagem-chainguard-giropops-senhas:1.0 -f Dockerfile.app .
```

Trivy é uma ferramenta de segurança de código aberto usada para detectar vulnerabilidades em contêineres e imagens de contêineres. Ele verifica imagens de contêineres em busca de pacotes vulneráveis, bibliotecas desatualizadas e outras ameaças de segurança conhecidas.
Como instalar o trivy: https://aquasecurity.github.io/trivy/v0.50/getting-started/installation/

Vamos utilizar o Trivy para detectar vulnerabilidades nas images.

Verificando a imagem do redis.
```bash
trivy image edemirtoldo/redis-server:1.0
```

![trivy1](https://github.com/edemirtoldo/LINUXtips-Imagem-Chainguard-Giropops-Senhas/blob/main/pictures/1.png)


Verificando a imagem da aplicação.
```bash
trivy image edemirtoldo/edemirtoldo/linuxtips-imagem-chainguard-giropops-senhas:1.0
```

![trivy2](https://github.com/edemirtoldo/LINUXtips-Imagem-Chainguard-Giropops-Senhas/blob/main/pictures/2.png)

Agora que temos certeza que as imagens são seguras vamos executar a aplicação. 

```bash
docker network create app_network
docker run -d --name redis-server --network app_network edemirtoldo/redis-server:1.0
docker run -itd -p 5000:5000 --network app_network --name app edemirtoldo/edemirtoldo/linuxtips-imagem-chainguard-giropops-senhas:1.0
```

Acessar o link:
http://localhost:5000/

![Localhost](https://github.com/edemirtoldo/LINUXtips-Imagem-Chainguard-Giropops-Senhas/blob/main/pictures/3.png)




