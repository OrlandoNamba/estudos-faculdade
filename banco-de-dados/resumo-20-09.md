# Resumo de Aula - 20/09
Arquivo markdown destinado ao resumo e anotações referente a aula de banco de dados do dia 20/09/2024.

## Anotações 
Não é possível criar em tabelas uma relação de "muitos para muitos", pois o sql não possui suporte para isso. Nessa situação, será necessário criar uma tabela intermediária.

Deve-se começar criando as tabelas comuns, para que somente depois crie-se as tabelas dependentes. Pois essas tabelas dependentes utilizarão chaves estrangeiras.

As chaves estrangeiras devem ser sempre "NOT NULL"


## Alguns Comandos
```
IdAutor SMALLINT GENERED ALWAYS AS IDENTITY
```
O código "GENERED ALWAYS AS IDENTITY" que o sistema gera o ID de forma automática. No exempo, ID do autor. <br> <br>

```
CONSTRAINT pk_ID_Autor PRIMARY KEY (IdAutor)
```
Indica que a chave primária da tabela Autor é a coluna IdAutor. O trecho "CONSTRAINT pk_ID_Autor" define uma nova restrição (constraint), ou seja, definiu uma nova restrição, chamada "pk_ID_Autor".<br> <br>

```
IdLivro SMALLINT GENERATED ALWAYS AS IDENTITY (START WITH 100 INCREMENT BY 1)
```
O comando em parênteses retorna que o ID do livro vai começar a partir do número 100, e ira aumentar de 1 em 1.<br><br>

```
ISBN13 CHAR(13) UNIQUE
```
O comando CHAR retorna que e o comando UNIQUE retorna que não pode ter duas ISBN13 <br><br>

```
DataPub DATE
```
DATE é um tipo de declaração de dado presente no sql, referente a datas.<br><br>

```
PrecoLivro NUMERIC(10, 2) NOT NULL
```
NUMERIC (10, 2) diz que pode ter 10 números a esquerda da vírgula e apenas 2 a direita da mesma e o NOT NULL retorna que este campo não pode estar vazio.<br><br>

```
CONSTRAINT fk_id_editora FOREIGN KEY (IdEditora) REFERENCES Editora (IdEditora) ON DELETE CASCADE ON UPDATE CASCADE
```
- O "fk" presente no ínicio do nome do id_editora, significa que é uma FOREIGN KEY (Chave Estrangeira).<br>
- O "FOREIGN KEY (IdEditora)" faz referencia ao IdEditora da tabela de livro;<br>
- O "REFERENCES Editora" faz referência a tabela Editora;<br>
- O último "(IdEditora)" faz referência a tabela Editora;<br>
- O "ON DELETE CASCADE ON UPDATE CASCADE" serve para quando for excluida uma editora da tabela de editoras, o livro será excluído automaticamente, e quando for atualizado o nome da editora, também será atualizado na tabela do livro. <br><br>

```
CONSTRAINT verifica_preco CHECK (PrecoLivro >= 0)
```

O comando "CHECK" verifica se o preço do livro é maior ou igual a 0.<br><br>