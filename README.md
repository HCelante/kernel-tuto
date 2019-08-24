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
### Adicionando repositório das dependências
> Caminho etc/apt/sources.list
![Lista de repositórios]()

### Baixando a última versão estável do kernel
> wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.2.9.tar.xz
![comando para baixar]()

### Descompactando na pasta /src
> tar xvf linux-5.2.9.tar.xz -C /usr/src

### Acessar o diretório com o código-fonte do kernel
> cd /usr/src/linux- 5.2.9

### Fazer uma cópia da configuração atual 
> cp -v /boot/config-$(uname -r) .config

