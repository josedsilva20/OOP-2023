
# Reutilização de código

# Composição
É um mecanismo que consiste em construir uma classe à custa de outras que já existam, diminuindo o trabalho e evitando a duplicação de código.

Por exemplo, um rectângulo é representado através de pontos:

![](images/Point_Rectangle%20-%2005.png)

> Em vez de representarmos os pontos `origem` e `destino` no diagrama correspondente à classe rectangle, descrevemos através da associação qual argumento da classe `Point` está incluído na classe `Rectangle`.

```java
public void move(int dx, int dy){
	origem.move(dx, dy);
	destino.move(dx, dy);
}
```

## Fugas de Privacidade

Quando temos um método que retorna um objeto temos uma fuga de privacidade, pois retornamos a referência do mesmo. Exemplo:

```java
public Poit getPoint(){
	return _origin;
}
```

Para solucionar isso, retornamos uma cópia do objeto que queríamos. Ou então usámos `Objectos Imutáveis`.

### Objectos imutáveis

São objetos que após criados, é impossível alterar os seus estados. Um bom exemplo disso é uma string, em que não conseguimos alterar o seu estado.

```java
public class Point{
    private int _x;
    private int _y;

    public Point(int x, int y) {
        _x = x;
        _y = y;
    }

    public int getX() {
        return _x;
    }

    public int getY() {
        return _y;
    }

    public Point move(int dx, int dy) {
        return new Point(_x + dx,_y + dy);
    }

    public boolean equals(Point r) {
        // remains the same
    }
}
```

### Composição e Fugas de privacidade nos Arrays

Há fuga de privacidade quando temos um `get` que retorna um atributo da classe e esse tipo de atributo é um array.

```java
public Point[] getPoints(){
    return _points;
}

    //isto não impede de fazermos:

Point[] p = a.getPoints();
p[0] = new Point(0,0);
```

> Para resolver esse problema em vez de retornarmos a referência do array, retornamos a cópia:

```java

// Usando a versão Imutável de Ponto
public Point[] getPoint() {
    Point[] temp = new Point[_points.length];

    for (int i = 0; i < _point.length; i++) {
        temp[i] = _points[i];
    }

    return temp;
} 

// ou então usando a versão mutável
// esta versão também pode ser chamada de deep copy
public Point[] getPoints() {
    Point[] temp = new Point[_points.length];

    for (int i = 0; i < _points.length; i++) {
        Point p = _points[i];
        temp[i] = new Point(p.getX(), p.getY());
    }

    return temp;
}
```

E se o programador quiser mesmo modificar o array dentro da classe?

> **NÃO DEVE FAZER!** 
> 
> Se quiser fazer, define um método na classe que é responsável por fazer isso.


***"keep it secret, keep it safe"***


# Convenções de codificação em Java

É o conjunto de regras para nomear classes, métodos e atributos.

Os nomes devem ter significados e devem ser explicativos e perceptíveis, ou seja, só pelo nome devemos perceber o que é e o que faz.

## Nomes de classes e interfaces

- Começar por uma `maiúscula`. As letras seguintes são `minúsculas`, excepto no início de novas palavras.
- Não usar traços de união
- Evitar o uso de abreviaturas e acrónimos.
- **Bons exemplos:** *Gato, PeleGato*
- **Maus exemplos:** *gato, PULGA, Gato_pata*

## Nomes de métodos

- Letras minúsculas excepto a primeira letra de novas palavras
- Não usar traços de união
- Usar verbos
- **Bons exemplos:** *correr(), correrDepressa(), chamarJerry()*
- **Maus exemplos:** *Felix(), Aceder(), obter_Peso()*

## Nomes de variáveis

- Letras minúsculas excepto a primeira letra de novas palavras
- Não usar traços de união
- Curtos mas com significado
- Evitar nomes com uma letra, excepto se forem índices utilizados num ciclo com poucas instruções:

    - i, j, k, m, n para inteiros;
    - c, d, e para caracteres;
- **Bons exemplos:** *acariciado, gato, meuComprimento*.
- **Maus exemplos:** *Felix, meu_Comprimento*.

## Nomes de variáveis de instância e de classe (não constantes)

Segue as mesmas regras do caso anterior com a resticção adicional de que devem  começar com um traço de união (underscores).

- **Bons exemplos:** *_pessoa, _contador, _totalCount*

## Nomes de constantes
- Letras maiúsculas e palavras separadas por traços de união.
- **Bons exemplos:** *NUM_OSSOS, MAX_PONTOS*.

> Só as variáveis de classe é que podem ser classifciadas como constantes. Uma variável de classe é uma constante quando é declarada como final e não é possível alterar a entidade referenciada pela variável de classe. Isto implica que o tipo da variável de classe deve ser imutável. Em Java, os tipos imutáveis incluem os tipos primitivos, String, os tipos Wrapper (Long, Integer, ...) e colecções imutáveis de tipos imutáveis. Um tipo é imutável quando não fornece nenhuma forma de alterar o conteúdo das suas instâncias.


## Acrónimos
Caso o nome a utilizar para um tipo, método ou variável (com a excepção de constantes) inclua um acrónimo, então só a primeira letra do acrónimo é que deverá ficar em maiúscula, devendo as restantes passarem a minúsculas. Caso o nome diga respeito a uma variável ou método, se o acrónimo for a primeira parte do nome então a primeira letra do acrónimo também deverá passar para minúscula.





