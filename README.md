
# Ansible

Reposiório para salvar comandos e playbooks do ansible, para utilizar mais tarde




### Instalar Ansible em CentOS
```bash
  sudo yum install epel-release
  yum install ansible
```
### Instalar Ansible em Ubuntu
```bash
  sudo apt update
  sudo apt install software-properties-common
  sudo add-apt-repository --yes --update ppa:ansible/ansible
  sudo apt install ansible
```
[Instalar em outros OS ](https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html)

## Configuração do Ansible

### Configurando hosts

a primeira etapa é configurar quais máquinas desejamos gerenciar, para isso devemos configurar o seguinte arquivo:
```bash
  sudo nano /etc/ansible/hosts
```
exemplo de configuração de duas máquinas:

```bash
  # distros é o nome do grupo que desejamos executar, poderia ser qualquer nome
  [distros]
  # aqui devo colocar os endereços de ip ou os dns,
  # lembrando que sempre devem ser ipv4 e públicos
  ec2-3.endereco.com
  ec2-3.endereco.com
  
  # Aqui as variaveis na hora do ansible executar o grupo
  [distros:vars]
  ansible_ssh_private_key_file=/caminho/chave-ssh-publica.pem
```

[Mais informações para esse arquivo](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html)

### ansible.cfg
 não uma configuração adequada, mas para evitar dor de cabeça podemos desabilitar o check do host, ir em /etc/ansible/ansible.cfg e substituir o conteudo por um padrão, nesse [link](https://github.com/ansible/ansible/blob/stable-2.9/examples/ansible.cfg) e na configuração host_key_checking = False, apenas descomentar.

### Testar conexão de máquinas
```bash
  ansible nomeDoGrupo -m ping
``` 

### Comando para rodar o playbook
```bash
  ansible-playbook playbook.yml
``` 

[Informações sobre os playbooks](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_intro.html) ou [Criando primeiro playbook](https://docs.ansible.com/ansible/latest/getting_started/get_started_playbook.html)
