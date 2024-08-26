# Provisionamento de Ambientes com Ansible

Este repositório contém um exemplo de como automatizar a instalação e configuração do WordPress, MySQL, Apache e todas as suas dependências utilizando o Ansible.

## Pré-requisitos

**VM Linux**: precisamos de 3 maquinas, sendo elas para o ansible, mysql e wordpress

## Instalação do Ansible

Para instalar o Ansible, execute o seguinte comando na maquina que será a "controladora":
`sudo apt install ansible`

## Configuração de Máquinas

O Ansible precisa saber quais máquinas devem ser provisionadas. Para isso, utilizamos um arquivo chamado `hosts`, onde são especificados os endereços de cada máquina.

## Preparando o Acesso às Máquinas

Antes de rodar o Ansible, é necessário configurar as chaves SSH para as máquinas gerenciadas. Utilize os seguintes comandos:

**Gere uma chave SSH**:
`ssh-keygen`

**Copie a chave SSH para a máquina de destino**:
`ssh-copy-id -i ubuntu-server-db.pub usuario@127.0.0.1`
Substitua `usuario` pelo nome de usuário e `127.0.0.1` pelo IP da máquina de destino.

## Executando o Ansible

Após configurar as chaves SSH e definir o arquivo `hosts`, crie um arquivo `.yml` que descreva todas as tasks que o Ansible deverá executar nas máquinas.

Para rodar o Ansible, use o comando:

`ansible-playbook arquivo.yml -i hosts -K`
`-i`: Especifica o caminho do arquivo de hosts.
`-K`: Solicita a senha de ROOT ao rodar o comando.

## Utilizando Templates e Variáveis

**Templates**: Para criar um arquivo template, basta adicionar a extensão `.j2` ao arquivo.

**Variáveis por Máquina**: Para definir variáveis específicas por grupo de máquinas, crie um arquivo `.yml` com o mesmo nome do grupo.

## Estrutura de Roles

As **roles** no Ansible representam "cargos" que executam tasks específicas. Elas ajudam a organizar e reutilizar tarefas em diferentes contextos.

## Utilizando Handlers

Os **handlers** funcionam como gatilhos, geralmente utilizados para reiniciar um serviço após uma mudança de configuração, por exemplo.
