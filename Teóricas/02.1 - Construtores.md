Quando criámos uma classe, devemos sempre inicializá-la para não haver valores estranhos (qtd negativa).

Para isso usámos **Construtores**.

# Construtores

São métodos que têm o nome da classe e que inicializam todos os atributos necessários.

Estes métodos obrigam que ao criar o objeto, ele seja inicializado.

Os construtores não têm valor de retorno, pelo que não se põe nenhum ao declará-lo.

`exemplo:`  
```java
	public Caneta (int cap, String c){  
		_qtdTinta = 0;  
		_capacidade = cap;  
		_cor = c;  
	}

```
```java
	public class Caneta {
		int _qtdTinta;
		int _capacidade;
		String _cor;

		Caneta c = new Caneta();
	}
```

Para usarmos os construtores dentro duma classe:

```
	Caneta c = new Caneta(100, "verde");
```

Podemos ter vários construtores. Para isso eles devem ter argumentos diferentes, mas o mesmo nome.

`Exemplo:`

```java
	public Caneta(int cap){
		_qtdTinta = 0;
		_capacidade = cap;
		_cor = "preta";
	}
```
Podemos usar o código dum construtor dentro de outros. Para isso devemos pôr na sua primeira linha a isntrução ***this(...)***:

```java
	public Caneta(int cap){
		this(cap, "preta");
	}
```

> *NB:* Isto ajuda a reduzir a duplicação de código.






