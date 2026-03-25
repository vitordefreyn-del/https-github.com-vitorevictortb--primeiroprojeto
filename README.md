# https-github.com-vitorevictortb--primeiroprojeto
#pseudocodigo
INÍCIO

CRIAR lista de palavras
CRIAR lista de dicas

SORTEAR um índice aleatório
DEFINIR palavra = palavra sorteada
DEFINIR dica = dica correspondente

CRIAR lista palavraOculta com "_" para cada letra
CRIAR lista letrasErradas vazia
DEFINIR erros = 0

MOSTRAR palavraOculta na tela
ESCONDER dica

ENQUANTO jogo não terminou

    LER letra do jogador

    SE letra estiver vazia
        CONTINUAR

    SE letra já foi usada
        IGNORAR

    SE letra estiver na palavra
        PARA cada posição da palavra
            SE letra for igual
                REVELAR letra na palavraOculta
    SENÃO
        ADICIONAR letra em letrasErradas
        AUMENTAR erros

    ATUALIZAR palavra na tela
    MOSTRAR letras erradas
    ATUALIZAR desenho do boneco

    SE não existir "_" na palavraOculta
        MOSTRAR "Você venceu"
        REINICIAR jogo

    SE erros atingirem limite
        MOSTRAR "Você perdeu"
        MOSTRAR palavra correta
        REINICIAR jogo

FIM ENQUANTO

FIM
