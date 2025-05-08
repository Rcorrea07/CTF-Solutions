# interencdec
###### Resolvido por @Rafael-Corrêa
> Este é um CTF sobre Base64, Cifra de César.

## Sobre o Desafio
Enunciado da questão: "Can you get the real meaning from this file."

#### Análise Inicial
Foi fornecido um arquivo, que ao abrilo com o bloco de notas, nos dá a seguinte mensagem:
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgyMHdNakV5TnpVNGZRPT0nCg==

## Solução
Após uma análise cuidadosa da frase obtida ao abrir o arquivo, percebe-se que esta tem as características necessárias para ser uma mensagem em Base64: 

"Utiliza letras maiúsculas (A-Z), minúsculas (a-z), números (0-9), e os símbolos + e /.
Pode incluir um ou dois sinais de igual (=) no final como preenchimento.
A string tem um comprimento divisível por 4."

Portanto, utilizaremos sites de decodificação como o [B64](https://www.base64decode.org/) para descobrir o que a mensagem que passar, nos retornando: "d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX20wMjEyNzU4fQ==", percebe-se que ao decodificar pela primeira vez, a mensagem continua na Base64, nos indicando que o ela foi codificada mais de uma vez.
Então, o mesmo processo é repetido, mas dessa vez com a nova sequência obtida, e ao decodifica-la, temos acesso a esse texto: "wpjvJAM{jhlzhy_k3jy9wa3k_m0212758}"

Agora que terminamos de retirar da Base64, ao analisarmos o formato obtido da última decodificação, vemos que tem um formato similar a flags de CTF (JAM{...} lembra CTF{...}), lembramos por sua vez da Cifra de César, uma técnica de criptografia que desloca as letras do alfabeto por um número fixo de posições, assim, relacionando o prefixo JAM com CTF, vê-se um deslocamento de 19 letras (ou -7).

Aplicamos então ROT19 com ajuda de um site como: [Cifra de César](https://site112.com/cifra-de-cesar-codificar-descodificar) no texto anteriormente descoberto, nos levando então para a flag, que conclui o desafio.
>`picoCTF{caesar_d3cr9pt3d_f0212758}`
