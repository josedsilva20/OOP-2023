# 1º Exercício

Considere o seguinte domínio de aplicação:
> Um pneu tem uma dada pressão de ar. Cada pneu tem também uma pressão de ar recomendada. Um pneu quando é criado tem uma dada pressão de ar e sabe também a sua pressão de ar recomendada. Pode-se saber a pressão de ar  e a pressão recomendada de um dado pneu. Não deve ser possível alterar a pressão de ar recomendada de um pneu. É possível saber se um pneu está vazio ou não. O pneu está vazio caso a sua pressão de ar seja inferior a 80% da pressão de ar recomendada. É possível alterar a pressão de ar de um pneu. Se o pneu passar a ter uma pressão de ar superior a 150% da pressão de ar recomendada, então o pneu estoira (fica com um furo) e fica com uma pressão de ar igual a 0. Quando um pneu tem um furo já não é possível alterar a sua pressão. É possível saber se um pneu tem um furo ou não.
> Primeiro modele o este domínio e depois concretize-o.

### Domínio

![](Pneu-02.png)

### Implementação do Problema

```java
    public class Pneu {
        private int _pressao; 
        private int _pressaoRecomendada;
        private boolean _furado;

        public Pneu (int pressao, int pRecomendada){
            _pressao = pressao;
            _pressaoRecomendada = pRecomendada;
        }

        public int getPressao(){
            return _pressao;
        }

        public int getPressaoRecomendada(){
            return _pressaoRecomendada;
        }

        public boolean vazio(){
            return (_pressao < (_pressaoRecomendada * 0.8));
        }

        public boolean furado(){
            return _furado;
        }

        public void alteraPressao(int valor){
            if(!furado)
                _pressao = valor;
                if (_pressao > (_pressaoRecomendada * 1.5)){
                    furado = true;
                    _pressao = 0;
                }
        }
    }

```

# 2º Exercício

Considere o seguinte domínio de aplicação:

> Um carro tem sempre uma marca, quilometragem, velocidade máxima e quatro pneus. Quando o carro é criado a sua quilometragem é igual 0 e é necessário indicar a marca, a velocidade máxima e os pneus do novo carro. O carro deve ficar sempre com a marca indicada. É possível saber a quilometragem do carro, a sua marca e se algum dos seus pneus está vazio. A marca é representada simplesmente por uma cadeia de caracteres. É possível também alterar o valor da quilometragem do carro. Um carro pode estar em movimento ou parado. Se estiver em movimento, então terá uma dada velocidade. Um carro pode ainda estar travado, Se o carro estiver travado, então não se movimentará. Um carro quando é criado está sempre travado. É possível travar ou destravar um carro. É ainda possível alterar a velocidade do carro desde que o carro não esteja travado. Não é possível ultrapassar a velocidade máxima do carro.
> Modele o este domínio e concretize-o em Java.

### Domínio

![](images/Carro%20-%2002.png)

### Implementação do Problema

```java
public class Carro {
	private String _marca;
	private int _quilometragem;
	private int _vMax;
	private Pneu[] _pneus;
	private int _velocidade;
	private boolean _travado;


	public Carro (String marca, Pneu[] pneus, int vMax){
		_marca = marca;
		_pneus = pneus;
		_vMax = vMax;
		_travado = true;
	}

	public int quilometragem(){
		return _quilometragem;
	}

	public String marca(){
		return _marca;
	}

	public boolean pneuVazio(){
		for (Pneu pneu: _pneus)
			if (pneu.vazio())
				return false;
		return true;
	}

	public void travado(){
		return _travado;
	}

	public void travar (){
		_velocidade = 0; 
		_travado = true;
	}

	public void alterarQuilometragem(int valor){
		_quilometragem += valor; 
	}

	public void alteraVelocidade(int valor){
		if ((_velocidade + valor) <= _vMax)
			_velocidade += valor; 
	}
}
```