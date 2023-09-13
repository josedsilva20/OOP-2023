# 1º Exercício

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