#  Curso Javascript Objects, Prototypes and Classes da Pluralsight.

## Objects
Objetos são basicamente tipos de variáveis mais complexos, são essencialmente uma maneira de agrupar informações em uma única variável.

### Dinamicidade dos Objetos em Javascript
Em javascript você pode criar propriedades e até funções de uma classe (objeto) fora de seu escopo {}

``` bash
  let person = {
  firstName = Gui
  lastName= Heringer
  }
  person.age = 21; // criando uma variável age dentro do objeto porém fora do escopo
  person.isAdult = function () { return this.age >= 18; } // igualmente criando a função isAdult()
  
   display(person.isAdult());
  ```
 Dentro de um objeto e de uma classe, a sintaxe da função isAdult pode ser abreviada, tornando-se assim:
 ``` bash
  person.isAdult { return this.age >= 18;}
 ```
 ------------------------------------------
 ### Propriedade For- in
 O laço for...in  interage sobre propriedades enumeradas de um objeto, na ordem original de inserção.
 ``` bash
  for (let nomeProps in person) { //percorre cada propriedade da classe person de cima para baixo, atribuindo o valor das variáveis dele à variável nomeProps.
   display(nomeProps);
  }
  ```
  ------------------------------------------
  ### Operadores de igualdade 
  - == 
    Deve ser evitado, não seguro, pois tem propriedades incomuns.
    "42" == 42 (string igual a inteiro)
    0 == " false "
    null == undefined 
    " " == 0 
    [1, 2] == "1, 2"
  - ===
    Geralmente usado, seguro.
    NaN (not a number) em Object.is não é igual a NaN, retorna false.
    + 0 é igual a - 0.
  - Object.is
    Menos usado, porém igualmente seguro
    NaN (not a number) em Object.is é igual a NaN, retorna true.
    + 0 é diferente de - 0.
 ------------------------------------------

