# Jogo-de-palavra-secreta-com-amigos
é um jogo de palavra secreta pra jogar com seus amigos, onde alguém digita a palavra secreta, e os outros tentarão adivinhar qual é a palavra


#jogo de palavra secreta para jogar com amigo
import os

print('Bem vindo ao jogo da palavra secreta.\n'
      'Esse jogo é feito para duas pessoas jogarem.\n'
      'Seu amigo ou você vai digitar uma palavra secreta,\n'
      'e um dos dois tentará advinhar qual é a palavra secreta.\n'
      'Serão 10 tentativas, mas fica a gosto do usuário querer aumentar ou não.\n')

palavra_secreta = input('Digite uma palavra secreta: ')
os.system('cls')

palavra_secreta2 = palavra_secreta
letras_acertadas = ''
tentativas = 0

while True:
    letra_digitada = input('Digite uma letra: ')
    tentativas += 1

    if len(letra_digitada) < 1:
        print('Digite pelo menos uma letra.')
        continue
    
    if len(letra_digitada) > 1:
        print('Digite apenas uma letra.')
        continue

    if letra_digitada.isnumeric() or not letra_digitada.isalpha():
        print('Digite apenas letras.')
        continue

    if letra_digitada in palavra_secreta2:
        letras_acertadas += letra_digitada


#nesse caso abaixo, a variável 'palavra_formada' vai servir para deixar a palavra secreta na horizontal
#é como se fosse uma nova palavra formada através das letras digitadas
#não consegui achar algum outro método para que fosse mais fácil de compreender
#(na verdade consegui, mas era mais complicado que esse, então resolvi deixar esse mesmo.)

    palavra_formada = ''#variável com string vazia

    for letra_secreta in palavra_secreta2:
        if letra_secreta in letras_acertadas:
            palavra_formada += letra_secreta#concatenar a variável criada pro for com a palavra formada

        else:
            palavra_formada += '*'
        
    print(palavra_formada, f'tentativa = {tentativas}')


    if tentativas >= 10:
        print('Que pena, acabaram as tentativas :(')
        break
    if palavra_formada == palavra_secreta2:
        print(f'Parabéns! Você acertou. A palavra secreta era "{palavra_secreta}".')
        break

#as tentativas também contarão com os espaços, infelizmente não consegui
#colocar pra parar em 10 tentativas digitando apenas espaços ou símbolos.
#mas mesmo assim vai contar as tentativas

           
