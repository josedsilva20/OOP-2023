# Contentores e Iteradores

## Exercício 1

Uma empresa tem funcionários. Um funcionário tem um nome e um salário. O nome do funcionário é um identificador único. Dois funcionários são iguais se tiverem o mesmo identificador (ou seja, o mesmo nome). Uma empresa deve ter as seguintes funcionalidades:

- adicionar um funcionário à empresa mas não pode haver dois funcionários com o mesmo identificador. Caso o novo funcionário seja igual a um já existente, então não deve ser adicionado. O método deve indicar se houve sucesso a adicionar o funcionário;
- Escreve no terminal o nome e o salário de cada empregado;
- Obter os funcionários que tenham um salário superior a um dado valor. Caso não exista nenhum funcionário nas condições indicadas então deve ser devolvida uma lista vazia;
- Remover os funcionários cujo nome começa com uma dada cadeia de caracteres (utilizar o método startsWith da classe String);
- Devolver uma colecção de funcionários ordenados por salário e nome.


### Código da classe Funcionário

```java
public class Funcionario {
	private String _nome;
	private int _salario;

	public Funcioario(int salario, String nome){
		_nome = nome;
		_salario = salario;
	}

	public boolean equals(Funcionario func){
		return _nome.equals(func.nome());
	}

	public String nome(){
		return _nome;
	}

	public int salario(){
		return _salario;
	}

	public String toString(){
		return _nome + " " + _salario;
	}

	// Override do método equals do hashSet
	public boolean equals (Object obj){
		if (obj instanceof Empregado)
			return equals((Empregado) obj);
		return false
	}

	// Será usado para calcular o valor de dispersão e será usado pelo HashSet
	public int hashCode(){
		// classe string também tem um método que calcula o hashCode.
		return _nome.hashCode();
	}
}
```

### Comparador de nome e salário 

```java
// Precisamos importar a biblioteca java.util
import java.util.*;

// Precisa ser package private porque apenas aceita uma pública
class SalaryAndNameComparator implements Comparator<Funcionario>{

	@Override
	public int compare(Funcionario f1, Funcionario f2){
        // compara e devolve o menor salário se os mesmos forem diferentes
		if (f1.salario() != f2.salario())
			return f1.salario() - f2.salario();

        // se tiverem mesmo salario, compara o nome
		else 
			return f1.nome().compareTo(f2.salario());
	}
}
```


### Código da classe Empresa

```java
public class Empresa{
	private Set<Funcionario> _funcionarios;

	public Empresa(){
		_funcionarios = new HashSet<>();
		// usamos um treeset se quisermos ordenados
		// para usarmos o hashset precisamos do hashCode() e do equals(Object) que recebe object
		// se usarmos treeset só precisamos do equals
		// ao usarmos o hashset, a classe que o usa deve substituir esse objeto, dois objetos iguais têm o mesmo hash
	}

	public boolean addFuncionario(Funcionario func){
		return _funcionarios.add(func);
	}

	public void mostraFuncionarios(){
		for(func: _funcionarios)
			System.out.println(func.toString());
	}

	public List<Funcionario> salarioInferiorA(int valor){
		List<Funcionario> _superior = new ArrayList<>();
		for (func: _funcionarios)
			if (func.salario() > valor)
				_superior.add(func);
		return _superior;
	}

	public void removeCom(String comeca){
		Iterator iter = _funcionarios.iter();

		while(iter.hasNext()){
			Funcionario func = iter.next();
			if (func.nome().startsWith(comeca))
				iter.remove(func);
		}
	}

	public List<Funcionario> devolveOrdenados(){
		List<Funcionario> ordenados = new ArrayList<>(_funcionarios);
        ordenados.sort(new SalaryAndNameComparator());
        return ordenados;
	}
}
```

___

## Exercício 2 

Um estojo serve para guardar lápis. Um lápis tem uma marca e uma cor. Dois lápis são iguais se tiverem a mesma marca e cor. A marca e a cor são representadas por uma cadeia de caracteres. Um estojo tem uma dada capacidade. A capacidade deve ser definida no momento da criação do estojo. O estojo deve ter a seguinte funcionalidade:
- adição de um lápis;
- obter todos os lápis iguais a um dado lápis. A colecção devolvida deve ter em conta a ordem pela qual os lápis foram inseridos no estojo;
- remover um dado lápis;
- remover todos os lápis que tenham uma dada cor;
- obter a lista de lápis ordenados (alfabeticamente) de forma crescente por marca e cor. Note que esta ordenação não deve alterar a ordem pela qual os lápis são mantidos no estojo;
- obter a lista de lápis do estojo pela ordem em que eles foram inseridos.


