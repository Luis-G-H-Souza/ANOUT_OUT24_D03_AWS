# CRIANDO INSTANCIA EC2:

1.  Para criar, abra o Console AWS e vá até a página do EC2 → [Painel | EC2 | us-east-2](https://us-east-2.console.aws.amazon.com/ec2/home?region=us-east-2#Home:)
2.  Procure na sua tela o botão de **Executar instância**
    ![Executar instancia](/data/image.png)
3.  Após isso, vá até **Nome e tags:**
    ![Executar instancia](/data/image-0.png)
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
    - Selecione o Security Group
      ![alt text](/data/image-5.png)
8.  Ao lado, você verá o quadro **Resumo**. Agora, basta clicar em **Executar instância**.
    ![alt text](/data/image-6.png)
