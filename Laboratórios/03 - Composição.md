# Composição

## Exercicío 1

### Domínio do Problema

![](images/Numero%20-%2003.png)

### Implementação do Problema em Java

```java
public class Numero {
	private int _valor;

	public Numero(int valor){
		_valor = valor;
	}

	@Override
	public boolean equals(Numero numero){
		return _valor == numero.valor();
	}

	public int valor(){
		return _valor;
	}

	@Override
	public String toString(){
		return "" + _valor;
	}

	public Numero maior(Numero numero){
		if (_valor >= numero.valor())
			return this;
		return numero;
	}

}
```

```java
public class Numero {
	private int _valor;
	private static final int SIZE = 99;
	private static int[] _valores = new int[SIZE];

	public Numero(int valor){

		for (int i = 0; i < SIZE; i++){
			if (valor == _valores[i])
				return;
		}

		_valor = valor;
	}

	public Numero(){}


	public boolean equals(Numero numero){
		return _valor == numero.valor();
	}

	public int valor(){
		return _valor;
	}

	public String toString(){
		return "" + _valor;
	}

	public Numero maior(Numero numero){
		if (_valor >= numero.valor())
			return this;
		return numero;
	}


	// main para testar os casos de erro
	public static void main(String[] args){
		Numero a = new Numero(5);
		Numero b = new Numero(6);

		System.out.println(a.toString() + b.toString());
		System.out.println("" + a.equals(b) + b.maior(a));

	}
}
```