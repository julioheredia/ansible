# ansible

![](https://media.licdn.com/dms/image/C560BAQHxkF3dudpvEQ/company-logo_200_200/0?e=2159024400&v=beta&t=cNaLAqnnv3gVvkUY3KIeKo5j_hXMSyYt7N4qg1HcJxg)

- Ansible é uma ferramenta de automação de TI. Com o Ansible é possível configurar sistemas, implantar softwares, e orquestrar tarefas na área de infraestrutura de TI.

### Usar Ansible
- No Ansible temos basicamente 2 formas de executar as nossas “receitas” nas máquinas remotas: playbook e ad hoc.

	+ Playbooks: Como são chamados os arquivos de gerenciamento de configuração. Nele é possível escrever os perfis de tarefas que serão executadas. Possui um padrão chamado YAML que torna simples a escrita e leitura dos playbooks.

	+ ADHOC: São comandos executados diretamente na linha de comando com a instrução que deseja.

#### Instação
- As compilações do Ubuntu estão disponíveis em um PPA, para configurar o PPA na sua máquina e instalar o ansible, execute esses comandos:

        $ sudo apt-get install software-properties-common
        $ sudo apt-add-repository ppa:ansible/ansible
        $ sudo apt-get update -y && sudo apt-get install -y ansible

- Rodando ansible via docker
O parâmetro -v indica o volume docker, ou seja, a pasta que será sincronizada entre o docker e o computador do usuário. Os arquivos que serão rodados pelo ansible deveram está nesta pasta.

        docker run --name rj-ansible -it -v "ansible/files/:/dados/ansible" julioheredia/ansible

####ansible commands
Estes são alguns exemplos de comandos do ansible. Estes comandos no caso vai fazer a criação do ambiente totalbus apartir de uma nova maquina.
- Playbooks:

        ansible-playbook jboss_server.yml -i host_jboss_server

- ADHOC:

        ansible -vvvv task --extra-vars "ansible_user=user ansible_password=passaword" -i hosts -m shell -a "echo Hello, World"

### Configurando Ansible
- Dentro do arquivo host_jboss_server por exemplo tera a tag jboss_server que indica a configuração pre-estabelecida para aquele ambiente, deve ser parametrizado o servidor que vai ser configurado pelo ansible

        [jboss_server] 
        172.17.0.3 ansible_user=user ansible_password=password
