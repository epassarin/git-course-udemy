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

Apor realizar o COMMIT e os arquivos forem adicionados no GIT ele receberá
a sua versao e todos os arquivos passam a ser UNMODIFIED

---------------------------------------------------------------------------------
      
   
      

