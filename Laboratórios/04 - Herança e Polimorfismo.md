# Herança e Polimorfismo

## Exercício 1

> Considere a seguinte classe Numero. Cada instância de Número representa um determinado número inteiro o qual pode ser alterado durante o tempo de vida de cada instância. 
> Pretende-se agora construir uma nova entidade, NumeroComMemoria, que tem um comportamento semelhante à classe Numero (deve suportar pelo menos as mesmas funcionalidade) mas que tem a seguinte funcionalidade extra:
> É possível desfazer a última alteração realizada. Por exemplo, suponha que criou um NumeroComMemoria a representar o número 5 e de seguida se altera o seu valor para 10. A nova funcionalidade de desfazer a última alteração deverá permitir alterar o valor de 10 para 5.
> Realizar a funcionalidade de desfazer duas vezes seguidas deve deixar o número inalterado. Considerando o exemplo anterior, ao realizar o desfazer pela segunda vez, o valor do número deverá passar de 5 para 10.
> É possível obter o valor anterior. Caso não haja valor anterior (ainda não foi feita qualquer alteração ao número em causa), então devolve o próprio valor do número.

Realize as seguintes actividades:  
- Modelize este domínio utilizando o diagrama de classes UML.
- Concretize a classe NumeroComMemoria.


### Implementação do Problema em Java

```java
public class NumeroComMemoria extends Numero{

	private int _anterior;

	public NumeroComMemoria(int valor){
		super(valor);
		_anterior = valor;
	}

	public NumeroComMemoria(){}

	public void alteraValor(int valor){
		_anterior = _valor;
		_valor = valor;
	}

        public int anterior(){
            return anterior;
        }

	public void desfazer(){
		int state;
		state = _anterior;
		_anterior = _valor;
		_valor = state;
	}
}
```