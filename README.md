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

![FIGURA 1] D:BACKUP SSD/PROJETOS/DESENVOLVIMENTO_WEB/git-course/tab.png

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

      

