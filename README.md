# TRABALHO 01:  "AiQueFome!"
Trabalho desenvolvido durante a disciplina de Banco de dados

# Sumário

### 1. COMPONENTES<br>
Integrantes do grupo<br>
Eduardo Olmo Santana:eduardo.olmosantana@gmail.com<br>
Nycolly do Nascimento Mendes:nycollydonascimentomendes@gmail.com<br>
Paulo Cezar Rocha Furtado:paulocezarrf@hotmail.com<br>
Elisa Andrade de Jesus:moon.anonimos.es@gmail.com<br>

### 2.INTRODUÇÃO E MOTIVAÇÃO<br>

> A empresa "AiQueFome!" busca alimentar seus clientes não so com comida, mas com cultura. É uma empresa de delivery de comida que busca levar aos seus clientes novas experiencias em forma de pratos caracteristicos de diversas nações, para que eles possam sentir um gostinhos das outras culturas dentro do conforto de seu proprio lar. Para alcançar seu objetivo a empresa está querendo criar um aplicativo que irá permitir seus clientes pedirem suas refeições de forma fácil e prática. Para gerenciar os pedidos, o aplicativo irá armazenar as informações relativas ao Restaurante, Produto, Pedido, Entregador, Cliente e ao Endereço. 
 

### 3.MINI-MUNDO<br>

>O aplicativo "AiQueFome!" foi feito para facilitar e otimizar os serviços de delivery de restaurantes e possibilitar que o clientes tenham acesso a diversos produtos alimentícios em um só lugar. Dessa forma o "AiQueFome!" criou um sistema que funciona da seguinte forma: Restaurante produz produto, o qual compõe o pedido, que é retirado pelo Entregador para ser entregue ao cliente, que possui um endereço. Do restaurante será armazenado o CNPJ (atributo identificador), e nome. Do produto armazenaremos código do produto(identificador), nome e preço. Do pedido armazenaremos código do pedido, seu atributo identificador, a data e hora, o seu preço total e a o CNPJ do restaurante que produziu o pedido. Do entregador armazenaremos cpf, que é seu identificador, turno, salário e nome. Do cliente armazenaremos: cpf(identificador), nome e telefone. Do endereço armazenaremos as informações do tipo do logradouro, nome do logradouro, número e bairro. Da entrega serão armazenadas as informações do código do pedido e a data e hora.<br>
Um restaurante pode produzir um ou vários produtos, enquanto um produto pode ser produzido por um ou vários restaurantes. Um produto pode compor um ou vários pedidos, assim como um pedido pode ser composto por um ou vários produtos. Um cliente pode fazer um ou vários pedidos, mas um pedido só pode ser feito por apenas um único cliente. Um entregador pode retirar um ou vários pedidos, porém um pedido só pode ser retirado por apenas um entregador. Um entregador pode entregar para nenhum ou vários clientes, e um cliente pode receber de um ou vários entregadores. Por fim, um  cliente possui apenas um endereço, e um endereço só pode estar relacionado a apenas um cliente.

### 4.PERGUNTAS A SEREM RESPONDIDAS E TABELA DE DADOS<br>
#### 4.1 QUAIS PERGUNTAS PODEM SER RESPONDIDAS COM O SISTEMA PROPOSTO?
    
> A Empresa "AiQueFome!" precisa inicialmente dos seguintes relatórios:
* Relatório que mostre o nome de cada entregador e a quantidade de entregas feitas por ele.
* Relatório que apresente o nome do restaurante, a quantidade de pedidos realizados por ele e o valor total desses pedidos.
* Relatório que mostre a quantidade das entregas feitas após certo horário.
* Relatório que mostre o nome de cada cliente e o valor total dos pedidos que esse cliente pediu.
* Relatório que mostre o nome do bairro e a quantidade de clientes que residem nele, agrupando pelo bairro.

 ### 5.MODELO CONCEITUAL<br>