### Código da classe Lápis

```java
public class Lapis {
    private String _marca;
    private String _cor;

    public Lapis(String marca, String cor){
        _marca = marca;
        _cor = cor;
    }

    public String marca(){
        return _marca;
    }

    public String cor(){
        return _cor;
    }

    public boolean equals(Lapis lapis){
        return (_marca.equals(lapis.marca()) && _cor.equals(lapis.cor()));
    }
}
```

### Código da classe Comparadora

```java
class BrandAndColorComparator implements Comparator<Lapis>{

	@Override
	public int Compare(Lapis l1, Lapis l2){
		if (!l1.marca().equals(l2.marca())){
			return l1.marca().compareTo(l2.marca());
		}
		else
			return l1.cor().compareTo(l2.cor());
	}
}
```

### Código da classe Estojo

```java
public class Estojo{
	private List<Lapis> _lapis; 

	public Estojo(int capacidade){
		_lapis = new ArrayList<>(capacidade);
	}

	public void addLapis(Lapis lapis){
		_lapis.add(lapis)
	}

	public List<Lapis> getEqualTo(Lapis lapis){
		List<Lapis> equal = new ArrayList<>();

		for(Lapis l: _lapis)
			if (l.equals(lapis))
				equal.add(lapis);
		return equal;
	}

	public void removeLapis(Lapis lapis){
		Iterator<Lapis> iter = new _lapis.iterator();

		while (iter.hasNext()){
			Lapis l = iter.next();
			if (l.equals(lapis))
				iter.remove(l);
		}
	}

	public void removeWithColor(String Color){
		Iterator<Lapis> iter = new _lapis.iterator();

		while (iter.hasNext()){
			Lapis l = iter.next();
			if (l.cor().equals(lapis.cor()))
				iter.remove(l);
		}
	}

	public List<Lapis> orderByBrandAndColor(){
		List<Lapis> ordered = new ArrayList<>(_lapis);
		ordered.sort(new BrandAndColorComparator());
		return ordered;
	}

	public List<Lapis> getByInsertionOrder(){
		List<Lapis> copy = new ArrayList<>(_lapis);
	}

}
```

## Exercício 3

Um navio tem tripulantes. Cada tripulante tem um nome, um ano de nascimento e um salário. Cada tripulante tem um identificador único no contexto do navio atribuído automaticamente pela aplicação. O navio tem que suportar a seguinte funcionalidade:
- manter o conjunto de tripulantes do navio. Deve ser possível aceder rapidamente ao tripulante que tem um dado identificador;
- obter o conjunto de tripulantes do navio que têm um salário inferior a um dado valor;
- remover o tripulante um dado identificador. Deve ser devolvido se a operação teve sucesso ou não;
- remover todos os tripulantes cujo ano de nascimento seja inferior a um dado valor.

### Código da classe Tripulante

```java
public class Tripulante{
	private String _nome;
	private int _salario;
	private int _anoDeNascimento;

	public Tripulante(String nome, int salario, int ano){
		_anoDeNascimento = ano;
		_salario = salario;
		_nome = nome;
	}

	public int salario(){
		return _salario;
	}

	public int ano(){
		return _anoDeNascimento;
	}

	public String nome(){
		return _nome;
	}
}
```

### Código da classe Navio

```java
public class Navio {
	private List<Tripulante> _tripulantes;

	public Navio (){
		_tripulantes = new ArrayList<>();
	}

	public void addTripulante(Tripulante trip){
		_tripulantes.add(trip);
	}

	public Tripulante getTripulantePorId(int id){
		return _tripulantes.get(id);
	}

	public List<Tripulante> tripulanteSalarioInferiorA(int valor){
		List<Tripulante> copy = new ArrayList<>();
		for(Tripulante t: _tripulantes)
			if (t.salario() < valor)
				copy.add(t);
		return copy;
	}

	public boolean removeById(int id){
		return _tripulantes.remove(id);
	}

	public void tripulanteAnoInferiorA(int ano){
		Iterator<Tripulante> iter = _tripulantes.iterator();

		while (iter.hasNext())
			if (t.ano() < ano){
				Tripulante t = iter.next();
				iter.remove(t);
			}
	}
}
```