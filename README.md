# APREDENDO GIT (Repositorio Local) e GITHUB (repositorio Remoto)

------------------------------------------------------------------

## 1ª DIA

O que é **GIT** e **GITHUB** ?

**GIT** é um sistema de controle de versão distribuida e atua tambem como um sitema de **gerenciamento local**
de código fonte para milhares de desenvolvedores no mundo todo

O projeto foi desenvolvido por **Çinus Torvalds** para o desenvolvimento do poderoso Kernel do Sistema Linux.

**GITHUB** é uma plataforma de hospedagem de codigo fonte e gerencimento de projetos de forma remota que prmite aos
usuarios o armazenar, gerenciar e compartilhar seus código e projetos com outros usuários.
É um sistema de controle de versão distribuido que ajuda a gerenciar as alterações feitas em um prjeto ao 
longo do tempo, e tudo isso de forma remota

**CONTROLE DE VERSÃO**

Controle de versão é um sistema responsável com a finalidade de gerenciar diferentes versãoes de um documento.
Posibilita fazer o backup das motidicações de um projeto


## COMO GIT FUNCIONA 

Vamos supor que eu tenha 3 arquivos em um reprositório que sao os arquivo A, B e C e ao longo do tempo seja necessarios fazer ajustes
ou talves um desenvolvedor de sua equipe tenha encontrado a solções para um problema que já havia algum tempo
que não era solucionado

Ao fazer esse ajuste nos codigos, entao ao commitar para o respositorio esse ajuste, o GIT deixará uma versao anterior
salva como um SNAPSHOT para garantir caso seja necessarios retornar a versao anterior.


--------------------------------------------------------------------------------------
   VERSAO 1    |     VERSAO 2    |     VERSAO 3    |     VERSAO 4    |     VERSAO 5
--------------------------------------------------------------------------------------
   ARQ A       |     **A1**      |        A1       |     **A2**      |       A2
--------------------------------------------------------------------------------------
   ARQ B       |       B         |        B        |     **B1**      |     **B2**
--------------------------------------------------------------------------------------
   ARQ C       |    **C1**       |      **C2**     |       C2        |     **C3**
--------------------------------------------------------------------------------------
   
   Obeserve o quadro acima

   NA VERSAO 1 
      - todos os arquivos tem a primera versao

   Na VERSAO 2 
      - os arquivos A e C passaram por mudanças e e passaram ter uma nova versão
   
   Na VERSAO 3
      - Enquanto o arquivo C recebe mais uma nova vesao ou atualizaçao, os demais se mantem nas versoes anteriores

   Na VERSAO 4
      - Arq A e Arq B passam por atualização enquanto C se mantem na versao C2.

   Na VERSAO 5
      - Enquanto ARQ A se mante na versao 4, os demais foram atualizados, porem todos eles 
      tem copias das versoes anteriores caso seja necessario retrocedes na versao.

      Resumindo, o GIT guarda o estados dos arquivos se utilizando de um sistema Snapshot.


