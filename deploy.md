# DEPLOY DO APLICATIVO NO EC2:

1. Acesse a instância da aplicação via SSH:

```bash
ssh -i "seu-arquivo.pem" ec2-user@<IP-da-instância-aplicação>
```

2. Já dentro da sua instância EC2, atualize o Sistema Operacional:

```bash
sudo yum update -y          # Para Amazon Linux
sudo apt update && sudo apt upgrade -y  # Para Ubuntu
```

3. Instale o Node.js e npm:

```bash
# Para Amazon Linux 2
curl -sL https://rpm.nodesource.com/setup_18.x | sudo bash -
sudo yum install -y nodejs

# Para Ubuntu
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs
```

4. Instale o Git:

```bash
sudo yum install -y git     # Amazon Linux
sudo apt install -y git     # Ubuntu
```

5. Após isso, clone o repositório do app:

```bash
git clone <URL-do-repositório>
```

Substitua <URL-do-repositório> pelo link HTTPS ou SSH do repositório.

6. O Git irá pedir seu NAME, coloque o nome do seu GitHub.
7. Ele irá pedir também sua PASSWORD, passe seu **Personal Access Tokens (classic)**, você o encontra dentro da sua conta GitHub, em Settings, Developer Settings, Personal Access Tokens, e por fim Tokens (classic).

8. Navegue até o diretório do app

```bash
cd nome-do-repositorio
```

9. Instale as dependências do app

```bash
npm install
```

10. Configure as variáveis de ambiente

```bash
touch .env
nano .env
```

Aqui está um exemplo:

```bash
DB_CONNECTION=postgres
DB_HOST=127.0.0.1
DB_PORT=5432
DB_USERNAME=postgres
DB_PASSWORD=senhadopostgres

JWT_SECRET=supersecret
USER_EMAIL=usuario.teste@example.com
USER_PASSWORD=Senha123!
```

Não se esqueça de colocar o IPv4 publico da EC2 que o app está rodando, na variável DB_HOST, e nem de colocar as informações do usuário do banco de dados, nas variáveis DB_USERNAME e DB_PASSWORD.

Salve e feche (Ctrl + O, Enter e Ctrl + X no Nano).

11. Inicie o aplicativo:

```bash
npm run start:dev
```
