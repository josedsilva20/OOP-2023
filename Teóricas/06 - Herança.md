# Herança

Consideremos um tabuleiro de Xadrez:
	
- tabuleiro tem 32 peças;

- peça tem posição;

- peça tem cor;

- a torre é uma peça;

- peão é uma peça.

    ...

> Existe a função de mover a peça.

Neste caso, peças diferentes podem ter operações de mover diferentes:

- uma torre move-se na linha ou na coluna onde está;
- o bispo move-se na diagonal;
- o peão move-se para a casa à sua frente.

Ou seja, todas as peças sabem se movimentar mas o comportamento é diferente para cada uma delas.

---

Consideremos agora um outro caso em que temos `Aluno` e `Pessoa`. Evidentemente um aluno é uma pessoa, e por isso dizemos que a relação entre essas duas entidades é do tipo `é um` (diferente da composição que é *tem um*).

Quando temos uma relação de `é um`, o aluno é uma pessoa que faz tudo que uma pessoa faz, mas também faz coisas específicas dele como frequentanar aulas ou fazer testes (chamam-se especialização).

Sempre que temos que uma relação de `é um`, não podemos representar como `tem um`. A forma de representar isso em PO é através do **`Mecanismo de Herança`**.

> Composição   ---> **tem um**
>
> Herança      ---> **é um**

---


## Conceitos Básicos sobre Herança

O código que está definido na primeira classe será herdado de forma automática pela segunda. No exemplo anterior, o código de pessoa é `herdado` pela classe `aluno`.

> Só usamos herança quando no modelo existe uma relação de `é um` porque senão dá problema.

Para usar Herança em java usamos a palavra reservada `extends`:

		
```java
public class Dog extends Animal
```

A classe `Animal` é chamada de **superclasse** (classe pai, classe ancestral ou classe base) de `Cão`.

A classe `Cão` é **subclasse**, descendente ou derivada de `Animal`.


> Cada classe só pode ter uma superclasse mas vários ascendentes.

![](images/Inheritance%20-%2006.png)


```java
public class B extends A
// todos os atributos e métodos são herdados do A

```
---


Se tentarmos aceder ele dá erro de compilação pois `B` herdar de `A` não quer dizer conseguir aceder aos atributos privados de `A`, em `B`.

Para resolver esse problema, podemos usar os métodos disponíveis em **A**, como por exemplo os do tipo *get*.

Podemos adicionar novos métodos em `B` (algo que só as classes derivadas sabem fazer) ou substituir os já existentes em `A` (modificando a semântica definida na superclasse, mudadando a sua implementação) fazendo **`override`**.

```java
public class Animal {
    private String _name;
    private Date _birthday;
    private Person _owner;

    public int getAge() {...}
    
    public Person getOwner() {...}

    public void makeNoise() {...}
}

public class Dog extends Animal {
    private Vacine[] _vacine;

    public void waggingTail() {...}
    
    public void makeNoise() {
        System.out.println(“ão ão”);
    }
}

public class Cat extends Animal {
    private int _numberLifes;

    public void climbTree() {...}
    
    public void makeNoise() {
        System.out.println(“miau miau”);
    }
}

```

## Overriding 

Consiste em substituir atributos e o código herdado de um método da superclasse e especializá-lo na classe derivada.

É importante usar a anotação `@override` antes do método a fazer substituição. Isto é considerado como sendo uma boa prática pois aumenta a legibilidade do código e também dizemos ao compilador que estamos a substituir um método da `superclasse`, por isso, se falharmos alguma coisa, ele dá erro de compilação.

Em java, todas as classes são obrigadas a herdar de uma e somente uma. 

> Se não dissermos de qual ela herda, então o Java afirma que a nossa classe herda da classe `Object`, ou seja, ele tem acesso aos métodos da classe Object como o ***toString()***.

> É impossível uma classe herdar de duas ao mesmo tempo.

---  

## Construtores herdados

A inicialização dos ***atributos do construtor*** da superclasse são inicializados na classe derivada. 

Para isso usámos a instrução `super()`, que invoca o código do construtor da superclasse e só depois disso é que inicilizá-mos os argumentos da classe derivada.

> A primeira linha de código deve ser a instrução `super()`. Se não fizermos isso, o compilador assume que invocámos o método super() sem argumentos, que é herdado pela classe `Object`.

```java
public class Animal {
    private String _name;
    private Date _birthday;
    private Person _owner;

    public Animal(String name, Date birthday, Person owner){
        _name = name;
        _birthday = birthday;
        _owner = owner;
    }
    
    ....
}

public class Dog extends Animal {
    private Vacine[] _vacine;

    public Animal (String name, Date birtday, Person owner, Vacine[] vacine){
        super(name, birthday, owner);
        _vacine = vacine;
    }

    ...
    
}
```


## Invocar metodos da superclasse

Se Dog herdar de Animal e animal tiver um metodo `getAge()` que retorna um inteiro:

```java
Dog d = new Dog();
d.getAge();
```
	

Se quisermos, podemos substituir o método herdado. Assim se alterarmos o `getAge()` dentro da classe `Dog`, o método invocado será `getAge()` da classe `Dog` e não da `Animal`.


Se quisermos executar um método da superclasse mas que já foi alterado na classe derivada devemos usar a palavra reservada `super` imediatamente antes do nome do método.

Exemplo:


```java
public class Animal{
	public int getAge(){
		return _age;
	}
}

@override
public class Dog (){
    public int getAge(){
        return 7 * super.getAge();
    }

```

## Substituição 

É um método igual com `mesmos parâmetros` e que fazem `coisas diferentes`. É nestes que usamos a tag `@override` por cima. 
> *Ver exemplo acima*


## Sobreposição

É um método com parâmetros diferentes e funcionalidade também diferente. Exemplo:

```java
public class Rectangle{
    private int _length, _width;

    public Rectangle(int l, int w) {
        _length = l;
        _width = w;
    }
    
    public void area() {
        return _length * _width;
    }

    public void print() {
        System.out.println(“length : “ + _length);
        System.out.println(“width : “ + _width);
    }

    public void setDimension(double l, double w) {
        _length = (l >= 0) ? l : 0;
        _width = (w >= 0) ? w : 0;
    }
}
```

```java
public class Box extends Rectangle {
    private int _height;

    public Box(int l, int w, int h) {
        super(l, w);
        _height = h;
    }

    public void volume() {
        // Utiliza o método area() herdado da superclasse
        return area() * _height;
    }

    @Override // Faz a substituição do método da superclasse
    public void print() {
        super.print();
        System.out.println(“height: “ + _height);
    }


    // Sobrepõe o método da superclasse
    public void setDimension(double l, double w, double h) {
        super.setDimension(l, w);
        if (h >= 0) _height = h;
        else _height = 0;
    }
}
```

> ***Supers encadeados não são permitidos em Java.***



		