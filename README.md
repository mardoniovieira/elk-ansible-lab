# elk_ansible_lab2

## Configuração das máquinas
- Cenário: um máquina de gerenciamento (ubuntuserver1), que hospeda o Ansible, e uma máquina gerenciada (ubuntuserver2).
- SO das vms: Ubuntu server 18.04
- Hostname das vms:
  - Máquina de gerenciamento: ubuntuserver1
  - Máquina gerenciada: ubuntuserver2
- Usuários das vms: um usuário sudo em comum entre as máquinas

## Parte 1 - Configuração do Ansible

### Python
O Anseble usa o interpretador Python para executar seus módulos. Então, é necessário instalar o Python 2 na máquina gerenciada (ubuntuserver2)
```
$ sudo apt update
$ sudo apt install python
```

### SSH
Na máquina de gerenciamento (ubuntuserver1), gere a chave ssh sem senha
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

## Parte 2 - Instalação do elk

Na máquina de gerenciamento (ubuntuserver1), cole os arquivos deste repositório, exeto READM.md e ansible.cfg, em /etc/ansible. Ou apague todos os aquivos do diretório ansible e clone este repositório lá
```
$ sudo rm -R /etc/ansible/*
$ sudo git clone https://github.com/sayonarasantos/elk_ansible_lab2.git /etc/ansible/
```
Por fim, execute as playbooks
```
$ cd ansible
$ ansible-playbook -K pb_control_vm.yml
$ ansible-playbook -K pb_controlled_vms.yml
```