###COMO CONFIGURAR O GIT###

   ANTES DE COMEÇAR FAÇA O DOWNLOAD DO GIT E SIGA OS PASSOS DE INSTALAÇÃO
   [ACESSE ESSE LINK E ESCOLHA SEU SISTEMA OPERACIONAL](https://git-scm.com/downloads)

   OBS: Se voce utilza o LINUX o git já vem nativo no sistema

   Os princpais comandos para configurar o GIT sao:
   
   *1- git config --global user.name "seu nome usuario"
      Esse comando configura seu nome de usuáio

   *2- git config --global user.email 'seu email aqui"
      Configura seu email
   

###CONFIGURANDO UM EDITOR  ###

   Por padrao o GIT vem com o editor 'vim'

   Para configura um editos de sua preferencia digite

   *1- git config --global core.editor "subl" (para usar o sublime)

   *2- git config --global core.editor "vim" (para utilizar o vim)

   *3- git config --global core.editos "code --wait" (para configura o VSCode)

   (code é a breviação de VSCODE e wait faz com que voce retorne ao shell depois de ser fechado)


###PARA VERIFICAR SUAS CONFIGURAÇÕES###

   Para ver seu nome de usuario:
      - git config user.name

   Para ver seu email
      - git config user.email

   Para ver tudo
      - git config --list

###INICIALIZANDO O REPOSITORIO DO SEU PROJETO###

   Se voce nao tiver criado uma pasta para seu projeto ainda, voce pode cria-la por aqui ou 
   se preferir voce poderá cria-la pelo "Explorador de Arquivos"

   No meu caso a partição ond estao meu projetos é a partição D, estando certo de onde esta é so seguir o passos

   Criar uma pasta para seu projeto
   
      - mkdir <nome da pasta do projeto>

   Entrar na pasta do projeto

      - cd <nome da pasta>

   Para listar os arquivos da pasta

      No WINDOWS | digite "dir"

      No MAC ou LINUX | digite "ls"

####DICAS PARA VER OS DIRETORIOS PELO CMD/PROMPT####

      diskpart - visualisa suas partições disponiveis
      list disk - mostra os disco acessiveis
      list volume - mostra o volume de suas partições
      dir - lista arquivos e pastas


---------------------------------------------------------------

###CASO DIGITE ALGUMA CREDENCIAL ERRADA NA CONFIGURAÇÃO###

   - Limpar credenciais no git

         git config --global --unset user.name
         git config --global --unsete user.email

   - Limpas as informações das credenciais globais guardadas

         git config --gloal --unset credencial.helper

   - Apagar informações de credenciais contidas no sistema

         git config --system --unset credential.helper


----------------------------------------------------------------

##PARA INICIAR O REPOSITORIO LOCAL NA PASTA DO PROJETO

   *1 - Entrar na pasta do projeto
   *2 - Iniciar o GIT

      git init
         Esse comando é responsavel por ficar enxergando as modificações
         realizadas dentro do repositorio do seu projeto.
         Ele é quem incia o repositorio

      git status
         Exibe as condições do diretorio de trabalho e em que STAGED seu 
         arquivos se encontra

   ###ESTAGIO DE SEUS ARQUIVOS NO PROJETO###
   
      São so estagios em que seu aquivo se encontra. Existem os seguintes
      estagios que o status retornara pra voce

      UNTRACKED
         Quando o git status retorna pra voce o UNTRACKED quer
         dizer que os arquivos que aparecerem nessa lista existem
         na pasta do seu projeto mas nao estao sendo rastreado pelo
         git ainda e o git nem conhece sua existencia.

      UNMODIFIED
         Se o estado do arquivo aparece como UNMODIFIED quer dizer
         que estão no repositorio git e ainda nao foram modificados
         desde o ultimo COMMIT

      MODIFIED
         Se depois de criar o arquivo, voce precisar fazer qualquer modificação
         o status irá mostrar os arquivo MODIFIED ou seja, os arquivos foram
         modificados desde o ultimo COMMIT mas anda nao foram adicionados
         ao proximo COMMIT. Esse arquivos ainda nao foram confirmados para
         fazer parte do proximo COMMIT
      
###CICLOS DE VIDA DOS STATUS DOS ARQUIVOS###

   O GIT serpar 4 estados bem definidos de como os aquivos vao ser

      UNTRACKED - Nao marcado
                  Foi adicionado no repositorio
                  Nao foi visto pelo GIT ainda
                  Não existe no GIT por enquanto
      
      UNMODIFIED - Apos adicionar utilizando o comendo - git add - 
                   ele passa a existir no repositorio porem 
                   aparecerá como NÃO MODIFICADO
                   Existe no gir mas nao foi modificado

      MODIFIED - Se o arquivo for modificado ele para a ser visto
                 como MODIFIED pelo git

      STAGE - Depois de modificado
              Pode colocar o arquivo como versao e ele passa
              a existir no STAGE

--------------------------------------------------------------------------------

Apos realizar o COMMIT e os arquivos forem adicionados no GIT ele receberá
a sua versao e todos os arquivos passam a ser UNMODIFIED

---------------------------------------------------------------------------------

###RESUMINDO###

   git status
      - Mostra como esta o status do repositorio. Untracked, Unmodified, Modified
   
   git add <nome do arquivo>
      - Vai adicionar o arquivo ao repositorio
   
Ao verificar o status e observar mudanças que foram necessarias voce poderá
utilizar o GIT ADD ou diretamente o GIT COMMIT

   git commit -am "mensagem sobre as mudanças feitas para voce ou outros usuarios"]
      - commit signitica tonar permanente as alterações feitas ou seja, enviar para
      ser efetivada uma nova versao do arquivo criado
      - am -  informa que deve ser fazer o envio do projeto e inserir a mensagem.
      - "mensagem entre aspas"

   Faz parte dos bons costumes inserir as mensagem condizente com as alterações feitas para
   quem desejar ajudar, ou precisar sabner as ultmas alterações feitas possa no projeto


---------------------------------------------------------------------------------