![image](https://user-images.githubusercontent.com/92343021/200873951-5b5c0785-fdc3-4182-8b82-6c79248e1cb1.png)
    
#### 5.1 Validação do Modelo Conceitual
    Grupo 1: Ilanna,Mariana,Bruna,Daianny
    

#### 5.2 Descrição dos dados 

    RESTAURANTE: Tabela que armazena os dados de cada restaurante. 
    Atributos: CNPJ(identificador) e nome.
    
    PRODUTO: Tabela que armazena as informações dos produtos.
    Atributos: código do produto(identificador), nome e preço.
    
    PEDIDO: Tabela que armazena as informações referentes dos pedidos.
    Atributos: código do pedido(identificador), data e hora e preço total.
    
    ENTREGADOR: Tabela que armazena os dados do entregador.
    Atributos: CPF(identificador), nome, salário, e turno.
    
    CLIENTE: Tabela que armazena os dados dos clientes.
    Atributos: CPF(identificador), nome e telefone.
    
    ENDERECO: Tabela que armazena o endereço dos clientes.
    Atributos: número, tipo logradouro, nome logradouro e bairro.
    
    RESTAURANTE/PRODUTO(Produz): Um restaurante pode produzir um ou vários produtos, enquanto um produto pode ser produzido por um ou vários restaurantes.
    
    PRODUTO/PEDIDO(Compoe): Um produto pode compor um ou vários pedidos, assim como um pedido pode ser composto por um ou vários produtos. 
    
    PEDIDO/CLIENTE(Feito): Um cliente pode fazer um ou vários pedidos, mas um pedido só pode ser feito por apenas um único cliente.
    
    PEDIDO/ENTREGADOR(Retira): Um entregador pode retirar um ou vários pedidos, porém um pedido só pode ser retirado por apenas um entregador. 
    
    ENTREGADOR/CLIENTE(Entrega): Um entregador pode entregar para nenhum ou vários clientes, e um cliente pode receber de um ou vários entregadores. Esse relacionamento possui o atributo data e hora.
    
    CLIENTE/ENDERECO(Possui): Um cliente possui apenas um endereço, e um endereço só pode estar relacionado a apenas um cliente.
    

### 6	MODELO LÓGICO<br>
        
![image](https://user-images.githubusercontent.com/92343021/200873616-e520677a-2a3b-4a15-a6f8-51b8d6ec9c9f.png)

### 7	MODELO FÍSICO<br>
        
   	drop table if exists CLIENTE_ENDERECO,PRODUTO,RESTAURANTE,ENTREGADOR,PEDIDO,PESSOA,RESTAURANTE_PRODUTO,PRODUTO_PEDIDO,ENTREGADOR_CLIENTE;

	CREATE TABLE RESTAURANTE (
	    cnpj VARCHAR(18) PRIMARY KEY,
	    nome VARCHAR(80)
	);

	CREATE TABLE PRODUTO (
	    cod_produto INTEGER PRIMARY KEY,
	    nome VARCHAR(80),
	    preco FLOAT
	);

	CREATE TABLE PEDIDO (
	    cod_pedido INTEGER PRIMARY KEY,
	    FK_RESTAURANTE_cnpj VARCHAR(18),
	    preco_total FLOAT,
	    FK_ENTREGADOR_FK_PESSOA_cpf VARCHAR(14),
	    FK_CLIENTE_ENDERECO_FK_PESSOA_cpf VARCHAR(14),
	    data_hora TIMESTAMP
	);

	CREATE TABLE ENTREGADOR (
	    turno VARCHAR(80),
	    salario FLOAT,
	    FK_PESSOA_cpf VARCHAR(14) PRIMARY KEY
	);

	CREATE TABLE CLIENTE_ENDERECO (
	    FK_PESSOA_cpf VARCHAR(14) PRIMARY KEY,
	    telefone INTEGER,
	    tipo_logradouro VARCHAR(100),
	    nome_logradouro VARCHAR(100),
	    numero INTEGER,
	    bairro VARCHAR(100)
	);

	CREATE TABLE PESSOA (
	    cpf VARCHAR(14) PRIMARY KEY,
	    nome VARCHAR(80)
	);

	CREATE TABLE RESTAURANTE_PRODUTO (
	    fk_RESTAURANTE_cnpj VARCHAR(18),
	    fk_PRODUTO_cod_produto INTEGER
	);

	CREATE TABLE PRODUTO_PEDIDO (
	    fk_PRODUTO_cod_produto INTEGER,
	    fk_PEDIDO_cod_pedido INTEGER
	);

	CREATE TABLE ENTREGADOR_CLIENTE (
	    fk_ENTREGADOR_FK_PESSOA_cpf VARCHAR(14),
	    fk_CLIENTE_ENDERECO_FK_PESSOA_cpf VARCHAR(14),
	    FK_PEDIDO_cod_pedido INTEGER PRIMARY KEY,
	    data_hora TIMESTAMP
	);

	ALTER TABLE PEDIDO ADD CONSTRAINT FK_PEDIDO_2
	    FOREIGN KEY (FK_ENTREGADOR_FK_PESSOA_cpf)
	    REFERENCES ENTREGADOR (FK_PESSOA_cpf)
	    ON DELETE CASCADE;

	ALTER TABLE PEDIDO ADD CONSTRAINT FK_PEDIDO_3
	    FOREIGN KEY (FK_CLIENTE_ENDERECO_FK_PESSOA_cpf)
	    REFERENCES CLIENTE_ENDERECO (FK_PESSOA_cpf)
	    ON DELETE CASCADE;

	ALTER TABLE PEDIDO ADD CONSTRAINT FK_PEDIDO_4
	    FOREIGN KEY (FK_RESTAURANTE_cnpj)
	    REFERENCES RESTAURANTE (cnpj)
	    ON DELETE CASCADE;

	ALTER TABLE ENTREGADOR ADD CONSTRAINT FK_ENTREGADOR_2
	    FOREIGN KEY (FK_PESSOA_cpf)
	    REFERENCES PESSOA (cpf)
	    ON DELETE CASCADE;

	ALTER TABLE CLIENTE_ENDERECO ADD CONSTRAINT FK_CLIENTE_ENDERECO_2
	    FOREIGN KEY (FK_PESSOA_cpf)
	    REFERENCES PESSOA (cpf)
	    ON DELETE CASCADE;

	ALTER TABLE RESTAURANTE_PRODUTO ADD CONSTRAINT FK_RESTAURANTE_PRODUTO_1
	    FOREIGN KEY (fk_RESTAURANTE_cnpj)
	    REFERENCES RESTAURANTE (cnpj)
	    ON DELETE CASCADE;

	ALTER TABLE RESTAURANTE_PRODUTO ADD CONSTRAINT FK_RESTAURANTE_PRODUTO_2
	    FOREIGN KEY (fk_PRODUTO_cod_produto)
	    REFERENCES PRODUTO (cod_produto)
	    ON DELETE CASCADE;

	ALTER TABLE PRODUTO_PEDIDO ADD CONSTRAINT FK_PRODUTO_PEDIDO_1
	    FOREIGN KEY (fk_PRODUTO_cod_produto)
	    REFERENCES PRODUTO (cod_produto)
	    ON DELETE CASCADE;

	ALTER TABLE PRODUTO_PEDIDO ADD CONSTRAINT FK_PRODUTO_PEDIDO_2
	    FOREIGN KEY (fk_PEDIDO_cod_pedido)
	    REFERENCES PEDIDO (cod_pedido)
	    ON DELETE CASCADE;

	ALTER TABLE ENTREGADOR_CLIENTE ADD CONSTRAINT FK_ENTREGADOR_CLIENTE_2
	    FOREIGN KEY (fk_ENTREGADOR_FK_PESSOA_cpf)
	    REFERENCES ENTREGADOR (FK_PESSOA_cpf)
	    ON DELETE CASCADE;

	ALTER TABLE ENTREGADOR_CLIENTE ADD CONSTRAINT FK_ENTREGADOR_CLIENTE_3
	    FOREIGN KEY (fk_CLIENTE_ENDERECO_FK_PESSOA_cpf)
	    REFERENCES CLIENTE_ENDERECO (FK_PESSOA_cpf)
	    ON DELETE CASCADE;

	ALTER TABLE ENTREGADOR_CLIENTE ADD CONSTRAINT FK_ENTREGADOR_CLIENTE_4
	    FOREIGN KEY (FK_PEDIDO_cod_pedido)
	    REFERENCES PEDIDO (cod_pedido)
	    ON DELETE CASCADE;


       
### 8	INSERT APLICADO NAS TABELAS DO BANCO DE DADOS<br>
        insert into PESSOA
	values ('111.111.111-22', 'Paolo Versalhes Nunes'),
		   ('222.222.222-33', 'David Barcelos'),
           ('333.333.333-44', 'Sônia Vasconcelos Santino'),
           ('444.444.444-55', 'André Soares Batista'),
           ('555.555.555-66', 'Vilmar Santos da Cunha'),
           ('666.666.666-77', 'Mario Fernandes Fellipy'),
           ('777.777.777-88', 'Laís Portinari Costa'),
           ('888.888.888-99', 'Ariel Fago'),
           ('999.999.999-11', 'Luca Amorim'),
		   ('111.111.111-11', 'Pedro Augusto Pina'),
           ('222.222.222-22', 'Álvares Virgulino'),
      	   ('333.333.333-33', 'Amanda Pessoa Carlos'),
           ('444.444.444-44', 'Luís Augusto Silva'),
		   ('555.555.555-55', 'Paola Jõao Orlando'),
		   ('666.666.666-66', 'Emanoel Silveira'),
		   ('777.777.777-77', 'Moisés Lima Soares'),
		   ('888.888.888-88', 'Sofia Pascal'),
		   ('999.999.999-99', 'Pâmela Oliveira Santos');


	insert into ENTREGADOR
	values ('Matutino', 1500.00, '111.111.111-22'),
           ('Vespertino', 1200.00, '222.222.222-33'),
           ('Vespertino', 1360.00, '333.333.333-44'),
           ('Matutino', 1450.00, '444.444.444-55'),
           ('Noturno', 1600.00,'555.555.555-66'),
           ('Matutino', 1520.00, '666.666.666-77'),
           ('Vespertino', 1480.00, '777.777.777-88'),
           ('Noturno', 1550.00, '888.888.888-99'),
           ('Noturno', 1580.00, '999.999.999-11');
		   
	insert into CLIENTE_ENDERECO
	values ('111.111.111-11', 998885430, 'Rua', 'Castelo', 155, 'Jardim Limoeiro'),
           ('222.222.222-22', 999532192, 'Avenida', 'Rui Barbosa', 23, 'Bairro de Fátima'),
      	   ('333.333.333-33', 988221445, 'Rua', 'Limoeiro', 26, 'Barcelona'),
           ('444.444.444-44', 992323555, 'Rodovia', 'do Rosário', 55, 'Nova Almeida'),
		   ('555.555.555-55', 992365539, 'Rua', 'Porto Alegre', 122, 'Nova Almeida'),
		   ('666.666.666-66', 998644222, 'Avenida', 'Carvalho', 15, 'Barcelona'),
		   ('777.777.777-77', 990843323, 'Rua', 'Lázaro Verde', 35, 'Jardim Limoeiro'),
		   ('888.888.888-88', 987657668, 'Rua', 'Monte Seco', 52, 'Bairro de Fátima'),
		   ('999.999.999-99', 994523223, 'Avenida', 'Pimenta', 165, 'Nova Almeida');

	insert into RESTAURANTE
	values ('12.332.646/0002-25', 'McDonalds'),
           ('16.225.938/0002-17', 'BurgerKing'),
           ('08.427.254/0002-19', 'Subway');

	insert into PRODUTO
	values (01, 'Hambúrguer', 15.00),
   	       (02, 'Pizza', 40.00),
           (03, 'Água', 2.00),
           (04, 'Suco', 5.00),
           (05, 'Refrigerante', 10.00),
           (06, 'Batata Frita', 8.50);
		   
 
	insert into PEDIDO
	values (001, '12.332.646/0002-25', 28.50, '222.222.222-33', '111.111.111-11', '2022-09-12 11:25:22'),
     	   (002, '16.225.938/0002-17', 50.00, '222.222.222-33', '777.777.777-77', '2022-09-12 11:32:12'),
   		   (003, '16.225.938/0002-17', 15.00, '888.888.888-99', '999.999.999-99', '2022-10-15 17:56:25'),
       	   (004, '12.332.646/0002-25', 10.50, '666.666.666-77', '444.444.444-44', '2022-08-23 06:27:26'),
           (005, '08.427.254/0002-19', 18.50, '333.333.333-44', '333.333.333-33', '2022-08-27 12:58:53'),
     	   (006, '12.332.646/0002-25', 73.50, '111.111.111-22', '555.555.555-55', '2022-10-16 08:24:36'),
     	   (007, '08.427.254/0002-19', 10.00, '444.444.444-55', '222.222.222-22', '2022-10-22 07:34:00'),
    	   (008, '08.427.254/0002-19', 27.00, '444.444.444-55', '888.888.888-88', '2022-10-23 05:58:18'),
   		   (009, '16.225.938/0002-17', 100.00, '333.333.333-44', '666.666.666-66', '2022-09-06 13:08:26'),
    	   (010, '08.427.254/0002-19', 130.00, '999.999.999-11', '777.777.777-77', '2022-07-26 17:09:19');

	insert into RESTAURANTE_PRODUTO
	values ('12.332.646/0002-25', 01),
           ('12.332.646/0002-25', 02),
           ('12.332.646/0002-25', 03),
           ('12.332.646/0002-25', 04),
           ('12.332.646/0002-25', 05),
           ('12.332.646/0002-25', 06),
           ('16.225.938/0002-17', 01),
           ('16.225.938/0002-17', 02),
           ('16.225.938/0002-17', 03),
           ('16.225.938/0002-17', 04),
           ('16.225.938/0002-17', 05),
           ('16.225.938/0002-17', 06),
           ('08.427.254/0002-19', 01),
           ('08.427.254/0002-19', 02),
           ('08.427.254/0002-19', 03),
           ('08.427.254/0002-19', 04),
           ('08.427.254/0002-19', 05),
           ('08.427.254/0002-19', 06);

	insert into PRODUTO_PEDIDO
 	 values (01, 001),
         (04, 001),
         (06, 001),
         (02, 002),
         (05, 002),
         (01, 003),
         (03, 004),
         (06, 004),
         (05, 005),
         (06, 005),
         (01, 006),
         (02, 006),
         (05, 006),
         (06, 006),
         (05, 007),
         (01, 008),
         (03, 008),
         (05, 008),
         (02, 009),
         (02, 009),
         (05, 009),
         (05, 009),
         (02, 010),
         (02, 010);

	insert into ENTREGADOR_CLIENTE
 	 values ('222.222.222-33', '111.111.111-11',001, '2022-09-12 12:20:50'),
         ('222.222.222-33', '777.777.777-77',002, '2022-09-12 12:50:00'),
         ('888.888.888-99', '999.999.999-99',003, '2022-10-15 19:36:35'),
         ('666.666.666-77', '444.444.444-44',004, '2022-08-23 08:12:30'),
         ('333.333.333-44', '333.333.333-33',005, '2022-08-27 14:44:23'),
         ('111.111.111-22', '555.555.555-55',006, '2022-10-16 10:14:46'),
         ('444.444.444-55', '222.222.222-22',007, '2022-10-22 09:12:00'),
         ('444.444.444-55', '888.888.888-88',008, '2022-10-23 07:16:18'),
         ('333.333.333-44', '666.666.666-66',009, '2022-09-06 15:03:33'),
         ('999.999.999-11', '777.777.777-77',010, '2022-07-26 18:06:39');
	
	
	


### 9	TABELAS E PRINCIPAIS CONSULTAS<br>
    https://colab.research.google.com/drive/16b3oBZUtT7vv-7eI0l2TMzgiczN3K4W_?usp=sharing
    
    
#### 9.1	CONSULTAS DAS TABELAS COM TODOS OS DADOS INSERIDOS (Todas) <br>
![image](https://user-images.githubusercontent.com/92343021/200924692-6edc974e-bd6d-4706-a4ff-fa58f2a2d9b2.png)

![image](https://user-images.githubusercontent.com/92343021/200924753-92d9af97-69f1-4a11-b224-1e11024fadc9.png)

![image](https://user-images.githubusercontent.com/91472785/200929881-f88f90ba-45e8-4c75-a48e-15643f39f98a.png)
	
![image](https://user-images.githubusercontent.com/92343021/200925283-44ee2b78-922e-4422-895b-99f2c88f70ce.png)

![image](https://user-images.githubusercontent.com/92343021/200925762-94afffcd-e35f-4267-a2db-57ed6c7c1994.png)

![image](https://user-images.githubusercontent.com/92343021/200925814-cc9d207f-6549-4006-b692-47598d15897f.png)

![image](https://user-images.githubusercontent.com/92343021/200925950-819b64e5-5777-450d-b38c-d83107b3a81d.png)

![image](https://user-images.githubusercontent.com/92343021/200925989-baeec5cc-7b18-44a5-959f-cf88bfe4f601.png)

![image](https://user-images.githubusercontent.com/92343021/200930615-8fc964f5-df45-4f87-9849-977c9371ca9e.png)


	
># Marco de Entrega 01: Do item 1 até o item 9.1<br>

#### 9.2	CONSULTAS DAS TABELAS COM FILTROS WHERE (Mínimo 4)
select * from Pedido where preco_total > 30;<br>
![Image](https://user-images.githubusercontent.com/84751064/201201102-262c5b4c-e259-4daa-8ea1-cacb815c2559.png)


select  FK_PESSOA_cpf ,tipo_logradouro,telefone from Cliente_Endereco where telefone <> '987657668';<br>
![Image](https://user-images.githubusercontent.com/84751064/201201839-3316a08d-e210-4ab2-af4a-8b4ec176eeaf.png)




select *from Entregador where turno <> 'Matutino';<br>
![Image](https://user-images.githubusercontent.com/84751064/201202016-2263465b-e1de-4865-8e0d-9c26949eccd2.png)


select *from Produto where preco > 10.00 ;<br>
![Image](https://user-images.githubusercontent.com/84751064/201202263-d8daacda-bf0f-48bd-aff6-88be61f22bb1.png)


#### 9.3	CONSULTAS QUE USAM OPERADORES LÓGICOS, ARITMÉTICOS E TABELAS OU CAMPOS RENOMEADOS (Mínimo 11)
    a) Criar 5 consultas que envolvam os operadores lógicos AND, OR e Not
    
select *from Produto where preco > 10.00 and preco <30.00 ;<br>
![image](https://user-images.githubusercontent.com/84751064/201212447-74152e01-98a9-4439-bad8-021581a3a8ec.png)

select *from Pedido where(data_hora <>'2022-07-26 18:06:39'and data_hora='2022-09-12 12:20:50') or FK_ENTREGADOR_FK_PESSOA_cpf<>'444.444.444-55';<br>
![image](https://user-images.githubusercontent.com/84751064/201212925-28f42a2d-4ee4-4994-ab2b-328df1c78df1.png)

select *from Entregador where(turno<>'Noturno'or turno='Matutino') and salario >=1200.00;<br>
![image](https://user-images.githubusercontent.com/84751064/201213021-0f973e27-350a-400a-b9c7-afc2eb314931.png)


select *from Entregador where(turno<>'Noturno'or turno='Vespertino') and salario >=1300.00;<br>
![image](https://user-images.githubusercontent.com/84751064/201213855-a8a4f9d8-3450-4f57-8acf-80b74262f59d.png)


select *from Pedido where preco_total < 20.00 or cod_pedido<>005;<br>
![image](https://user-images.githubusercontent.com/84751064/201213742-63eb7526-2607-4563-88f0-1a966060e91e.png)


select *from Cliente_Endereco where (tipo_logradouro<>'rua' or bairro<>'Nova Almeida')and not nome_logradouro='Rua do Rosário';<br>
![image](https://user-images.githubusercontent.com/84751064/201213628-9d0fa054-3020-404e-89e5-f77745f85888.png)

select *from Pedido where not preco_total =50.00 or FK_ENTREGADOR_FK_PESSOA_cpf<>'222.222.222-33';<br>
![image](https://user-images.githubusercontent.com/84751064/201213319-14f913a4-a786-4143-b0fd-d860519bcb34.png)

	
	b) Criar no mínimo 3 consultas com operadores aritméticos 
    
PRIMEIRO:
select * from COMPOE where fk_PRODUTO_cod_produto > 2*2;<br>
![image](https://user-images.githubusercontent.com/103542882/200878717-cfa2fa85-37b0-46cd-b8b3-8b3c3bc36f8f.png)

SEGUNDO:
select * from PEDIDO where preco_total*50/100 > 2^4;<br>
![image](https://user-images.githubusercontent.com/103542882/200879460-a74e0f2b-095a-4766-abc1-5169b7479128.png)

	c) Criar no mínimo 3 consultas com operação de renomear nomes de campos ou tabelas
    

#### 9.4	CONSULTAS QUE USAM OPERADORES LIKE E DATAS (Mínimo 12) <br>
    a) Criar outras 5 consultas que envolvam like ou ilike
    
select * from produto where nome like '%a';<br>
![image](https://user-images.githubusercontent.com/91472785/200929491-c63e0e0c-53b4-46fc-bc5d-1eff19aef403.png)

select * from cliente_endereco where bairro like 'B%';<br>
![image](https://user-images.githubusercontent.com/91472785/200926258-f6f1d9cf-a5bf-4d35-9608-8e71438cf221.png)

select * from entregador where turno like 'V%';<br>
![image](https://user-images.githubusercontent.com/91472785/200926333-81451549-def7-4409-8025-9fd2df8589c9.png)

select * from restaurante where nome like '%u%';<br>
![image](https://user-images.githubusercontent.com/91472785/200926454-b423337a-f1cc-4ceb-8389-8615db1deccd.png)

select * from pessoa where nome like 'P%' or nome like 'A%';<br>
![image](https://user-images.githubusercontent.com/91472785/200926521-58335f8f-0404-491a-971a-8fe23e79fe30.png)
    
    b) Criar uma consulta para cada tipo de função data apresentada.

select *, current_date - data_hora as tempo from pedido;<br>
![image](https://user-images.githubusercontent.com/91472785/200935520-e6d593d7-8fc0-459b-b9b2-548a6d13270a.png)

select *, now() - data_hora as tempo from entregador_cliente;<br>
![image](https://user-images.githubusercontent.com/91472785/200935207-eb8d4aa5-440b-4377-9748-17e8aef8c343.png)

select *, age(current_date,data_hora) as tempo from pedido;<br>
![image](https://user-images.githubusercontent.com/91472785/200935054-33f136ac-39b2-41ad-9c17-5c93f8a29f3e.png)

select *, date_part('month',age(current_date,data_hora)) as "tempo em meses" from entregador_cliente;<br>
![image](https://user-images.githubusercontent.com/91472785/201132561-03c09750-fc66-4650-9a65-4067d2992d3c.png)

select * from entregador_cliente where (extract(day from current_date-data_hora) < 20);<br>
![image](https://user-images.githubusercontent.com/91472785/201136153-e70381c7-4894-47f6-9b7c-75c9626db516.png)

select * from pedido where extract(hour from data_hora) < 12;<br>
![image](https://user-images.githubusercontent.com/91472785/201138431-919ce2d0-1c7a-491b-8dbe-5cedb812dc20.png)

select * from entregador_cliente where extract(hour from data_hora) < 12;<br>
![image](https://user-images.githubusercontent.com/91472785/201138558-ef723b29-96d0-4803-8306-783daebc4eb5.png)



#### 9.5	INSTRUÇÕES APLICANDO ATUALIZAÇÃO E EXCLUSÃO DE DADOS (Mínimo 6)<br>
    a) Criar minimo 3 de exclusão

 update Pessoa set nome='Fernanda Fagundes' where cpf='555.555.555-66';
select * from Pessoa;<br>
![Image](https://user-images.githubusercontent.com/84751064/201203050-bc3a2f9f-ddf7-4914-a1ba-53466bdddc41.png)



update Produto set nome='Tortilhas' where cod_produto='06';
select * from Produto;<br>
![Image](https://user-images.githubusercontent.com/84751064/201203269-fd2efef7-899b-4528-8345-19e1214b0f55.png)


update CLIENTE_ENDERECO set tipo_logradouro='rua' where Bairro='Barcelona';
select * from CLIENTE_ENDERECO;<br>
![Image](https://user-images.githubusercontent.com/84751064/201204014-3ea98852-72e3-4daa-a1c0-cac241644be5.png)

	b) Criar minimo 3 de atualização

DELETE FROM Pessoa where nome like 'A%';
select * from Pessoa;<br>
![Image](https://user-images.githubusercontent.com/84751064/201204948-e87fde17-059f-4d35-8d92-45bc9f74a381.png)

DELETE FROM Entregador_cliente where data_hora='2022-09-12 12:50:00' ;
select * from Entregador_Cliente<br>
![Image](https://user-images.githubusercontent.com/84751064/201205878-bc353822-ee90-4dc0-9d5a-8e170eec461f.png)

DELETE FROM Cliente_Endereco where  tipo_logradouro='Avenida' or bairro like 'N%' ;
select * from Cliente_Endereco<br>
![Image](https://user-images.githubusercontent.com/84751064/201206732-8c7f5a51-1ab0-4eeb-8706-aea57dea7f53.png)

#### 9.6	CONSULTAS COM INNER JOIN E ORDER BY (Mínimo 6)<br>
    a) Uma junção que envolva todas as tabelas possuindo no mínimo 2 registros no resultado

select cnpj,cod_produto,cod_pedido,e.fk_pessoa_cpf,pessoa.nome,ce.fk_pessoa_cpf,ps.nome<br>
from restaurante_produto as rp<br>
inner join restaurante as r<br>
on(rp.fk_restaurante_cnpj = r.cnpj)<br>
inner join produto as pr<br>
on(rp.fk_produto_cod_produto = pr.cod_produto)<br>
inner join produto_pedido as pp<br>
on(pr.cod_produto = pp.fk_produto_cod_produto)<br>
inner join pedido as pe<br>
on(pe.cod_pedido = pp.fk_pedido_cod_pedido)<br>
inner join entregador as e<br>
on(e.fk_pessoa_cpf = pe.fk_entregador_fk_pessoa_cpf)<br>
inner join pessoa<br>
on(e.fk_pessoa_cpf = pessoa.cpf)<br>
inner join entregador_cliente as ec<br>
on(e.fk_pessoa_cpf = ec.fk_entregador_fk_pessoa_cpf)<br>
inner join cliente_endereco as ce<br>
on(ec.fk_cliente_endereco_fk_pessoa_cpf = ce.fk_pessoa_cpf)<br>
inner join pessoa as ps<br>
on(ce.fk_pessoa_cpf = ps.cpf)<br>
order by ce.fk_pessoa_cpf;<br>

![Imagem do WhatsApp de 2022-11-10 à(s) 17 49 30](https://user-images.githubusercontent.com/91472785/201203268-1bcd9a0f-1a7e-4288-8f8f-70c084d3260d.jpg)

    b) Outras junções que o grupo considere como sendo as de principal importância para o trabalho
select r.nome as restaurante,p.nome as produto<br>
from restaurante as r<br>
inner join restaurante_produto as rp<br>
on(rp.fk_restaurante_cnpj = r.cnpj)<br>
inner join produto as p<br>
on(rp.fk_produto_cod_produto = p.cod_produto)<br>
![image](https://user-images.githubusercontent.com/91472785/201206014-37e3bc5b-9180-4882-b78a-5332d42a6b1a.png)


select fk_pessoa_cpf,nome
from entregador
inner join pessoa
on(pessoa.cpf = entregador.fk_pessoa_cpf)
![image](https://user-images.githubusercontent.com/91472785/201205037-bbe5488a-5007-4585-9e97-c26d37ade3e7.png)

select nome,cod_pedido<br>
from entregador<br>
inner join pessoa<br>
on(pessoa.cpf = entregador.fk_pessoa_cpf)<br>
inner join pedido<br>
on(entregador.fk_pessoa_cpf = pedido.fk_entregador_fk_pessoa_cpf)<br>
![image](https://user-images.githubusercontent.com/91472785/201208623-9650b7be-3eb5-4311-b4e0-77c17b6dd112.png)

select fk_pessoa_cpf,nome
from cliente_endereco as ce
inner join pessoa
on(pessoa.cpf = ce.fk_pessoa_cpf)
![image](https://user-images.githubusercontent.com/91472785/201207387-f3799631-59d7-411e-8bec-f30acd921490.png)

select nome,cod_pedido<br>
from cliente_endereco as ce<br>
inner join pessoa<br>
on(ce.fk_pessoa_cpf = pessoa.cpf)<br>
inner join pedido<br>
on(pedido.fk_cliente_endereco_fk_pessoa_cpf = ce.fk_pessoa_cpf)<br>
![image](https://user-images.githubusercontent.com/91472785/201209371-2d13a2e2-2a4c-4f27-a87b-3db5076a54e5.png)



#### 9.7	CONSULTAS COM GROUP BY E FUNÇÕES DE AGRUPAMENTO (Mínimo 6)<br>
    a) Criar minimo 2 envolvendo algum tipo de junção
select pessoa.nome, count(pedido.cod_pedido) as qtd_entregas<br>
from entregador<br>
inner join pessoa<br>
on (pessoa.cpf = entregador.fk_pessoa_cpf)<br>
inner join pedido<br>
on (entregador.fk_pessoa_cpf = pedido.fk_entregador_fk_pessoa_cpf)<br>
group by pessoa.nome;<br>
![image](https://user-images.githubusercontent.com/92343021/200932809-0d143044-8e29-4ab3-8286-66e9bc5a05ca.png)

select restaurante.nome, count(pedido.cod_pedido) as qtd_pedidos, sum(pedido.preco_total) as valor_total<br>
from restaurante<br>
inner join pedido<br>
on (restaurante.cnpj = pedido.fk_restaurante_cnpj)<br>
group by restaurante.nome;<br>
![image](https://user-images.githubusercontent.com/92343021/200934612-4c5f5392-41a8-4976-ace0-e7ee2fb150cc.png)

select pessoa.nome, sum(pedido.preco_total) as valor_total<br>
from pessoa<br>
inner join cliente_endereco<br>
on (pessoa.cpf = cliente_endereco.fk_pessoa_cpf)<br>
inner join pedido<br>
on (cliente_endereco.fk_pessoa_cpf = pedido.fk_cliente_endereco_fk_pessoa_cpf)<br>
group by pessoa.nome;<br>
![image](https://user-images.githubusercontent.com/92343021/200936150-4f848acb-3bfe-4d56-9764-06f8fca3bc79.png)

select cliente_endereco.bairro,<br>
count(cliente_endereco.fk_pessoa_cpf) as qtd_clientes<br>
from cliente_endereco<br>
group by bairro;<br>
![image](https://user-images.githubusercontent.com/92343021/201430392-235e0aba-c3d8-42e8-a6fd-f8b2b260fcc6.png)

select entregador.turno,<br>
count(entregador.fk_pessoa_cpf) as qtd_entregadores,<br> 
sum(entregador.salario) as soma_salario<br>
from entregador<br>
group by turno;<br>
![image](https://user-images.githubusercontent.com/92343021/201431035-876589a2-980d-42f4-a785-f2285a6f15d1.png)

select produto_pedido.fk_pedido_cod_pedido,<br> 
count(produto.cod_produto) as qtd_produtos<br>
from produto_pedido<br>
inner join produto<br>
on (produto.cod_produto = produto_pedido.fk_produto_cod_produto)<br>
group by produto_pedido.fk_pedido_cod_pedido<br>
order by produto_pedido.fk_pedido_cod_pedido;<br>

![image](https://user-images.githubusercontent.com/92343021/201432265-03a93b4d-851f-44bb-90bf-903de2cf23b3.png)

#### 9.8	CONSULTAS COM LEFT, RIGHT E FULL JOIN (Mínimo 4)<br>
    a) Criar minimo 1 de cada tipo
select pessoa.cpf,<br>
pessoa.nome,<br>
entregador.salario,<br>
entregador.turno<br>
from entregador<br>
right outer join pessoa<br>
on(pessoa.cpf = entregador.fk_pessoa_cpf);<br>	

![image](https://user-images.githubusercontent.com/92343021/201438227-d7a56bc4-206c-4a6d-a896-a425712469cd.png)

select pessoa.cpf,<br>
pessoa.nome,<br> 
cliente_endereco.telefone,<br> 
cliente_endereco.tipo_logradouro,<br> 
cliente_endereco.nome_logradouro,<br> 
cliente_endereco.numero,<br> 
cliente_endereco.tipo_logradouro<br> 
from pessoa<br> 
left outer join cliente_endereco<br> 
on(cliente_endereco.fk_pessoa_cpf = pessoa.cpf);<br> 

![image](https://user-images.githubusercontent.com/92343021/201435741-7daa119c-9e31-4765-a10d-5a3de4306f64.png)

select * <br> 
from entregador<br> 
full outer join entregador_cliente<br> 
on(entregador.fk_pessoa_cpf = entregador_cliente.fk_entregador_fk_pessoa_cpf)<br> 
full outer join cliente_endereco<br> 
on(cliente_endereco.fk_pessoa_cpf = entregador_cliente.fk_cliente_endereco_fk_pessoa_cpf)<br> 

![image](https://user-images.githubusercontent.com/92343021/201437813-3e04de4e-cbad-4b0a-8308-2ba7125c8947.png)

select pessoa.cpf,<br> 
pessoa.nome,<br> 
entregador.salario,<br> 
entregador.turno,<br> 
cliente_endereco.telefone,<br> 
cliente_endereco.tipo_logradouro,<br> 
cliente_endereco.nome_logradouro,<br> 
cliente_endereco.numero,<br> 
cliente_endereco.tipo_logradouro<br> 
from entregador<br> 
right outer join pessoa<br> 
on(pessoa.cpf = entregador.fk_pessoa_cpf)<br> 
left outer join cliente_endereco<br> 
on(cliente_endereco.fk_pessoa_cpf = pessoa.cpf);<br> 

![image](https://user-images.githubusercontent.com/92343021/201438723-45419f1a-cfc6-47dd-8006-b989d8b43bd3.png)


#### 9.9	CONSULTAS COM SELF JOIN E VIEW (Mínimo 6)<br>
        a) Uma junção que envolva Self Join (caso não ocorra na base justificar e substituir por uma view)
        b) Outras junções com views que o grupo considere como sendo de relevante importância para o trabalho

#### 9.10	SUBCONSULTAS (Mínimo 4)<br>

select * from entregador
where turno in('Matutino','Vespertino');<br>
![image](https://user-images.githubusercontent.com/91472785/201218402-4261f0ad-96a1-4dcd-abeb-9cabff345ccc.png)

select * 
from cliente_endereco
where bairro not in('Nova Almeida','Barcelona');<br>
![image](https://user-images.githubusercontent.com/91472785/201224118-579b2319-1cd1-4b5e-a9a8-86db94cd018d.png)

     a) Criar minimo 1 envolvendo GROUP BY

select nome,count(cod_produto)<br>
from produto<br>
inner join produto_pedido as pp<br>
on(produto.cod_produto = pp.fk_produto_cod_produto)<br>
where nome in('Pizza','Refrigerante')<br>
group by nome<br>
order by count(cod_produto) desc;<br>
![image](https://user-images.githubusercontent.com/91472785/201221449-deb39e3b-421e-4ced-a29b-013546edc28b.png)

     
     b) Criar minimo 1 envolvendo algum tipo de junção
     
select cod_pedido,nome from produto<br>
inner join produto_pedido as pp<br>
on(pp.fk_produto_cod_produto = produto.cod_produto)<br>
inner join pedido<br>
on(pp.fk_pedido_cod_pedido = pedido.cod_pedido)<br>
where nome in('Hambúrguer','Batata Frita');<br>
![image](https://user-images.githubusercontent.com/91472785/201218075-9c362a8f-3e72-4562-9045-c73abcc61eaa.png)



># Marco de Entrega 02: Do item 9.2 até o ítem 9.10<br>

### 10 RELATÓRIOS E GRÁFICOS (Usar template disponibilizado)
[Template de relatórios](https://github.com/discipbdint/public_samples/blob/main/BD_Exemplo_Relatorios_Empresa_VA.ipynb "Template relatórios")

#### a) análises e resultados provenientes do banco de dados desenvolvido (usar modelo disponível)
#### b) link com exemplo de relatórios será disponiblizado pelo professor no AVA
#### OBS: Esta é uma atividade de grande relevância no contexto do trabalho. Mantenha o foco nos 5 principais relatórios/resultados visando obter o melhor resultado possível.

    

### 11	AJUSTES DA DOCUMENTAÇÃO, CRIAÇÃO DOS SLIDES E VÍDEO PARA APRESENTAÇAO FINAL <br>

#### a) Modelo (pecha kucha)<br>
#### b) Tempo de apresentação 6:40 

># Marco de Entrega 03: Itens 10 e 11<br>
<br>
<br>
<br> 



### 12 FORMATACAO NO GIT:<br> 
https://help.github.com/articles/basic-writing-and-formatting-syntax/
<comentario no git>
    
##### About Formatting
    https://help.github.com/articles/about-writing-and-formatting-on-github/
    
##### Basic Formatting in Git
    
    https://help.github.com/articles/basic-writing-and-formatting-syntax/#referencing-issues-and-pull-requests
    
    
##### Working with advanced formatting
    https://help.github.com/articles/working-with-advanced-formatting/
#### Mastering Markdown
    https://guides.github.com/features/mastering-markdown/

    
### OBSERVAÇÕES IMPORTANTES

#### Todos os arquivos que fazem parte do projeto (Imagens, pdfs, arquivos fonte, etc..), devem estar presentes no GIT. Os arquivos do projeto vigente não devem ser armazenados em quaisquer outras plataformas.
1. <strong>Caso existam arquivos com conteúdos sigilosos<strong>, comunicar o professor que definirá em conjunto com o grupo a melhor forma de armazenamento do arquivo.

#### Todos os grupos deverão fazer Fork deste repositório e dar permissões administrativas ao usuário do git "profmoisesomena", para acompanhamento do trabalho.

#### Os usuários criados no GIT devem possuir o nome de identificação do aluno (não serão aceitos nomes como Eu123, meuprojeto, pro456, etc). Em caso de dúvida comunicar o professor.


Link para BrModelo:<br>
http://www.sis4.com/brModelo/download.html
<br>


Link para curso de GIT<br>
![https://www.youtube.com/curso_git](https://www.youtube.com/playlist?list=PLo7sFyCeiGUdIyEmHdfbuD2eR4XPDqnN2?raw=true "Title")


