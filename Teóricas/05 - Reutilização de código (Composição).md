
# Reutilização de código

# Composição
É um mecanismo que consiste em construir uma classe à custa de outras que já existam, diminuindo o trabalho e evitando a duplicação de código.

Por exemplo, um rectângulo é representado através de pontos:

![](images/Point_Rectangle%20-%2005.png)

```java
public void move(int dx, int dy){
	origem.move(dx, dy);
	destino.move(dx, dy);
}
```




