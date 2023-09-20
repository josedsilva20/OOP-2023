# Variaveis em Java
	
## Inicialização

### Variáveis Locais

São atribuídos valores automaticmente pelo java.

### Atributos não estáticos

É atribuído um valor por omissão (os predefinidos para os tipos: 0 para int, null para String...).

> Pode ainda ser atribuído um valor na sua declaração:

```java
    public class Caneta {
	    private int tinta = 2;
	}
```

Também pode ser inicializada dentro do construtor:
```java
    public Caneta(int quantidade, String marca){
        _quantidade = quantidade;
        _marca = marca;
    }
```

### Atributos estáticos

É atribuído um valor por omissão (os predefinidos para os tipos: 0 para int, null para String...).


> Pode ser atribuído um valor na declaração:

A inicialização é feita quando é feita uma abordagem ao código da classe caneta, ou seja a primeira vez em que se faz referência à essa classe.

> Como é ao nível da classe **não faz sentido** ter construtor.

### Constantes

São definidas com a palavra reservada `final`:
```java
	int f(int x){
		final int l = x; //dentro do método o valor é sempre igual
	}
```
Precisam sempre ser inicializadas na sua declaração, portanto se fizermos:

```java
    final Caneta c = new Caneta (---, ---);
```
> ``Atenção:`` isto apenas garante que o objeto c vai sempre referenciar a essa caneta criada, mas não garante que os atributos dela sejam sempre os mesmos, pois podem ser alterados: 

> ex: 
```java
    c.escreve ("abc");
```

Neste outro caso:
```java
    public static final int x = 50;
```
		
Isto quer dizer que temos uma variável que é um `atributo estático` da classe `caneta` que tem valor `50`, e como é `final`, ele nunca vai mudar de valor, que é 50. Sempre que tivermos algo do género `Caneta.x`, o compilador substitui isso pelo valor 50. 

---

O operador `+` pode também ser usado como:

>Se tivermos duas strings 
```java
    String s = "abc", s1 = "def";
	String s2 = s + s2;
    // concatena as strings
```

## Sobreposição - Overloading

Permite que numa mesma classe possamos ter vários métodos com mesmo nome.

Obrigatoriamente não podem ter os mesmos parâmetros. Exemplo:

```java
    // escreve a msg
    public int escreve (String msg){
		System.out.println(msg);
	}

    // escreve a msg n vezes.
	public int escre(String msg, int n){
        for ( int i = 0; i < n; i++)
			if (!escreve(msg)) // vai buscar o metodo escreve (msg) e não o escreve (msg, n)
			    return i;

	    return n;
	}
```


	