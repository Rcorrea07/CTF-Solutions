# Cookie Monster Secret Recipe
###### Resolvido por @Rafael-Corrêa
> Este é um CTF sobre Web exploitation, Diretórios ocultos.

## Sobre o Desafio
Enunciado da questão: "Cookie Monster has hidden his top-secret cookie recipe somewhere on his website. As an aspiring cookie detective, your mission is to uncover this delectable secret. Can you outsmart Cookie Monster and find the hidden recipe?
You can access the Cookie Monster here and good luck."

#### Análise Inicial
Foi fornecido um link, que ao clicar nele, nos leva ao seguinte site: [here](http://verbal-sleep.picoctf.net:49737/)

## Solução
Após uma análise cuidadosa do site, ao tentar entrar com um usuário e senha aleatório, somos levados para uma pagina que contêm as seguintes informações: [![Print.png](https://i.postimg.cc/tgZJSL6j/Captura-de-tela-2025-05-08-203858.png)](https://postimg.cc/WDVstYSW)

Quando chegamos nessa página, nos deparamos com 'Me no need password. Me just need cookies!', ou seja, o foco do desafio não tem relacção alguma com descobrir usuário ou senha. O proxímo passo foi olhar entender Cookies como pequenos arquivos de texto que um site guarda no seu computador ou dispositivo móvel quando o visita, e a frase "Hint: Have you checked your cookies lately?" nos leva a voltar ao início do site para verificar os Cookies do mesmo.

Inspecionamos o site então, e vamos para a região que nos mostra os Cookies: Application e dentro vemos a opção Cookies:

[![Print.png](https://i.postimg.cc/pLnykwzt/Captura-de-tela-2025-05-08-213450.png)](https://postimg.cc/PCTt5FS6)

Encontramos "cGljb0NURntjMDBrMWVfbTBuc3Rlcl9sMHZlc19jMDBraWVzXzk4RDA2MDNGfQ%3D%3D". Em primeira vista, parece estranho, mas ao examinar com calma, percebece que é uma mensagem em Base64: "Utiliza letras maiúsculas (A-Z), minúsculas (a-z), números (0-9), e os símbolos + e /. Pode incluir um ou dois sinais de igual (=) no final como preenchimento. A string tem um comprimento divisível por 4.". O único problema seria o %3D, entretanto, ele é um caractere codificado em URL, (URL Encoding), que corresponde ao símbolo '=''(O %3D foi usado para evitar conflitos com sintaxe de URLs).

Portanto, utilizaremos sites de decodificação como o [B64](https://www.base64decode.org/) para descobrir o que a mensagem quer passar, nos retornando a flag.
>`picoCTF{c00k1e_m0nster_l0ves_c00kies_98D0603F}`