Quando criamos um novo arquivo e o salvamos dentro do repositorio, ou mesmo copiamos
algum arquivo pra dentro dele, ao utilizar o comando

      Git Status

      O novo arquivo deverá sera marcado no stage como UNTRACKED, ou seja, ele esta 
      informando que o arquivos existe, esta no repositorios mas que ele ainda nao 
      foio adicionado ao repositorio.

      Mesmo que voce altere esse arquivo novamente varias vezes antes de add, 
      ele continuara sendo UNTRACKED

      Dessa forma, apos criarmos os arquivos devemos adiciona-los ao repositorio

      Git Add <nome do arquivo>

      Apos adicionar o arquivo e solitar novamente um git status, 
      ele será apresentado como "new file" informando que esta pronto para 
      ser commitado, então basta seguir as recomendações se estiver tudo certo

      git commit -m "mensaghem do commit"

      Após o commit o arquivo ja se encontra dentro do repositorio, mas ainda 
      nao existe dentrro do BRANCH principal, entao dessa forma se reesvolver 
      alterar novamente o arquivo e verificar o STATUS esse será apresentado 
      a voce como MODIFIED

      GIT COMMIT
         - commit  é o momento quie voce avisa oa GIT para pegar todos os
         arquivos que estao no repositorio e pede para que seje criado
         uma imagem deles.
         - O GIT cria entao uma imaghem daquele arquivos fazendo um SNAPSHOT, 
         ou seja, criando uma imaghem, uma versao.

         Parta realizar o committ basta digitar
         - git commit -m "mensagem"

         Se voce digitar git status , depois do commit, voce será informado que esta na
         BRANCH MASTER ou MAIN e que nao ha mais arquivos para serem commitados.

      Toda vez que voce alterar um arquivo deve se lembrar de fazer o 
      - Git Add <nome do arquivo> para que o status entenda que existem 
      arquivos modificados MODIFIED


-------------------------------------------------------------------------------------
##cOMANDO PARA USAR DEPOIS DOP COMMIT##

   Apos fazer o "git commit" verifique o log do repositorio

      - git log
         mostra as seguintes informaçoes
         - O autor do commit
         - a hash do commit
         - o email do autor
         - a data 
         - a mensagem registrada pelo autor

      - git log --decorate
         mostra tambem
         - de qual branch para qual branch
         - se houve murph

      - git log --author "eme"
         - mostra uma lista dos commits realizados
         por nome do autor. Pode se escolher um nome
         ou parte dele

      - git shortlog
         - Mostra em ordem alfabetica
            - os autores e quantos commits foram feitos
            - mostra quais foram os commits

      - git shortlog -sn
         - mostra a quantidade de commites
         - mostra as pessoas que fizeram commit e a quanitdade de cada um
      
      - git logo --graph
         - mostra em forma de gráfico o que esta acontecendo com os branchs e
         as versoes


   ###PELA HASH DA PRA VER AS ATUALIZAÇÕES###

      - gist show <cole uma hash aqui>
         - verifica o que foi mudado/alterado no arquivo
         - mostra as alterações realizadas

      - git diff
         - com esse comando voce consegue ver as alterações que 
         foram realizadas antes de fazer o commit.

         obs: depois de fazer o commit essas informaçoes ficam 
         indisponiveis para ver as alterações. Se voce ja tiver realizado
         o commit, precisara realizar os reset para que possa ter acesso
         novamente

      git diff --name-only
         - se voce tem uma lista grande de arquivos modificados, como esse
         comando voce consegue ver uma lista sem precisar analisar um grande log

---------------------------------------------------------------------------------------
###IMPORTANTE###

      Como regra de boa prática é sempre importante utilizar o comando 
      git diff
      antes re realizar o commit, assim voce evita enviar arquivos 
      com algum erro, evitanto sujar demais seu repositorios.

----------------------------------------------------------------------------------------

##DESFAZENDO COISAS NO GIT##

      Suponhamos que voce tenha feito algumas modificaçoes em seus codigos e de repente
      descobriu que precisa retrocedes, ou voltar atrás, que nao quer mais essas alterações, 
      porem voce acabou fazendo o commit desse arquivos

      Existem algumas formas para voce resetar, mas como ja mencionei anteriormente, se voce
      fizer uso das boas praticas voce ira evitar muito utilizar o reset

      **PARA RESTAURAR A ULTIMA MODIGICAÇÕA**

      Caso tenha realizado alguma modificação mas ainda nao realizou o commit, basta utilizar
      o seguinte codigo

      - git checkout <nome do arquivo>
         Esse comando irá retornar o arquivo para antes da ultima edição

      - git resert --HEAD <nome do arquivo>

      As principais formas de reset sao:
      - git reset --soft <a ultima hash antes do arquivo que pretende resetar>
         vai pegar as modificações e ira matar o ultimo commit e voltar para staged 

      - gitr reset --mixed <ultima hash antes do arquivo que pretende resetar>
         vai matar o commit e voltar para antes de staged

      - git reset --hard <ultimo hash antes do aqrquivo que pretende resetar>
         vai matar tudo que foi feito no commit

      OBS: Voce precisa escolhjer a hash antes do commit que deseja matar.
            Exermplo: digamos que voce tem 5 commit, porem, deseja matar os dois ultimo, entao
            voce precisara informar a hash ates desses commits que pretende resetar


