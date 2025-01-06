# CONFIGURANDO INSTÂNCIA DO BANCO DE DADOS

1. Acesse a instância da aplicação via SSH:

```bash
ssh -i "seu-arquivo-chave.pem" ec2-user@<IP-público-da-instância-banco>
```

2. Já dentro da sua instância EC2, atualize o Sistema Operacional:

```bash
sudo yum update -y          # Para Amazon Linux
sudo apt update && sudo apt upgrade -y  # Para Ubuntu
```

3. Instale o PostgreSQL:

```bash
# Para Amazon Linux 2
sudo amazon-linux-extras enable postgresql14
sudo yum install -y postgresql-server postgresql-contrib

# Para Ubuntu
sudo apt install -y postgresql postgresql-contrib
```

4. Inicie e configure o PostgreSQL:

```bash
# Iniciar o serviço
sudo systemctl start postgresql
sudo systemctl enable postgresql

# Acessar o PostgreSQL como usuário "postgres"
sudo -i -u postgres
```

5. Entre no Terminal do PostgreSQL
   No shell do sistema operacional (postgres@ip-10-0-7-65:~$), digite:

```bash
psql
```

Agora você estará no terminal do PostgreSQL, que se parece com isto:

```bash
postgres=#
```

6. Crie o Banco de Dados e Usuário:

```sql
-- Crie o banco de dados
CREATE DATABASE "challengeDB";

-- Crie um usuário e defina uma senha
CREATE USER seu_usuario WITH PASSWORD 'minha_senha';

-- Dê permissões ao usuário
GRANT ALL PRIVILEGES ON DATABASE "challengeDB" TO postgres;

\q  -- Saia do terminal PostgreSQL

exit -- Vá para o terminal do Ubuntu
```

Caso você esteja utilizando o usuario padrão postgres, ao invés de criar um usuario, como descrito na linha 2 acima, utilize esse comando para colocar sua senha do usuario postgres

```sql
ALTER USER postgres PASSWORD 'nova_senha';
```

7. Agora que você está no shell do sistema operacional, configure o PostgreSQL:

   7.1. Abra o arquivo de configuração:

   ```bash
   sudo nano /etc/postgresql/<versão>/main/postgresql.conf
   ```

   Substitua <versão> pela versão instalada (por exemplo, 16).

   Em caso de duvida, utilize esse comando para ver a versão instalada do PostgreSQL:

   ```bash
   psql --version
   ```

   7.2. Localize a linha:

   ```plaitext
   #listen_addresses = 'localhost'
   ```

   Apague o # e altere para:

   ```plaitext
   listen_addresses = '*'
   ```

   Ou especifique o IP privado da instancia EC2 que está rodando o app.

   7.3. Salve e feche (Ctrl + O, Enter e Ctrl + X no Nano) e reinicie o PostgreSQL:

   ```bash
   sudo systemctl restart postgresql
   ```

8. Configuração do Arquivo pg_hba.conf:

   8.1. Edite o arquivo pg_hba.conf:

   ```bash
   sudo nano /etc/postgresql/<versão>/main/pg_hba.conf
   ```

   Substitua <versão> pela versão instalada.

   8.2. Adicione a seguinte linha ao final:

   ```plaintext
   host    all             all             10.0.0.0/16            md5
   ```

   Isso permite conexões de qualquer IP na sub-rede privada da VPC.

   8.3. Salve e feche (Ctrl + O, Enter e Ctrl + X no Nano) e reinicie o PostgreSQL:

   ```bash
   sudo systemctl restart postgresql
   ```
