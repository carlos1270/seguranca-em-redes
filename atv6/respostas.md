**1. Qual é a diferença entre aleatoriedades estatísticas e imprevisibilidade?**

R: A aleatoriedade estatística refere-se à propriedade de uma sequência de dados ou números que apresenta uma distribuição uniforme e aparentemente aleatória quando analisada estatisticamente. Um exemplo simples de aleatoriedade estatística é o lançamento de uma moeda. Já a imprevisibilidade refere-se à propriedade de uma sequência de dados ou números em que é difícil ou impossível fazer previsões precisas sobre o próximo elemento da sequência, mesmo com acesso a informações anteriores ou estatísticas. Voltando ao exemplo da moeda, suponha que você esteja observando uma sequência de lançamentos de moeda, mas não tem acesso aos resultados anteriores. Neste caso, você não consegue prever o resultado do próximo lançamento, pois não possui informações para basear suas previsões.

**2. Liste considerações de projeto importantes para uma cifra de fluxo.**

R: As mesmas considerações que se aplicam a cifras de bloco são válidas para cifras de fluxo, uma cifra de fluxo deve utilizar uma chave de 128 bits, a chave gerada na cifra de fluxo deve ser obtida por meio da geração de um número pseudoaleatório pois a cifra de fluxo encripará uma certa quantidade de bits ou bytes por vez, sendo que quando utilizada a mesma chave para fluxos diferentes a criptoanalise se torna relativamente simples. Por fim, o fluxo de bits deve ter um periodo relativamente longo, já que quando maior o fluxo a imprevisibilidade dos bits será maior.

**3. Por que não é desejável reutilizar uma chave de cifra de fluxo?**

R: Como já dito a cifra de fluxo encripará uma certa quantidade de bits ou bytes por vez, sendo que quando utilizada a mesma chave para fluxos diferentes a criptoanalise se torna relativamente simples, visto que uma vez que tenhamos os dois fluxos lado a lado é "fácil" adivinhar qual a chave. 

**4. Que operações primitivas são usadas no RC4?**

R: São utilizadas permutações, para gerar um S-box e criar uma chave pseudoaleátoria e combinações XOR da chave com o texto livre para gerar o texto cifrado.

**5. Se apanharmos um algoritmo de congruência linear com um componente aditivo de 0: X<sub>n+1</sub> = (aX<sub>n</sub>) mod m então, podemos mostrar que, se m é primo, e se determinado valor de a produz o período máximo de m − 1, então a<sup>k</sup> também produzirá o período máximo, desde que k seja menor que m e que m − 1 não seja divisível por k. Demonstre isso usando X<sub>0</sub> = 1 e m = 31, e produzindo as sequências para ak = 3, 3<sup>2</sup>, 3<sup>3</sup>, 3<sup>4</sup>.**

R: Sabemos que 31 é primo, logo devemos achar um a que produz um periodo máximo de m-1, ou seja, 31-1=30. Temos como primeira opção 3, a=3 e k=1. 

Sequência 
```
X<sub>0</sub> = 1
X<sub>1</sub> = (3 * 1) mod 31 = 3
X<sub>2</sub> = (3 * 3) mod 31 = 9
X<sub>3</sub> = (3 * 9) mod 31 = 27
X<sub>4</sub> = (3 * 27) mod 31 = 19
X<sub>5</sub> = (3 * 19) mod 31 = 26
X<sub>6</sub> = (3 * 26) mod 31 = 16
X<sub>7</sub> = (3 * 16) mod 31 = 17
X<sub>8</sub> = (3 * 17) mod 31 = 20
X<sub>9</sub> = (3 * 20) mod 31 = 29
X<sub>10</sub> = (3 * 29) mod 31 = 25
X<sub>11</sub> = (3 * 25) mod 31 = 13
X<sub>12</sub> = (3 * 13) mod 31 = 8
X<sub>13</sub> = (3 * 8) mod 31 = 24
X<sub>14</sub> = (3 * 24) mod 31 = 10
X<sub>15</sub> = (3 * 10) mod 31 = 30
X<sub>16</sub> = (3 * 30) mod 31 = 28
X<sub>17</sub> = (3 * 28) mod 31 = 22
X<sub>18</sub> = (3 * 22) mod 31 = 4
X<sub>19</sub> = (3 * 4) mod 31 = 12
X<sub>20</sub> = (3 * 12) mod 31 = 5
X<sub>21</sub> = (3 * 5) mod 31 = 15
X<sub>22</sub> = (3 * 15) mod 31 = 14
X<sub>23</sub> = (3 * 14) mod 31 = 11
X<sub>24</sub> = (3 * 11) mod 31 = 2
X<sub>25</sub> = (3 * 2) mod 31 = 6
X<sub>26</sub> = (3 * 6) mod 31 = 18
X<sub>27</sub> = (3 * 18) mod 31 = 23
X<sub>28</sub> = (3 * 23) mod 31 = 7
X<sub>29</sub> = (3 * 7) mod 31 = 21
X<sub>30</sub> = (3 * 21) mod 31 = 1 (Repete)
```

Para esse caso, temos uma sequência de 30, logo já está provado que para um a=3 temos uma sequência m-1.

**6. a. Qual é o período máximo que pode ser obtido do seguinte gerador? X<sub>n+1</sub> = (aX<sub>n</sub>) mod 2<sup>4</sup>**

R: Como 2<sup>4</sup> é um inteiro não primo, supondo que a e x sejam inteiros também, a sequência pode produzir valores 0 ≤ X<sub>n</sub> < 2<sup>4</sup>.

**b. Qual deverá ser o valor de a?**

R: Como 2<sup>4</sup> é não primo, então a escolha do valor de a deve ser feita de forma que geremos a maior sequência possivel, ou seja 0 < a < 2<sup>4</sup> e que gera a maior sequência possivel de inteiros.

**c. Que restrições são exigidas na semente?**

R: Como essa equação gera uma sequência previsivel de números a partir do conhecimento dos coeficientes a escolha correta da semente deve ser um número aleatório ou psedoaleátorio.

**7. Que valor de chave RC4 deixará S inalterado durante a inicialização? Ou seja, após a permutação inicial de S, as entradas de S serão quais aos valores de 0 a 255 na ordem crescente.**

Para que isso ocorra a chave deve ser uma chave sequêncial de 0 a 255, visto que a inicialização de S possui os mesmos valores, resultando na não alteração de S no final da fase de inicialização.