###O GIT RESET###

      É importante para evitar que voce suba muita sujeira sem importancia, porem,
      é necessário tomar muito cuidado porque o Git reset altera o historico do comit, ou seja,
      se voce ja havia dado um PUSH daquel commit e precisou fazer um RESET HARD e resolver
      subir novamente, o GIT ira informar que existe uma diferença entre o arquivo e o que já
      está no GIT.

      Se isso ocorrer voce conseguira subir somente com FORCE

      - Use o GIT RESET com muito cuidado.


-------------------------------------------------------------------------------------------------

#GITHUB#

### repositório remoto ###

Alem de um repositorio para compartilhar seu codigo e versiona-los, ele é muito urilizado 
por empresas para nalisar o seu desempenho antes da entrevista ou mesmo antes de entrar
em contato com voce

-----------------------------------

Se voce ainda nao, o primeiro passo é criar sua conta no git hub.
acesse esse link [github](https://https://github.com/)

Crie sua conta ou acesse sua conta caso ja tenha

###PARA CRIAR UM NOVO REPOSITORIO REMOTO###

ANTRES DE MAIS NADA PARA EVITAR MAIORES PROBLEMAS NA HORA DE ENVIAR
CRIE UM ACESSO SSH PELO GIT HUB.

- CONECTE-SE AO GITHUB COM O SSH
   [ACESSE AQUI](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh)

   [CLIQUE AQUI](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh) 
   VERIFIQUE SE EXISTE UMA CHAVE EXISTENTE. SIGA OS PASSOS

   [CLIQUE AQUI](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
   SE PRECISAR CRIAR UM NOVA CHAVE SSH

   [CLIQUE AQUI](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
   PARA ADICIONAR UM NOVA CHAVE/KEY SSH NO GITHUB


Para voce enviar os arquivos do repositorio local (git)
para o repositorio remoto (github) voce precisara criar
dentro do github um novo respositorio.

Para fazer isso, dentro do GITHUB, depois de acessa-lo com sua
conta criada, basta ir ao lado de sua imaghem de login e clicar no +
e em "new Repository" e nomea-lo da forma que voce preferir.


-----------------------------------------------------------------------------------------
COMO CRIAR SEU REPOSITORIO PELA LINHA DE COMANDO DO GIT

ECHO "#<digite aqui o nome do seu repositorio no git hub>" >> <README.md>
git init
git add README.md
git commit -am "primeiro commit"
git remote add origin git@github.com: <nome do seu repositorio criado na primeira linha>.git
git push -v origin master (em alguns casos como o github fez algumas mudanças, substitua master por main)

-------------------------------------------------------------------------------------------
CASO JA TENHA CRIADO O NOVO REPOSITORIO NO PROPRIO GITHUB SEGUINDO OS PASSOS ANTERIORES
UTILIZE APENAS AS LINHAS ABAIXO

-git remote add origin git@github.com:<seu_usuario_no_github>/<nome_do_repositorio_criado>.git


###PARA VERIFICAR SE ACESSOU O REPOSITORIO REMOTO###

   -  git remote
      renornará pra voce "origin"

   - git remote -v
      mostra mais detalhes do repósitorio

   - git push -u oririn master ou main
      -u = serve para trackear
      origin = para onde vai
      master ou main = branch padrao no github 

   assim foi feita a ligação entre o repostirorio local e o repostirio remoto

------------------------------------------------------------------------------------------------------

##COMO ENVIAR MUDANÇAS DOS MEUS ARQUIVOS APÓS JA TER ENVIADO PARA O
REPOSITORIO REMOTO (GITHUB)##

   - Depois de realizar as mudanças nos arqauivos voce deverá realizar os comandos
      - git add - Adicionar
      - git commit -m -  comitar
      - git push - enviar 

   Exemplo: 

   - code README.md
   - realizar as mudanças e salve as mudanças no arquivo README.md
   - git status para ver se esta modificado
   - git add README.md
   - git commit -am "alteração de acertoda na linha tal"
   - git push -f origin main (ou master)
   - git log para veirificar se ja esta no repositorio

   Para finalizar entre no github, acesse sua conta ou de um refresh para atualizar a pagina
   e ver se os aqruivos estão ok
   

]





            

     

   

      
   
      

