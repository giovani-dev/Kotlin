# Entendendo como o Git funciona por baixo dos panos.

* O git identifica a modificao de um arquivo de acordo com o algoritmo de criptografia sha-1, gerando um hash baseado conteudo do arquivo.
    1. As altracoes sao indentificadas de acordo com o hash, assim mantendo um historico de todas as alteracoes.
    2. Tembem pdoemos citar que o hash nao se delimita somente ao conteudo dos arquivos, mas tambem dos objetos internos do git (Blobs, Trees e Commits)

* Os objetos internos do git sao responsaveis pelo versionamento do codigo.
    1. Alguns dos objetos
        - Blobs, Trees e Commits

    2. Blobs
        - Responsavel por armazenar metadados do git. Exemplo: Tipo do objeto, tamanho do arquivo ... Contem um sha-1 do arquivo.

    3. Trees
        - Armazenam e apontam para os blobs e outras arvores. Assim montando toda a estrutura dos arquivos, armazenando nomes. Cada arvore contem um sha-1 dos seus metadados.

    4. Commit
        - O commit aponta para uma arvore, parente, data e hora da alteracao, autor e menssagem. Assim possibilitando ter um rastreio do projeto, sendo gerado e transposto para um hash sha-1.

# Ciclo de vida dos arquivos no Git

* Tracked e untracked

    1. Quando estao em no modo Tracked, os arquivos sao separados em 3 fazes
        - Unmodified
            - Quando **removemos um arquivo**, o estado do git **sai de Tracked e da faze Unmodified para o estado Untracked.**
            - Ao **editar um arquivo** o git move ele para a faze **Modified.**
        - Modified
            - Stage do arquivo
        - Staged
            - Quando damos um **commit o arquivo vai para a faze unmodified.**

    2. Untracked
        - E quando o Git nao tem ciencia dos arquivos.
        - Quando Nos **adicionamos um arquivo**, o git vai para o estado **Tracked na faze Staged**, assim criando um snapshot do codigo dentro do commit.

* Repercucao do codigo
    1. Ambiente de desenvolvimento
        - Working Directory
            - Vai apra essa area quando executo o comando git add
        - Staging Area
            - Vai apra essa area quando executo o comando git add
        - Local Repository
            - Vai apra essa area quando executo o comando git commit

    2. Servidor
        - Remote Repository
            - Vai apra essa area quando executo o comando git push
