# Tutorial - Compilar Kernel FreeBSD e Debian

### Descrição de Ambiente:
- SO hospedeiro: Windows 10 Pro
- Software de Virtualização: Virtual Box 5.2.8
- Hardware Host: 
      
    - i5-8400
    - 16gb RAM

- Versão dos SO's:
   - Debian GNU/Linux 10 
   - Kernel : 4.19.0-5-amd64
   - Tamanho lib/modules/4.19.0-5-amd64 = 258mb
   - FreeBSD   12
   - Kernel:


## **Compilação no Debian:**

### Checando a versão atual do kernel
![Checando a versão](https://i.imgur.com/ET65fG0.png)

### Entrando como root

![root](https://i.imgur.com/be4kyk3.png)

### Adicionando repositório das dependências

> Caminho etc/apt/sources.list

![Lista de repositórios](https://i.imgur.com/kr81MyK.png)

### Baixando a última versão estável do kernel

> wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.2.9.tar.xz

![comando para baixar](https://i.imgur.com/vPiRySI.png)

### Descompactando na pasta /src

> tar xvf linux-5.2.9.tar.xz -C /usr/src

### Acessar o diretório com o código-fonte do kernel

> cd /usr/src/linux- 5.2.9

### Fazer uma cópia da configuração atual 

> cp -v /boot/config-$(uname -r) .config

### Configurar o kernel com as opções específicas para a arquitetura e módulos que deseja compilar

> make localmodconfig

![localmodconfig](https://i.imgur.com/LFOzyhf.png)

> make menuconfig

![menuconfig](https://i.imgur.com/kVA6NDp.png)
![Imgur](https://i.imgur.com/8pZNJq6.png)

###  Após gravar as configurações, compile e instale:

> make -j2 //onde 2 é o número de núcleos (nproc) 

![makej2](https://i.imgur.com/yDzsB1s.png)

> make modules_install

![Imgur](https://i.imgur.com/AMeFJqO.png)

> make install

![Imgur](https://i.imgur.com/fd8uKzy.png)

### Checando o tamanho da pasta modules

> du -sh 5.2.0-2-amd64/

![Imgur](https://i.imgur.com/Spefpec.png)

### Checando a versão do kernel

Após reiniciar a máquina abra o terminal

> uname -r

![Imgur](https://i.imgur.com/wTnn9S3.png)


## **Compilação no FreeBSD:**

### Acessar o arquivo de configuração e criar uma cópia da configuração genérica: 

> cd /usr/src/sys/amd64/conf 
> cp GENERIC MYKERNEL

![Imgur](https://i.imgur.com/lSrsWM5.png)

### Altere a identificação do kernel GENERIC e desabilite os módulos e dispositivos não necessários 

> vi MYKERNEL 

ident GENERIC → ident MYKERNEL

### Volte para o diretório raiz do fonte: 

> cd /usr/src

### Compile o novo kernel:

> make buildkernel KERNCONF=MYKERNEL

#### E espere:
![Imgur](https://i.imgur.com/Rf3iXxH.png)

### Instale o novo kernel: 

> make installkernel KERNCONF=MYKERNEL

#### E espere novamente:

![Imgur](https://i.imgur.com/OKGahhJ.png)


### Para verificar o tamanho do novo kernel e antigo: 

> cd /boot/kernel 

> du -sh 

> cd /boot/kernel.old 

> du -sh - Reinicie o sistema. 

![Imgur](https://i.imgur.com/t38c1jJ.png)



















