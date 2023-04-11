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


###<font color=\"red"\>COMO CONFIGURAR O GIT </font> ###

   ANTES DE COMEÇAR FAÇA O DOWNLOAD DO GIT E SIGA OS PASSOS DE INSTALAÇÃO
   [ACESSE ESSE LINK E ESCOLHA SEU SISTEMA OPERACIONAL](https://git-scm.com/downloads)

   OBS: Se voce utilza o LINUX o git já vem nativo no sistema

   Os princpais comandos para configurar o GIT sao:
   
   *1- git config --global user.name "seu nome usuario"
      Esse comando configura seu nome de usuáio

   *2- git config --global user.email 'seu email aqui"
      Configura seu email
   

### CONFIGURANDO UM EDITOR  ###

   Por padrao o GIT vem com o editor 'vim'

   Para configura um editos de sua preferencia digite

   *1- git config --global core.editor "subl" (para usar o sublime)

   *2- git config --global core.editor "vim" (para utilizar o vim)

   *3- git config --global core.editos "code --wait" (para configura o VSCode)

   (code é a breviação de VSCODE e wait faz com que voce retorne ao shell depois de ser fechado)


### PARA VERIFICAR SUAS CONFIGURAÇÕES ###

   Para ver seu nome de usuario:
      - git config user.name

   Para ver seu email
      - git config user.email

   Para ver tudo
      - git config --list

### INICIALIZANDO O REPOSITORIO DO SEU PROJETO ###

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

#### DICAS PARA VER OS DIRETORIOS PELO CMD/PROMPT ####

      diskpart - visualisa suas partições disponiveis
      list disk - mostra os disco acessiveis
      list volume - mostra o volume de suas partições
      dir - lista arquivos e pastas


---------------------------------------------------------------

### CASO DIGITE ALGUMA CREDENCIAL ERRADA NA CONFIGURAÇÃO ###

   - Limpar credenciais no git

         git config --global --unset user.name
         git config --global --unsete user.email

   - Limpas as informações das credenciais globais guardadas

         git config --gloal --unset credencial.helper

   - Apagar informações de credenciais contidas no sistema

         git config --system --unset credential.helper


----------------------------------------------------------------

## PARA INICIAR O REPOSITORIO LOCAL NA PASTA DO PROJETO ##

   *1 - Entrar na pasta do projeto
   *2 - Iniciar o GIT

      git init
         Esse comando é responsavel por ficar enxergando as modificações
         realizadas dentro do repositorio do seu projeto.
         Ele é quem incia o repositorio

      git status
         Exibe as condições do diretorio de trabalho e em que STAGED seu 
         arquivos se encontra

   ### ESTAGIO DE SEUS ARQUIVOS NO PROJETO ###
   
      São so estagios em que seu aquivo se encontra. Existem os seguintes
      estagios que o status retornara pra voce

     ** UNTRACKED **
         Quando o git status retorna pra voce o UNTRACKED quer
         dizer que os arquivos que aparecerem nessa lista existem
         na pasta do seu projeto mas nao estao sendo rastreado pelo
         git ainda e o git nem conhece sua existencia.

      ** UNMODIFIED **
         Se o estado do arquivo aparece como UNMODIFIED quer dizer
         que estão no repositorio git e ainda nao foram modificados
         desde o ultimo COMMIT

      ** MODIFIED **
         Se depois de criar o arquivo, voce precisar fazer qualquer modificação
         o status irá mostrar os arquivo MODIFIED ou seja, os arquivos foram
         modificados desde o ultimo COMMIT mas anda nao foram adicionados
         ao proximo COMMIT. Esse arquivos ainda nao foram confirmados para
         fazer parte do proximo COMMIT
      
### CICLOS DE VIDA DOS STATUS DOS ARQUIVOS ###

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

### RESUMINDO ###

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
## COMANDO PARA USAR DEPOIS DOP COMMIT ##

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


   ### PELA HASH DA PRA VER AS ATUALIZAÇÕES ###

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
### IMPORTANTE ###

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


### O GIT RESET ###

      É importante para evitar que voce suba muita sujeira sem importancia, porem,
      é necessário tomar muito cuidado porque o Git reset altera o historico do comit, ou seja,
      se voce ja havia dado um PUSH daquel commit e precisou fazer um RESET HARD e resolver
      subir novamente, o GIT ira informar que existe uma diferença entre o arquivo e o que já
      está no GIT.

      Se isso ocorrer voce conseguira subir somente com FORCE

      - Use o GIT RESET com muito cuidado.


-------------------------------------------------------------------------------------------------

# GITHUB #
## Repositorio Remoto ##

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
### COMO CRIAR SEU REPOSITORIO PELA LINHA DE COMANDO DO GIT ###

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


### PARA VERIFICAR SE ACESSOU O REPOSITORIO REMOTO ###

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

## COMO ENVIAR MUDANÇAS DOS MEUS ARQUIVOS APÓS JA TER ENVIADO PARA O REPOSITORIO REMOTO (GITHUB) ##

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
   - git log para verificar se ja esta no repositorio
### Para finalizar entre no github, acesse sua conta ou de um refresh para atualizar a pagina
### e ver se os aqruivos estão ok


-----------------------------------------------------------------------

# CLONANDO UM RESPOSITORIO #

      - É possivel CLONAR no repositorio local alguns repositorio remotos, para fazer isso

         1 - Acesse o GitHub, escolha o Repositorio que deseja clonar no seu repositorio local
         2 - Clique no botao CODE e la copia a linha da aba HTTPS ou SSH (recomendado SSH)
         3 - Apos copiar, voce retorna para o terminal, escolhe a pasta ou cria uma nova onde
         deseja que seja clonado o repositorio escolhido

      - Em seguida basta seguir os codigos:

         - git clone <cole aqui a linha copiada do respoitorio no github> <insira aqui o 
         nome da nova pasta inde deseja oque o clone seja salvo>
      
         - Pronto voce ja tem o reposito clonado dentro da sua pasta


# FAZENDO UM FORK #

      - FOKR e o mesmo projeto de outra pessoa no seu namespace.
      - Permite que voce faça alterações em um projeto publicamente como um forma de contribuir
      para um projeto.
      - O projetos nao precisam se precoupar em adicionar colaboradores, pois 
      ele esta aberto e dessa forma nao ha necessida de dar acesso ao push.
      -  E como um projeto de codigo aberto ou quando o usuario nao tem acesso de gravação ao
      repositorio upstream

## PARA USAR O FORK NO GIT ##

      - Acesse o projeto pela bara de pesquisa do GITHUB
      - Encontre no lado direito superior do projeto um botão FORK proximo do seu usuario.
      - Clique nesse botao FORK para iniciar o processo 

## QUAL A DIFERENÇA ENTRE FORK E CLONE ##

      - CLONE voce literalmente faz um clone do de um respositorio para sua máquia criando
      um repositorio local desse clone.
      - FORK voce faz o clone dentro do GITHUB 3e cria um CONEXAO entre o que voce contriubuiu
      com o Repositorio Original

--------------------------------------------------------------------------------------------------------

### ADICONANDO TODOS OS ARQUIVO DE UM DIRETORIO RECUSRIVAMENTE ###

      - git add . (basta adicionar ponto no final sem nome dos arquivos)

### FAZER O COMMIT DE TODOS OS ARQUIVOS DO REPOSITORIO LOCAL ###

      - git commit -am "mensagem do commit"
         - a =  all (todos)
         - , = message (mensagem)

--------------------------------------------------------------------------------------------------------


# BRANCH #

## O QUE É ? ##

      - BRANCH  é um pontero movel que leva-o a um COMMIT

## COMO USAR ##

      - Quando criamos um repositório no GIT e fazemos um COMMIT, vai ser gerado uma no HASH.

      --  HASH é um conjunto de numero e letras extensos utilizado para identificar cada COMMIT

      - Para cada HASH sabemos que é criado um SNAPSHOT daquele estado.

      -- SNAPSHOT é como um foto tirada daquele estado, caso precise retornar a ele, 
      aquele COMMIT ficará salvo.

      - O que a HASH faz é aponto para aquele COMMIT - SnapShot
      e vai seguindo esse COMMIT, caso preciso resetar para àquele estado.

      -POR EXEMPLO
         Em um repositorio com 3 COMIT ficaria assim
         
                  |           |  MASTER
         98C34A   |  34AD8V   |  A34FD9
         SNAP A   |  SNAP B   |  SNAP C

         - o BRANCH MASTER estará posicionado no ultimo COMMIT ou HASH

      - Mas podemos criar um NOVO BRANCH, e esse NOVO BRANCH apontar para o mesmo COMMIT
      ou podemos criar esse mesmo NOVO BRANCH ou um terceiro BRANCH e aponta-lo para um
      NOVO COMMIT.

      - Mas como faço para unir esse BRANCH quando precisar?
         Ao final desse material voce verá o que é MERGE e REBASE, quais as vantagens e desvantagens
         de cada um deles.

## PORQUE DEVO USAR O BRANCHE ##

      - Existem várias vantagens em utilizar a criação de novos BRANCH.

         1 - voce pode usa-lo sem alterar o local principal (MASTER)
         2 - ele é facilmente desligado;
         3 - posso criar e apagar o novo BRANCH quando necessario
         4 - pode haver varias pessoas tralhando em outro branch enquanto
         voce faz modificações em outro, como por exemplo no MASTER.
         5 - voce pode criar no seu repositorio por exemplo um NOVO BRANCH A e ou B
         e enquanto as pessoas trabalham nesses BRANCHs, voce continuar trabalhando
         no MASTER sem ninguem atrapalhar ninguem.
         6 - evia que ocorram conflitos.
         7 - é melhor varias pessoas trabalhando em branch diferentes do que em um só
         branch, pois isso pode geral conflitos atrapalhando na produtividade.

# PRÁTICA #
## CRIANDO UM BRANCH ##

      - Para criar um branch novo é extremamente facil
         - git chekout -b <novo Branch>

      - Para mostrar os BRANCHS dispóniveis e qual esta sendo utilizado 
         - git branch
            - ira mostrar os branch disponiveis no repositorio
            - o asteristico determina em que branch voce esta conctado

## NAVEANGO ENTRE OS BRANCHS ##

    - Verifique osa Branchs e escolha um
      - git checkout <nome do branch>
         Esse comando ac3essa o branch que desejar acessar
   
## APAGAR UM BRANCH ##

      - Para deletar um BRANCH quer foi criado basta
         - git branch -d <nome do branch>

# MERGE E REBASE #


      - Ao criarmos um novo BRANCH para fazer modificações ou algum tipo de trabalho
      será necessario UNIR esses BRANCHs e para isso existem duas forma de fazer essa
      união que são:

         * MERGE
         * REBASE

      -- Os doios fazem a mesma coisa, eles unificam os BRANCHs trabalhados mas 
      de FOMAS DIFERENTES que será necessários conhece-las.

      Aqui vou falar dsobre os dois modelos de unificar os branch e depois vamos
      aos codigos e usos deles.


## MERGE  ## 

      No MERGE, suponhamos que temos o MASTER ou MAIN e criamos um novo BRANCH para trabalhar nele.
      Então ficaria encontrariamos nosso respositorio da seguinte forma onde criamos o novo branch 
      chamado de newb553

                  |                 |     MASTER      
      COMMIT 0    <     COMMIT 1    <     COMMIT2     
                  |                 |     newB553

      - Depoios de criar o novo Branch vamos criar um novo COMMIT  dentro do Branch newb553, 
      que será o COMMIT 3 e depois criamos novo BRANCH HOTFIX com o COMMIT 4 

                  |                 |     MASTER                        |     hotfix
      COMMIT 0    <     COMMIT 1    <     COMMIT2     <     COMMIT 3    <     COMMIT 4
                  |                 |     newB553     |     COMMIT 3
                                       

      - Os dois branchs criados estao com seuc commits apontados para MASTER, porem 
      para unificar esses dois BRANCH será nessarios criar um novo COMMIT 5 para fazer a 
      união do novos BRANCH criados no repositorio. apesar de se apresnetar de forma linear
      o repositorio ficará bastante sobrecarregado ou com muita sujeira.

### VANTAGENS DO MERGE ###

      PRÓS        >     * OPERAÇÃO NA DESTRUTIVA
                        * MANTER O REPOSITORIO ORGANIZADO

      CONTRATO    >     * CRIAÇÃO DE COMMIT EXTRA
                        * EXCESSO DE COMMIT SEM SENTIDO
                        * DEIXA HISTÓRICO POLUIDO
                        * CAUSA CONFUSÃO NA HORA DE ANALISAR OS COMMITS


## REBASE ##

      - É mais simples que o MERGE, porem cumpre seu pape de UNIR os BRANCHS.

      - Esse vaso vamos criar criar duas novas branchs

                  |                                                     |     MASTER      |     MASTER      
      COMMIT 0    <     COMMIT 1    <     COMMIT2     <     COMMIT 3    <     COMMIT 4    <     COMMIT 3'
                                                      |     newBRANCH           

      - No caso do uso do REBASE para unificar os BRANCHs, ao aplicar as modificações
      ele mata completamente o COMMIT 3 onde esta o newBranch e cria um COMMIT 3' 
      (commmit 3 linha) no topo a frente dos demais commits.

      PROS        >       * EVITA CRIAÇÃO DE COMMITS EXTRA
                          * HISTORIO FICA SEMPRE EM LINHA SEM VARIOS AGRUPAMENTOS

      CONTRA      >       * PERDE TODA ORDEM CRONOLOGICA 
                          * MUDA TODO HISTORICO FACILMENTE
                          * PODE OCASIONAR PROBLEMAS POR CONTA DA DESORGANIZAÇÃO    
      

      



         


