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