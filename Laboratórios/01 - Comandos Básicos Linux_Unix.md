# Comandos básicos Unix
### Trocar o diretório
```shell
	$ cd dir/a/aceder
```
### Mostrar o conteúdo do diretório atual
```shell
	$ ls
```
Existem algumas tags extra que podemos usar neste comando, tais como:

```shell
	$ ls -l	---> apresenta mais info sobre cada entrada do dir.
	
	$ ls -al---> mostra tudo do -l e adiciona algumas coisas.
```

> O `-al` mostra tudo do -l e também **/.** e **/..** que indicam **diretório atual e anterior**.
> 
>  Também mostra os ***ficheiros ocultos, nome do dono, grupo, tamanho do ficheiro, data da última modificação e mostra as permissões (rwxrwxrwx)***.  
> 
> o x significa que se for um ficheiro, posso executá-lo e se for um diretório podemos entrar nele.

### Criar directórios

```shell
	$ mkdir nome_do_diretorio
```

### Remover directórios vazios

```shell
	$ rmdir nome_do_diretorio
```

### Remover ficheiro (ação irreversível)

```shell
	$ rm ficheiro_a_apagar
```
> quando executamos este comando, o ficheiro é apagado permanentemente. Para resolver esse problema usamos a tag `-i`.

  
### Remover ficheiro (com confirmação)

Este comando pede uma confirmação ao utilizador antes de realmente apagar o ficheiro.

```shell
	$ rm -i ficheiro_a_apagar
```

### Remover directório (não vazio)

Este comando elimina o directório e tudo que o contenha de forma recursiva.

```shell
	$ rm -r diretório_a_remover
```

> Se quisermos, podemos acrescentar o `-i` para confirmar cada ficheiro dentro do mesmo.
R
### Copiar ficheiros

Este comando copia o ficheiro `a` e cola no diretório `d3` com o nome `c`.

```shell
	$ cp d1/d2/a d3/c
```

### Renomear ficheiros

Este comando renomeia o ficheiro `ficheiro_origem` para `novo_nome` e remove o `ficheiro_origem`. Ou seja, muda o nome de `ficheiro_origem` para `novo_nome`.

```shell
	$ mv ficheiro_origem novo_nome
```
> Também serve para mover um ficheiro de um directório para o outro. Se em `novo_directorio` houver um `ficheiro_origem` ele remove-o:

```shell
	$ mv ./ficheiro_origem novo_directorio/
```

> Para evitar esse risco, recorremos ao `-i` após o comando (`mv`).

> `Dica`:
> 
> O ***mv***, ***cp*** e ***rm*** são sempre aconselhados a levar o `-i` para evitar erros, pois são *irreversíveis*





