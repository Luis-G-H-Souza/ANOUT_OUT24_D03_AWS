# INSTÂNCIA EC2:

## CONSIDERAÇÕES INICIAIS ANTES DA CRIAÇÃO DA INSTÂNCIA EC2:

Antes de partir para a criação da instância EC2, temos alguns detalhes que se configurados previamente ao EC2, facilita o processo de criação, aqui está um tutorial para a configuração desses detalhes:

[**Tutorial de criação de VPC - Virtual Private Cloud**](https://israelbarberino-dev.notion.site/VPC-Virtual-Private-Cloud-12ea01dcbda18000bd5aee45e22568ad)

[**Tutorial de criação de SSH - Key Pair**](https://israelbarberino-dev.notion.site/SSH-Key-Pair-12ea01dcbda180dbb2baea41bef444ef)

[**Tutorial de importação das chaves SSH**](https://israelbarberino-dev.notion.site/Importando-seu-par-de-chaves-SSH-do-Git-na-AWS-12ea01dcbda1807c8512f522d4768cce)

## CRIANDO INSTÂNCIA EC2:

1.  Para criar, abra o Console AWS e vá até a página do EC2 → [Painel | EC2 | us-east-2](https://us-east-2.console.aws.amazon.com/ec2/home?region=us-east-2#Home:)
2.  Procure na sua tela o botão de **Executar instância**

    ![Executar instância](/data/image.png)

3.  Após isso, vá até **Nome e tags:**
    ![Executar instância](/data/image-0.png)
4.  Em seguida. crie as seguintes Tags:
    <aside>

            Importante: Essas tags são importantes, pois estão de acordo com os atributos da política (ABAC) atribuída às contas do Scholarship Program.

    ![Tags](/data/image-1.png)

5.  Após isso, em **Imagens de aplicação e de sistema operacional (imagem de máquina da Amazon)**, escolha a imagem Ubuntu.
    ![Ubuntu](/data/image-2.png)
6.  Vá até **Par de Chaves(login)** e selecione seu par de chaves SSH (ou crie uma clicando em **Criar novo par de chaves**)
    ![Par de chaves](/data/image-3.png)
7.  Em **Configuração de rede**, clique em editar e informe as suas configurações de rede e segurança:
    - Informe sua VPC
    - Informe a Sub-rede
    - Habilite IP público
    - Selecione o Security Group ([**Para a criação do SG, clique aqui**](https://israelbarberino-dev.notion.site/Security-Group-12ea01dcbda1806eaf3cc8a209fe9424))
      OBS: No tutorial acima, é mostrado como abrir a porta TCP 8080, mas para essa aplicação, troque para 3000 e permita as entradas HTTP e HTTPS.
      ![alt text](/data/image-5.png)
8.  Ao lado, você verá o quadro **Resumo**. Agora, basta clicar em **Executar instância**.

    ![alt text](/data/image-6.png)
