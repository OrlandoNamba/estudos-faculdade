# 📚 Resumo de Aula - 20/09
Arquivo markdown destinado ao resumo e anotações referente a aula de banco de dados do dia 20/09/2024.

## 📝 Anotações 
Não é possível criar em tabelas uma relação de "muitos para muitos", pois o sql não possui suporte para isso. Nessa situação, será necessário criar uma tabela intermediária.

Deve-se começar criando as tabelas comuns, para que somente depois crie-se as tabelas dependentes. Pois essas tabelas dependentes utilizarão chaves estrangeiras.

As chaves estrangeiras devem ser sempre "NOT NULL"


## 💻 Alguns Comandos
```sql
IdAutor SMALLINT GENERED ALWAYS AS IDENTITY
```
O comando GENERATED ALWAYS AS IDENTITY indica que o sistema gera o ID de forma automática. No exemplo, refere-se ao ID do autor. <br> <br>

```sql
CONSTRAINT pk_ID_Autor PRIMARY KEY (IdAutor)
```
Esse comando indica que a chave primária da tabela Autor é a coluna IdAutor. O trecho CONSTRAINT pk_ID_Autor define uma nova restrição, chamada "pk_ID_Autor".<br> <br>

```sql
IdLivro SMALLINT GENERATED ALWAYS AS IDENTITY (START WITH 100 INCREMENT BY 1)
```
O comando em parênteses indica que o ID do livro começará a partir do número 100 e aumentará de 1 em 1.<br><br>

```sql
ISBN13 CHAR(13) UNIQUE
```
O comando CHAR indica que a coluna armazena caracteres e o UNIQUE assegura que não pode haver duas entradas iguais para ISBN13.<br><br>

```sql
DataPub DATE
```
DATE é um tipo de dado presente no SQL, referente a datas.<br><br>

```sql
PrecoLivro NUMERIC(10, 2) NOT NULL
```
NUMERIC(10, 2) define que podem haver 10 números à esquerda da vírgula e apenas 2 à direita. O NOT NULL indica que este campo não pode estar vazio.<br><br>

```sql
CONSTRAINT fk_id_editora FOREIGN KEY (IdEditora) REFERENCES Editora (IdEditora) ON DELETE CASCADE ON UPDATE CASCADE
```
- O prefixo fk indica que é uma FOREIGN KEY (chave estrangeira)..<br>
- FOREIGN KEY (IdEditora) faz referência ao IdEditora da tabela de livro;<br>
- O "REFERENCES Editora" faz referência a tabela Editora;<br>
- O último "(IdEditora)" faz referência a tabela Editora;<br>
- ON DELETE CASCADE ON UPDATE CASCADE significa que, ao excluir uma editora, os livros correspondentes serão excluídos automaticamente, e ao atualizar o nome da editora, a alteração será refletida na tabela de livros.<br><br>

```sql
CONSTRAINT verifica_preco CHECK (PrecoLivro >= 0)
```

O comando CHECK assegura que o preço do livro é maior ou igual a 0.<br><br>