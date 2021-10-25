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
  - == : <br>
    Deve ser evitado, não seguro, pois tem propriedades incomuns.
    "42" == 42 (string igual a inteiro) <br>
    0 == " false " <br>
    null == undefined <br>
    " " == 0 <br>
    [1, 2] == "1, 2"<br>
  - === : <br>
    Geralmente usado, seguro. <br>
    NaN (not a number) em Object.is não é igual a NaN, retorna false. <br> 
     + 0 é igual a - 0. <br>
  - Object.is : <br>
    Menos usado, porém igualmente seguro. <br>
    NaN (not a number) em Object.is é igual a NaN, retorna true.< br>
     + 0 é diferente de - 0.<br>
     
     <br>Diferença de comparação de Objetos e variáveis no JS. 
        Quando se trata de Objetos o JavaScript não considera o conteúdo do Objeto na comparação e sim seu endereço de memória: <br>
      ``` bash
        let person1 = { firstName: Gui , lastName: Heringer } 
        let person2 = {firstName: Gui , lastName: Heringer } 
        person1 == person2 // false 
        person1 === person2 // false 
        Object.is(person1,person2) // false
      ```
       <br> Quando se trata de variáveis do tipo primitivo o JavaScript compara o seus conteúdos: <br>
    ``` bash
        firstName1 = "Gui"
        firstName2 = "Gui" 
        fistName1 = firstName2 // true
    ```
 ------------------------------------------
 ### Funções de Object
 - `Object.assign`
 Object.assign é uma propriedade útil, pois ela mescla propriedades de um objeto com outro objeto.
 ``` bash 
 let person1{
 fistName = "Gui"
 lastName = "Heringer"
 age: 21
 person1.isAdult { return this.age > 18;}
 }
 
 let healthStats = {
 height = 1,86 ,
 weight = 70;
 }
 
 //deseja-se fundir healthStats em Person1
  //criando uma função que retorna um novo objeto fundido, para não alterar os objetos originais, no caso o person1.
  function mergeStatsHealth (person, healthStats){
    return Object.assign({}, person, healthStats); //coloca esse objeto em branco no primeiro parametro para alterar ele, e não person1. Parametro da direita é o a fundir e o direita é onde fundir.
  }
```
- `Object.create()`
Forma mais detalhada de criar objetos, com o mesmo resultado, porém menos usual e de sintaxe menos limpa.

------------------------------------------

