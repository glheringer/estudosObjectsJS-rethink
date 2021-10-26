#  Curso Javascript Objects, Prototypes and Classes da Pluralsight.

## Objects
Objetos são basicamente tipos de variáveis mais complexos, são essencialmente uma maneira de agrupar informações em uma única variável.

### Dinamicidade dos Objetos em Javascript
Em javascript você pode criar propriedades e até funções de uma classe (objeto) fora de seu escopo {}

``` JavaScript
  let person = {
  firstName = Gui
  lastName= Heringer
  }
  person.age = 21; // criando uma variável age dentro do objeto porém fora do escopo
  person.isAdult = function () { return this.age >= 18; } // igualmente criando a função isAdult()
  
   display(person.isAdult());
  ```
 Dentro de um objeto e de uma classe, a sintaxe da função isAdult pode ser abreviada, tornando-se assim:
 ``` JavaScript
  person.isAdult { return this.age >= 18;}
 ```
 ------------------------------------------
 ### Propriedade For- in
 O laço for...in  interage sobre propriedades enumeradas de um objeto, na ordem original de inserção.
 ``` JavaScript
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
      ``` JavaScript
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
 - `Object.keys(Objeto);`
 Exibe em um vetor de cima para baixo o nome das propriedades do objeto.
 - `Object.assign`
 Object.assign é uma propriedade útil, pois ela mescla propriedades de um objeto com outro objeto.
 ``` JavaScript 
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
- `Object.getOwnPropertyDescriptor (Objeto, propriedade);`
 Usado para ver os atributos de uma propriedade: Value, writable, enumerable, configurable.
- `Object.defineProperty(Objeto, propriedade), {atributo, true ou false} ; `
Define os atribudos de uma propriedade.
- `Object.freeze (Propiedade)`
Congela alterações nos atributos dessa propriedade.

------------------------------------------
## Notação de colchetes (Bracket Notation)
``` JavaScript 
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
   display(person.firstName); // O que se faz normalmente
   // Também podemos escrever da seguinte forma:
   display(person[`firstName`]; // a notação bracket me permite colocar nomes que nas propriedades que eu nã
o poderia colocar comumente como:
  display(person[`first name`]; // soltando espaço ou usando caracteres especiais, porque agora o nome da propriedade é
 uma string.
 ```
 <br> Também é útil se usado com o for in para mostrar o conteúdo das prorpriedades.
  ``` bash
  for (let nomeProps in person) { 
   display(nomeProps + `: ` + person[propertyName]);
  }
  ```
  ------------------------------------------
  ## Setter & Getter
  ``` JavaScript
 `use strict`
(function()){

    let person = {
        name: {
            first: `Gui` ,
            last: `Heringer`
        },
        age: 21
    }

    Object.defineProperty(person,`fullName`,{ //criando uma propriedade fullName
        get : function(){
            return this.name.first + ` ` + this.last.name;
        },
        set: function (value){
            let nameParts = value.split (` `);
            this.name.first = nameParts [0];
            this.name.last = namePartsp[1];
        }
    });
    person.fullName = `Ana Paula`;
    display(person.fullName);
}

```
------------------------------------------   
## Protótipos
Prototype é um objeto que esta em todas as funções de JavaScript. É usado como um protótipo quando a função é usado como um contrutor de objectos. Quando se muda um prototype todos objetos que usam essa Function Prototype iram mudar também Person.prototype.age = 30 todos objetos teram 30 anos. Porém se editar apenas diretamente o `jim.age = 18` pela Inheritance apenas o jim tera 18, e tambem tera agora sua propria property AGE.

Em um cadeia/corrente de Inheritance é necessário criar 3 linhas: Dentro da função: Person.call(this, firstNAme, lastName, age)// para trazer as infos de Person para Student Fora da função : Students.prototype = Objects.create(Person.prototype); Students.prototype.constructor = Student;

Sim existe propertype em classes assim como nas funções e são definidas de uma forma similar: Usando: Object.defineProperty(Person.proportype, 'firstName', {enumerable: true}); // usado da mesma forma com outros Prototype.

------------------------------------------
## Herança em JavaScript
  - Em Funções:  
  Usa-se as classes protótipos dos dois objetos que se deseja fazer herança adicionando uma classe protótipo no subnível da outra.
  ``` JavaScript
  // esta classe está herdando de uma classe Person já criada, com as propriedades: fistName,lastName,age, set and get fullname.
  function Student(firstName, lastName, age) {
    Person.call(this, firstName, lastName, age); //linha propriamente dita para fazer herança
    this._enrolledCourses = [];
   
    this.enroll = function(courseId) { 
      this._enrolledCourses.push(courseId);
    };
   
    this.getCourses = function() {
      return this.fullName + "'s enrolled courses are: " +
        this._enrolledCourses.join(', ');
    };
  }
  Student.prototype = Object.create(Person.prototype); //linha propriamente dita para fazer herança
  Student.prototype.constructor = Student;  //linha propriamente dita para fazer herança
  Student.fromPerson = function(person) {
    return new Student(person.firstName, person.lastName, person.age);
  }
  

  let jim = new Student('Jim', 'Cooper', 29);
  jim.enroll('CS205');
  jim.enroll('MA101');
  jim.enroll('PS101');
   
  display(jim.getCourses());

})();
  
  ```
  
  - Em Classes:
   Igualmente ao Java, usando a propriedade Extends, fazendo isso é feita automaticamente a herança. Lembrete: para usar o construtor da classe mãe , usa-se o método `super();`.
