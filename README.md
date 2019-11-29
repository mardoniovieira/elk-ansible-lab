# elk_ansible_lab2

## Parte 1 - Configuração do Ansible

Cenário: um máquina de gerenciamento (ubuntuserver1), que hospeda o Ansible, e uma máquina gerenciada (ubuntuserver2).

### Python
O Anseble usa o interpretador Python para executar seus módulos. Então, é necessário instalar o Python 2 na máquina gerenciada (ubuntuserver2)
```
$ sudo apt update
$ sudo apt install python
```

### SSH
Na máquina de gerenciamento (ubuntuserver1), gere a chave ssh
```
$ ssh-keygen
```
Copie-a para a máquina gerenciada
```
$ ssh-copy-id ip_m_controlled
```
E acesse a máquina gerenciada para verificar o funcionamento da chave
```
$ ssh ip_m_controlled
$ exit
```

### Instalação Ansible
A instalação deve ser feita na máquina de gerenciamento (ubuntuserver1).
Para obter a versão mais recente do Ansible, adicione o repositório no sistema e instale o ansible desse repositório.
Antes disso, verifique se o pacote software-properties-common está instalado (esse pacote facilita o gerenciamento de repositórios de software independentes)
```
$ sudo apt install software-properties-common
```
Agora, adicione o pacote do Ansible e atualize o índice de pacotes do sistema
```
$ sudo apt-add-repository ppa:ansible/ansible
$ sudo apt update
```
E finalmente instale o Ansible
```
$ sudo apt install ansible
```
Para verificar a instalação, digite
```
$ ansible --version
```

-----------------------------------

## Parte 1 - Instalação do elk

Clone este repositório no diretório /etc/ansible da máquina de gerenciamento (ubuntuserver1)
```
$ git clone ..
```
E execute as playbooks
```
$ ansible-plabook -K pb_control_vm.yml
$ ansible-plabook -K pb_controlled_vms.yml
```
