# Composição

## Exercicío 1

> Concretize em Java uma classe chamada Numero que deverá representar um número inteiro. Esta classe deverá permitir o seguinte:
> - obter o valor inteiro representado por uma dada instância de >Numero;
> - obter o número representado por uma instância de Numero como uma String;
> - por omissão, as instâncias criadas representam o número 0:
> é também possível criar uma instância de Numero que representa um dado número inteiro;
> - Verificar se dois objectos Numero são iguais ou não. Considere que duas instâncias são iguais desde que representem o mesmo número inteiro;
> - Devolver o número maior
> - Construa uma aplicação Java que tem como objectivo exercitar as funcionalidades da classe Numero. Assim é necessário especificar o método main, nesta ou noutra classe. Este método deverá criar duas instâncias de Numero e verificar o correcto funcionamento dos vários métodos definidos em Numero.

Primeiro modele este domínio e de seguida concretize-o.


### Domínio do Problema

![](images/Numero%20-%2003.png)

### Implementação do Problema em Java

```java
public class Numero {
	private int _valor;

    public Numero(){}

	public Numero(int valor){
		_valor = valor;
	}

	@Override
	public boolean equals(Numero numero){
		return _valor == numero.valor();
	}

        public void altera(int novoValor){
            _valor = novoValor;
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
---

## Exercício 2

> Altere o exercício anterior por forma a garantir que cada um dos números inteiros entre 0 e 99 será sempre representado pela mesma instância de Numero. Ou seja, quer-se uma solução que garanta que não é possível ter duas instâncias distintas de Numero a representar o número 5 (por exemplo).

### Implementação do Problema em Java

```java
public class Numero {
	private int _valor;
	private static final int SIZE = 99;

    // atributo ao nível da classe que guarda todos os numeros criados
	private static int[] _valores = new int[SIZE];

	public Numero(int valor){

        // verifica se o numero que queremos criar já existe
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