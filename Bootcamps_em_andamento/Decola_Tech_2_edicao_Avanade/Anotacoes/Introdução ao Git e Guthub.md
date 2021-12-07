# Git e Github

## Comandos básicos CLI

- **ls:** equivalente ao 'dir'
- **cd:** Change Directory
- **clear** ou **Alt + L**: equivalente ao 'cls'
- **mkdir: **make directory (usar com sudo)
- **del: **deletar arquivos
- **rm:** remove pastas (-rf)
- **mv:** mover arquivos

## Como Funciona o Git

Utiliza o SHA1: **Algoritmo de encriptação** (caracteres de 40 dígitos). Isso o torna muito seguro, possibilitando sua **distribuição**

## Objetos internos do Git

- Blobs: contém os arquivos. Contém o tipo do objeto (bloob), o tamanho, o \0 e o conteúdo do arquivo. Ḿetadados. Possui um SHA1
- Trees: armazena blobs. Metadados: \0, aponta para blobs, tem tamanhos e o nome dos arquivo. Também podem apontar para outras trees. Elas também tem seu próprio SHA1
- Commits: junta tudo. Aponta para arvorés, para o commit anterior, para o autor, para uma mensagem e uma data. Também possui SHA1. 

## Chaves SSH e Tokens

- **Chave SSH:** Autenticação em 2 fatores. Assinatura da máquin
- Passo a passo para instalação
  - Acessar o **GIthub > Settings > SSH and GPG keys > New SSH key**
  - Acessar o CLI e digitar o comando para gerar a chave: **ssh-keygen -t ed25519 -C**  **__seu_email_**
  - acessar a pasta em que foi criada a chave e ler o conteúdo do arquivo **.pub**
  - Colar o conteúdo no GIthub e salvar
  - Depois, digitar **eval $(ssh-agent -s)** no CLI para criar o agente que rodará em segundo plano
  - Adicionar a  chave **privada** ao agente  



## Comandos básicos Git

- **git init:** inicializar o git na pasta. "Criar um repositório". Navege até a pasta e **git init**. Antes de começar a utilizar o repositório que foi inicializado, algumas configurações podem ser necessárias, principalmente se for a primeira vez usando o git: Segue
  - use o **git config --global user.email "_seu_email_"**
  - use o **git config --global user.name "_seu_user_"**
- **git add:** adicionar os arquivos que poderão ser comitados. Podem ser usados caracteres coringas (* por exemplo)
- **git commit:** _-m_ "mensagem". Usado para comitar. Ao comitar, serão exibidos os primeiros digitos do sha1, arquivos modificados e etc.
- **git status:** informações básicas desse repositório (arquivos untracked, modifieds, etc)
- **git clone**: Clonar um repositório para a máquina
- **git remote**: usado para "linkar" um repositório no servidor (GItHub) com o repositório local
  - **addorigin _link_**: Adicionar um repositório. Origin é uma convenção usada para o link. Esse link pode sr encontrado ao criar um repositorio no GitHub
  - **-v**: usado para ver os repositórios
- **git push origin master:** comando usado para empurrar os arquiivos locais para o servidor
- **git pull origin master:** puxar os arquivos do GitHUb para a máquina

## Ciclo de vida dos arquivos no Git

Quando fazemos um init, estamos criando um repositório git no caminho desejado.

### Tracked Untracked

- **Untracked:** Todos os arquivos antes de serem adicionados ou após sua remoção. GIt não tem ciência deles
- **Tracked:** podem ter 3 estágios:
  - **Unmodified:** arquivos que não sofreram nenhuma alteração
  - **Modified:** arquivo _Unmodified_ que sofreu alteração
  - **Staged:** está pronto para ser commitado. O comando **git add**, por exemplo, manda o arquivo diretamente para o staged. Analogia do back-stage. "Preparado para entrar no palco". Ele está sendo preparado para um commit. Após o commit, o arquivo passa a ser _Unmodified_ novamente. É um ciclo :recycle:

### Servidor e Ambiente de Desenvolvimento

- Servidor: **Remote Repository**. É como se fosse uma cópia na nuvem dos seus arquivos
- Ambiente de Desenvolvimento: Tudo que está na nossa máquina. Existem 3 separações 
  - Working DIrectory: o local onde manipulamos os arquivos.
  - Staging Area: local onde os arquivos prontos para serem comitados
  - Local Repository: quando os arquivos são commitados, eles vem para esse ambiente local. Arquivos não modificados. Ou seja, tudo que está aqui está comitado.

## Resolvendo conflitos

- **Conflito de merge**: duas alterações na mesma linha. Vc deve abrir o arquivo e manualmente resolver o conflito. Depois disso, vc poderá enviar o código para o Github normalmente 
- 