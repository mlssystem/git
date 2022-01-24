# ALGUNS COMANDOS GIT


## Ajuda


##### Geral
	git help
	git help --all
	git help <qualquer_comando_git>
	git <comando_git> -help


## Versão
	git --version


## Configure o Git

##### Setar usuário
	git config --global user.name "Leonardo Comelli"

##### Setar email
	git config --global user.email "email"

##### Setar editor
	git config --global core.editor vim


## Repositório Local

### Criar diretório Git
	mkdir nome_projeto

### Criar arquivo
	touch nome_arquivo

### Inicialize Git
	git init

### Verificar estado dos arquivos/diretórios
	git status

### Adicionar arquivo/diretório

##### Adicionar um arquivo em específico
	git add nome_arquivo

##### Adicionar um diretório em específico
	git add nome_diretorio

##### Adicionar todos os arquivos/diretórios
	git add .

### Comitar arquivo/diretório

##### Arquivo
	git commit nome_arquivo

##### Comitar vários arquivos
	git commit nome_arquivo meu_outro_arquivo

##### Comitar informando mensagem
	git commit nome_arquivo -m "Mensagem"

#### Adicionar e commitar
	git commit -am "Mensagem"

### Remover arquivo/diretório

##### Remover arquivo
	git rm nome_arquivo

##### Remover diretório
	git rm -r diretorio

### Visualizar histórico

##### Exibir histórico
	git log

##### Exibir histórico commit com hash e mensagem
	git log --oneline

### Desfazendo operações

##### Desfazendo alteração local (antes de adicionar modificações)
Este comando deve ser utilizando enquanto o arquivo não foi adicionado na **staged area**.

	git checkout -- nome_arquivo

##### Desfazendo alteração local (depois adicionar modificações)
Este comando deve ser utilizando quando o arquivo já foi adicionado na **staged area**.
	git reset HEAD nome_arquivo

Se o resultado abaixo for exibido, o comando reset *não* alterou o diretório de trabalho.

	Unstaged changes after reset:
	M	nome_arquivo

A alteração do diretório pode ser realizada através do comando abaixo:

	git checkout nome_arquivo

## Repositório Remoto

### Exibir os repositórios remotos
	git remote
	git remote -v

### Vincular repositório local com um repositório remoto
	git remote add origin git@github.com:mlssystem/git.git

### Exibir informações dos repositórios remotos
	git remote show origin

### Renomear um repositório remoto
	git remote rename origin git

### Desvincular um repositório remoto
	git remote rm git

### Enviar arquivos/diretórios para o repositório remoto

O primeiro **push** de um repositório deve conter o nome do repositório remoto e o branch.

	git push -u origin master

Os demais **pushes** não precisam dessa informação

	git push

### Atualizar repositório local de acordo com o repositório remoto

##### Atualizar os arquivos no branch atual
	git pull

##### Buscar as alterações, mas não aplica-las no branch atual
	git fetch

### Clonar um repositório remoto já existente
	git clone git@github.com:mlssystem/git.git

### Tags

##### Criando uma tag leve
	git tag vs-1.1

##### Criando uma tag anotada
	git tag -a vs-1.1 -m "Minha versão 1.1"

##### Criando uma tag assinada
Para criar uma tag assinada é necessário uma chave privada (GNU Privacy Guard - GPG).

	git tag -s vs-1.1 -m "Minha tag assinada 1.1"

##### Criando tag a partir de um commit (hash)
	git tag -a vs-1.2 9fceb02

##### Criando tags no repositório remoto
	git push origin vs-1.2

##### Criando todas as tags locais no repositório remoto
	git push origin --tags

### Branches
O **master** é o branch principal do GIT.

O **HEAD** é um ponteiro *especial* que indica qual é o branch atual. Por padrão, o **HEAD** aponta para o branch principal, o **master**.

##### Criando um novo branch
	git branch nova_branch

##### Trocando para um branch existente
	git checkout nova_branch

Neste caso, o ponteiro principal **HEAD** esta apontando para o branch chamado nova_branch.

##### Criar um novo branch e trocar
	git checkout -b segunda_nova_branch

##### Voltar para o branch principal (master)
	git checkout master

##### Resolver merge entre os branches
	git merge nova_branch

Para fazer o *merge*, tem que estar no branch que deverá receber as alterações. O *merge* pode ser automático ou manual. O merge automático será feito em arquivos textos que não sofreram alterações nas mesmas linhas, já o merge manual será feito em arquivos textos que sofreram alterações nas mesmas linhas.

A mensagem indicando um *merge* manual será:

	Automerging nome_arquivo
	CONFLICT (content): Merge conflict in nome_arquivo
	Automatic merge failed; fix conflicts and then commit the result.


##### Apagando um branch
	git branch -d nova_branch

##### Listar branches
	git branch

###### Listar branches com informações dos últimos commits
	git branch -v

###### Listar branches que já foram fundidos (merged) com o **master**
	git branch --merged

###### Listar branches que não foram fundidos (merged) com o **master**
	git branch --no-merged

##### Criando branches no repositório remoto

###### Criando um branch remoto com o mesmo nome
	git push origin nova_branch

###### Criando um branch remoto com nome diferente
	git push origin nova_branch:new-branch

##### Baixar um branch remoto para edição
	git checkout -b nova_branch origin/nova_branch

##### Apagar branch remoto
	git push origin:nova_branch

### Reescrevendo o histórico

##### Alterando mensagens de commit
	git commit --amend -m "Nova mensagem"

##### Alterar últimos commits
Alterando os três últimos commits

	git rebase -i HEAD~3

O editor de texto será aberto com as linhas representando os três últimos commits.

	pick f7f3f6d changed my name a bit
	pick 310154e updated README formatting and added blame
	pick a5f4a0d added catfile

Altere para edit os commits que deseja realizar alterações.

	edit f7f3f6d changed my name a bit
	pick 310154e updated README formatting and added blame
	pick a5f4a0d added catfile

Feche o editor de texto.

Digite o comando para alterar a mensagem do commit que foi marcado como *edit*.

	git commit –amend -m “Nova mensagem”

Aplique a alteração

	git rebase --continue

# Contribuições

Sinta-se a vontade para realizar adicionar mais informações ou realizar correções.
