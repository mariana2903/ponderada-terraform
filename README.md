# ponderada-terraform

Para iniciar o tutorial é necessário abrir o terminal powershell como administrador e instalar o terraform CLI com o seguinte comando:

```
 Invoke-WebRequest -Uri https://releases.hashicorp.com/terraform/1.0.11/terraform_1.0.11_windows_amd64.zip -OutFile terraform.zip
```

E assim será feita a instalação pelo terminal

![image](https://github.com/mariana2903/ponderada-terraform/assets/99264876/4b8f7b9e-fb9d-4329-9624-03c62245d458)

Depois de feito a instalação é necessário extrair o arquivo zip e para isso é necessário utlizar o comando a seguir:

```
Expand-Archive -Path terraform.zip -DestinationPath C:\terraform
```

Para verifcar se está instalado e funcionando pode ser utilizado o comando 'terraform -v'

Em seguida, depois de concluir a instalação do terraform CLI é necessário baixar o instalador da AWS CLI com o comando a seguir:

```
Invoke-WebRequest -Uri https://awscli.amazonaws.com/AWSCLIV2.msi -OutFile AWSCLIV2.msi
```

Depois disso fazer a instalar com o comando 

```
Start-Process msiexec.exe -Wait -ArgumentList '/I AWSCLIV2.msi /quiet'
```

E por fim verificar o funcionamento com 'aws --version'

Depois de finalizado esse processo de instalação é necessário executar 'aws configure' para configurar as credenciais da AWS

Abrindo no dirétorio 'cd ~\.aws\' e depois notepad credentials é necessário adicionar o conteúdo a seguir, das chaves da AWS e no lugar de 'YOUR_ACCESS_KEY_ID', ' YOUR_SECRET_ACCESS_KEY' e 'YOUR_SESSION_TOKEN', substituir por suas credenciais, no caso da AWS Academy eles ficam na aba de início do Lab, depois de clicar no botão "AWS Details" e depois "Show" em AWS CLI

```
[default]
aws_access_key_id = YOUR_ACCESS_KEY_ID
aws_secret_access_key = YOUR_SECRET_ACCESS_KEY
aws_session_token = YOUR_SESSION_TOKEN
```

Depois de todo esse processo de instalação e configuração é necessário criar um arquivo chamado "main.tf" com o conteúdo a seguir 

```
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "example" {
  ami           = "ami-0c02fb55956c7d316"  # Amazon Linux 2 AMI (HVM), SSD Volume Type
  instance_type = "t2.micro"

  tags = {
    Name = "TerraformExample"
  }
}
```

Criado o arquivo é necessário abrir novamento o terminal no dirétorio que está o arquivo main.tf e executar "terraform init"

![image](https://github.com/mariana2903/ponderada-terraform/assets/99264876/87e33523-f6a2-4beb-b186-bd11789929df)

Em seguida "terraform plan" e depois "terraform apply"

E por fim é possível conferir a instância que foi criada na AWS 

![image](https://github.com/mariana2903/ponderada-terraform/assets/99264876/26bb55e5-f746-480c-bfce-4ed669a76c74)






