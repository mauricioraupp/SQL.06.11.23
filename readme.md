## Comandos de banco de dados

### Criar database
* Local para criar as tabelas do sistema
```
create database NOME_DATABASE;
```

### Executar o comando
```
Ctrl + Enter
```

### Selecionar database
```
use NOME_DATABASE;
```
<hr>

## Projeto site Ecommerce
* Tabela de usuarios
* Tabela de produtos
* Tabela de carrinho de compras

### Criar tabela usuarios

```
create table usuarios(
 id int not null auto_autoincrement,
 nome varchar(120) not null,
 email varchar(120) not null,
 senha varchar(120) not null,
 primary key(id)
);
```
* id: Identificador de cada registro
* not null: Campo  obrigatorio, não pode ser nulo
* auto_autoincrement: Soma +1 no ultimo registro de id
* varchar(120): Campo de texxto com 120 caracteres

### Criar tabela de produtos
```
create table produtos(
    id int not null auto_increment,
    modelo varchar(120),
    nome varchar(120) not null,
    valor float not null,
    primary_key(id)
);
```

### Criar tabela carrinho

```
create table carrinho(
    id int not null auto_autoincrement,
    id_usuario int not null,
    id_produto int not null,
    primary key(),
    foreign key(id_usuario) references usuarios(id),
    foreign key(id_produto) references produtos(id)
)
```
* foreign key: Chave estrangeira que recebe a referencia de outra tabela
* references: Atributo para definir a tabela e o campo estrangeiro

### Inserir usuarios
```
insert into usuarios(nome, email, senha) values('Renato Gaucho', 'teste@teste.com', 'secret')
```

### Inserir produto
```
insert into produtos(modelo, nome, valor) values('11', 'Iphone', 10500,99)
```

```
insert into carrinho(id_usuario, id_produto) values(43, 200);
insert into carrinho(id_usuario, id_produto) values(43, 189);
insert into carrinho(id_usuario, id_produto) values(43, 4);
insert into carrinho(id_usuario, id_produto) values(43, 123);
insert into carrinho(id_usuario, id_produto) values(43, 230);
```

### Listar todos usuarios
```
select * from usuarios;
```

### Listar os nomes e email dos usuarios
```
select nome, email from usuarios;
```

### Listar usuarios pelo id
```
select * from usuarios where id = 23;
```

### Verificar produtos no carrinho pelo id do usuario

```
select p.nome
from produtos p, carrinho c
where c.id_usuario = 23 AND p.id = c.id_produto;
```