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

>O aplicativo "AiQueFome!" foi feito para facilitar e otimizar os serviços de delivery de restaurantes e possibilitar que o clientes tenham acesso a diversos produtos alimentícios em um só lugar. Dessa forma o "AiQueFome!" criou um sistema que funciona da seguinte forma: restaurante produz produto, o qual compõe o pedido, que é retirado pelo entregador para ser entregue ao cliente, que possui um endereço. Do restaurante será armazenado o CNPJ (identificador), e nome. Do Produto armazenaremos código do produto(identificador), nome e preço. Do pedido armazenaremos código do pedido(identificador), a data e hora, o seu preço total e a o CNPJ do restaurante que produziu o pedido; é importante armazenar a quantidade do produto que está compondo um pedido. Da Pessoa armazenaremos o CPF(identificador) e o nome. O entregador é uma pessoa que tem turno e salário. O cliente é uma pessoa que tem telefone. Do endereço armazenaremos as informações do tipo do logradouro, nome do logradouro, número e bairro. Da entrega serão armazenadas as informações do código do pedido e a data e hora. Um restaurante pode produzir um ou vários produtos, enquanto um produto pode ser produzido por um ou vários restaurantes. Um produto pode compor um ou vários pedidos, assim como um pedido pode ser composto por um ou vários produtos. Um cliente pode fazer um ou vários pedidos, mas um pedido só pode ser feito por apenas um único cliente. Um entregador pode retirar um ou vários pedidos, porém um pedido só pode ser retirado por apenas um entregador. Um entregador pode entregar para nenhum ou vários clientes, e um cliente pode receber de um ou vários entregadores. Por fim, um cliente possui apenas um endereço, e um endereço só pode estar relacionado a apenas um cliente.

### 4.PERGUNTAS A SEREM RESPONDIDAS E TABELA DE DADOS<br>
#### 4.1 QUAIS PERGUNTAS PODEM SER RESPONDIDAS COM O SISTEMA PROPOSTO?
    
> A Empresa "AiQueFome!" precisa inicialmente dos seguintes relatórios:
* Relatório que mostre o nome de cada entregador e a quantidade de entregas feitas por ele.
* Relatório que apresente o nome do restaurante e o valor total dos pedidos realizados por ele.
* Relatório que mostre a quantidade das entregas feitas em cada turno.
* Relatório que mostre o nome de cada cliente e a quantidade de pedidos feitos por ele.
* Relatório que mostre o nome do bairro e a quantidade de clientes que residem nele, agrupando pelo bairro.

 ### 5.MODELO CONCEITUAL<br>

![image](https://user-images.githubusercontent.com/91472785/204053853-e1f73c7d-0ef8-4fe2-991d-9927ee62aac4.png)
    
#### 5.1 Validação do Modelo Conceitual
	Grupo 1: Ilanna,Mariana,Bruna,Daianny
    

#### 5.2 Descrição dos dados 

	RESTAURANTE: Tabela que armazena os dados de cada restaurante. 
	Atributos: CNPJ(identificador) e nome.

	PRODUTO: Tabela que armazena as informações dos produtos.
	Atributos: código do produto(identificador), nome e preço.

	PEDIDO: Tabela que armazena as informações referentes dos pedidos.
	Atributos: código do pedido(identificador), cnpj do restaurante, data e hora e preço total.

	PESSOA: Tabela que armazena os dados das pessoas(entregadores e clientes).
	Atributos: CPF(identificador) e nome.

	ENTREGADOR: Tabela que armazena os dados do entregador.
	Atributos: salário e turno.

	CLIENTE: Tabela que armazena os dados dos clientes.
	Atributos: telefone.

	ENDERECO: Tabela que armazena o endereço dos clientes.
	Atributos: número, tipo logradouro, nome logradouro e bairro.

	RESTAURANTE/PRODUTO(Produz): Um restaurante pode produzir um ou vários produtos, enquanto um produto pode ser produzido por um ou vários restaurantes.

	PRODUTO/PEDIDO(Compoe): Um produto pode compor um ou vários pedidos, assim como um pedido pode ser composto por um ou vários produtos. Esse relacionamento possui o atributo quantidade.

	PEDIDO/CLIENTE(Feito): Um cliente pode fazer um ou vários pedidos, mas um pedido só pode ser feito por apenas um único cliente.

	PEDIDO/ENTREGADOR(Retira): Um entregador pode retirar um ou vários pedidos, porém um pedido só pode ser retirado por apenas um entregador. 

	ENTREGADOR/CLIENTE(Entrega): Um entregador pode entregar para nenhum ou vários clientes, e um cliente pode receber de um ou vários entregadores. Esse relacionamento possui o atributo código do pedido, além da data e hora.

	CLIENTE/ENDERECO(Possui): Um cliente possui apenas um endereço, e um endereço só pode estar relacionado a apenas um cliente.


### 6	MODELO LÓGICO<br>
        
![image](https://user-images.githubusercontent.com/91472785/204053819-1dbbe31a-dfd1-49bc-825c-b10f62bb0faa.png)

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
	    fk_PEDIDO_cod_pedido INTEGER,
	    qtd INTEGER
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
		   ('999.999.999-99', 'Pâmela Oliveira Santos'),
		   ('121.212.121-21','Romeu Silva Rodrigues'),
		   ('131.313.131-31','Joana Augusta Santana'),
		   ('141.414.141-41','Eduardo Olmo Santana'),
		   ('151.515.151-51','Paulo Cezar Rocha Furtado'),
		   ('161.616.161-61','Ilanna dos Reis Cardoso'),
		   ('171.717.171-71','Mariana Lopes de Gouvêa'),
		   ('181.818.181-81','Bruna Ramos Rocha'),
		   ('191.919.191-91','Daianny Maria Oliveira da Silva'),
		   ('232.323.232-32','Camila Fraga Egydio'),
		   ('242.424.242-42','Nycolly do Nascimento Mendes'),
		   ('252.525.252-52','Elisa Andrade de Jesus'),
		   ('262.626.262-62','Isabelly Balestrassi Nunes de Andrades'),
		   ('272.727.272-72','Kauã Mateus de Barros Terra'),
		   ('282.828.282-82','Davi Nunes Ribeiro'),
		   ('292.929.292-92','Lorena Toraes dos Santos'),
		   ('343.434.343-43','João Vitor Oliveira Scheidegger'),
		   ('353.535.353-53','Esther Moraes Nascimento'),
		   ('363.636.363-63','Raynan Araujo da Silva'),
		   ('373.737.373-73','Yasmin Santana Rodrigues'),
		   ('383.838.383-83','Sofia Andrade Nascimento'),
		   ('393.939.393-93','Jorge Pereira Alves'),
		   ('454.545.454-54','Arthur Dias Silveira'),
		   ('464.646.464-64','Guilherme Ferreira Mendes'),
		   ('474.747.474-74','Amanda Carvalho Castro');


	insert into ENTREGADOR
	values ('Matutino', 1500.00, '111.111.111-22'),
	       ('Vespertino', 1200.00, '222.222.222-33'),
	       ('Vespertino', 1360.00, '333.333.333-44'),
	       ('Matutino', 1450.00, '444.444.444-55'),
	       ('Noturno', 1600.00,'555.555.555-66'),
	       ('Matutino', 1520.00, '666.666.666-77'),
	       ('Vespertino', 1480.00, '777.777.777-88'),
	       ('Noturno', 1550.00, '888.888.888-99'),
	       ('Noturno', 1580.00, '999.999.999-11'),
		   ('Matutino',1500.00,'121.212.121-21'),
		   ('Matutino',1250.00,'131.313.131-31'),
		   ('Matutino',1320.00,'181.818.181-81'),
		   ('Vespertino',1300.00,'262.626.262-62'),
		   ('Vespertino',1400.00,'282.828.282-82'),
		   ('Noturno',1450.00,'393.939.393-93'),
		   ('Matutino',1570.00,'454.545.454-54'),
		   ('Noturno',1370.00,'464.646.464-64'),
		   ('Matutino',1230.00,'474.747.474-74'),
		   ('Vespertino',1444.00,'363.636.363-63'),
		   ('Vespertino',1333.00,'272.727.272-72'),
		   ('Noturno',1222.00,'383.838.383-83');
		   
	insert into CLIENTE_ENDERECO
	values ('111.111.111-11', 998885430, 'Rua', 'Castelo', 155, 'Jardim Limoeiro'),
	       ('222.222.222-22', 999532192, 'Avenida', 'Rui Barbosa', 23, 'Bairro de Fátima'),
		   ('333.333.333-33', 988221445, 'Rua', 'Limoeiro', 26, 'Barcelona'),
	       	   ('444.444.444-44', 992323555, 'Rodovia', 'do Rosário', 55, 'Nova Almeida'),
		   ('555.555.555-55', 992365539, 'Rua', 'Porto Alegre', 122, 'Nova Almeida'),
		   ('666.666.666-66', 998644222, 'Avenida', 'Carvalho', 15, 'Barcelona'),
		   ('777.777.777-77', 990843323, 'Rua', 'Lázaro Verde', 35, 'Jardim Limoeiro'),
		   ('888.888.888-88', 987657668, 'Rua', 'Monte Seco', 52, 'Bairro de Fátima'),
		   ('999.999.999-99', 994523223, 'Avenida', 'Pimenta', 165, 'Nova Almeida'),
		   ('141.414.141-41',991111111,'Rua','Pássaros',10,'Morada de Laranjeiras'),
		   ('151.515.151-51',992222222,'Rua','Louros',22,'Jacaraípe'),
		   ('161.616.161-61',993333333,'Avenida','Rosas',76,'Manguinhos'),
		   ('171.717.171-71',994444444,'Rua','Pétalas',19,'Porto Canoa'),
		   ('191.919.191-91',995555555,'Avenida','Tulipas',13,'Porto Canoa'),
		   ('232.323.232-32',996666666,'Avenida','Espinhos',09,'Morada de Laranjeiras'),
		   ('242.424.242-42',997777777,'Rua','Montanha Azul',03,'Manguinhos'),
		   ('252.525.252-52',998888888,'Avenida','Bosque Ensolarado',07,'Morada de Laranjeiras'),
		   ('292.929.292-92',999999999,'Rua','Vendaval',173,'Manguinhos'),
		   ('343.434.343-43',990000000,'Rua','Ipê Amarelo',100,'Jacaraípe'),
		   ('353.535.353-53',991010101,'Avenida','Ipê Branco',150,'Jacaraípe'),
		   ('373.737.373-73',992020202,'Avenida','Ipê Roxo',111,'Manguinhos');

	insert into RESTAURANTE
	values ('12.332.646/0002-25','McDonalds'),
	       ('16.225.938/0002-17','Burger King'),
	       ('08.427.254/0002-19','Subway'),
		   ('03.231.435/0002-11','Ricks Burguer'),
		   ('44.123.443/0002-01','Spoleto'),
		   ('23.124.554/0002-08','Giraffas'),
		   ('11.214.235/0002-99','Bobs'),
		   ('32.411.333/0002-02','China in Box'),
		   ('41.345.457/0002-34','Pedrinni Frutos do Mar'),
		   ('51.742.899/0002-09','Habibs'),
		   ('66.346.234/0001-03','Outback Steakhouse'),
		   ('87.332.111/0002-32','Taco Bell'),
		   ('10.120.102/0001-45','Pizza Hut'),
		   ('55.462.725/0002-79','KFC'),
		   ('79.402.967/0002-53','Starbucks'),
		   ('18.894.492/0002-39','Baskin-Robbins'),
		   ('91.794.386/0002-90','Dairy Queen'),
		   ('90.846.365/0002-17','Papa Johns'),
		   ('21.494.780/0001-86','Club Fit Life'),
		   ('57.282.078/0001-43','Cloud Foods');
		   		 
	insert into PRODUTO
	values (01,'Hambúrguer',15.00),
	       (02,'Pizza',40.00),
		   (03,'Água',2.00),
		   (04,'Suco',5.00),
		   (05,'Refrigerante',10.00),
		   (06,'Batata Frita',8.50),
		   (07,'Sushi',12.00),
		   (08,'Macarrão',5.00),
		   (09,'Frutos do Mar',20.00),
		   (10,'Sorvete',6.00),
		   (11,'Açaí',10.00),
		   (12,'Milkshake',5.00),
		   (13,'Esfirra',5.00),
		   (14,'Dumpling',4.00),
		   (15,'Bolo',7.00),
		   (16,'Chá',3.00),
		   (17,'Sopa',20.00),
		   (18,'Refrigerante sem açúcar',8.50),
		   (19,'Balde de Frango',35.00),
		   (20,'Taco',15.00);	 
 
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
		   (010, '08.427.254/0002-19', 130.00, '999.999.999-11', '777.777.777-77', '2022-07-26 17:09:19'),
		   (011,'32.411.333/0002-02',9.00,'121.212.121-21','252.525.252-52','2022-05-10 03:00:00'),
		   (012,'32.411.333/0002-02',20.00,'121.212.121-21','141.414.141-41','2022-11-03 15:30:00'),
		   (013,'10.120.102/0001-45',40.00,'181.818.181-81','252.525.252-52','2022-09-01 10:34:10'),
		   (014,'55.462.725/0002-79',35.00,'282.828.282-82','555.555.555-55','2022-03-30 13:33:33'),
		   (015,'79.402.967/0002-53',28.00,'393.939.393-93','141.414.141-41','2022-04-04 14:04:40'),
		   (016,'79.402.967/0002-53',19.00,'282.828.282-82','333.333.333-33','2022-05-06 06:07:08'),
		   (017,'91.794.386/0002-90',7.00,'393.939.393-93','373.737.373-73','2022-09-08 08:19:29'),
		   (018,'51.742.899/0002-09',15.00,'393.939.393-93','353.535.353-53','2022-09-08 18:20:45'),
		   (019,'87.332.111/0002-32',30.00,'474.747.474-74','373.737.373-73','2022-11-12 12:11:13'),
		   (020,'41.345.457/0002-34',22.00,'363.636.363-63','242.424.242-42','2022-02-22 22:23:24'),
		   (021,'11.214.235/0002-99',16.00,'383.838.383-83','333.333.333-33','2022-07-03 07:03:33');

	insert into RESTAURANTE_PRODUTO
	values ('12.332.646/0002-25',01),
	       ('12.332.646/0002-25',02),
	       ('12.332.646/0002-25',03),
	       ('12.332.646/0002-25',04),
	       ('12.332.646/0002-25',05),
	       ('12.332.646/0002-25',06),
	       ('16.225.938/0002-17',01),
	       ('16.225.938/0002-17',02),
	       ('16.225.938/0002-17',03),
	       ('16.225.938/0002-17',04),
	       ('16.225.938/0002-17',05),
	       ('16.225.938/0002-17',06),
	       ('08.427.254/0002-19',01),
	       ('08.427.254/0002-19',02),
	       ('08.427.254/0002-19',03),
	       ('08.427.254/0002-19',04),
	       ('08.427.254/0002-19',05),
	       ('08.427.254/0002-19',06),
		   ('03.231.435/0002-11',01),
		   ('03.231.435/0002-11',06),
		   ('03.231.435/0002-11',05),
		   ('44.123.443/0002-01',08),
		   ('44.123.443/0002-01',17),
		   ('44.123.443/0002-01',04),
		   ('23.124.554/0002-08',08),
		   ('23.124.554/0002-08',04),
		   ('11.214.235/0002-99',12),
		   ('11.214.235/0002-99',10),
		   ('11.214.235/0002-99',01),
		   ('32.411.333/0002-02',08),
		   ('32.411.333/0002-02',14),
		   ('32.411.333/0002-02',07),
		   ('41.345.457/0002-34',09),
		   ('41.345.457/0002-34',17),
		   ('51.742.899/0002-09',13),
		   ('51.742.899/0002-09',18),
		   ('66.346.234/0001-03',17),
		   ('66.346.234/0001-03',10),
		   ('66.346.234/0001-03',01),
		   ('87.332.111/0002-32',20),
		   ('87.332.111/0002-32',18),
		   ('10.120.102/0001-45',02),
		   ('55.462.725/0002-79',19),
		   ('79.402.967/0002-53',12),
		   ('79.402.967/0002-53',16),
		   ('18.894.492/0002-39',10),
		   ('91.794.386/0002-90',15),
		   ('90.846.365/0002-17',02),
		   ('21.494.780/0001-86',11),
		   ('21.494.780/0001-86',18),
		   ('57.282.078/0001-43',17);

	insert into PRODUTO_PEDIDO
	values (01, 001,1),
	     (04, 001,1),
	     (06, 001,1),
	     (02, 002,1),
	     (05, 002,1),
	     (01, 003,1),
	     (03, 004,1),
	     (06, 004,1),
	     (05, 005,1),
	     (06, 005,1),
	     (01, 006,1),
	     (02, 006,1),
	     (05, 006,1),
	     (06, 006,1),
	     (05, 007,1),
	     (01, 008,1),
	     (03, 008,1),
	     (05, 008,1),
	     (02, 009,2),
	     (05, 009,2),
	     (02, 010,2),
		 (08,011,1),
		 (14,011,1),
		 (17,012,1),
		 (02,013,1),
		 (19,014,1),
		 (05,015,1),
		 (12,015,3),
		 (16,015,1),
		 (16,016,3),
		 (12,016,1),
		 (04,016,1),
		 (15,017,1),
		 (13,018,3),
		 (20,019,2),
		 (03,020,1),
		 (09,020,1),
		 (12,021,2),
		 (10,021,1);


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
	     ('999.999.999-11', '777.777.777-77',010, '2022-07-26 18:06:39'),
		 ('121.212.121-21','252.525.252-52',011,'2022-05-10 05:00:00'),
		 ('121.212.121-21','141.414.141-41',012,'2022-11-03 17:30:00'),
		 ('181.818.181-81','252.525.252-52',013,'2022-09-01 11:55:00'),
		 ('282.828.282-82','555.555.555-55',014'2022-03-30 11:33:33'),
		 ('393.939.393-93','141.414.141-41',015,'2022-04-04 16:04:40'),
		 ('282.828.282-82','333.333.333-33',016,'2022-05-06 07:30:30'),
		 ('393.939.393-93','373.737.373-73',017,'2022-09-08 09:19:29'),
		 ('393.939.393-93','353.535.353-53',018,'2022-09-08 19:40:45'),
		 ('474.747.474-74','373.737.373-73',019,'2022-11-12 13:11:13'),
		 ('363.636.363-63','242.424.242-42',020,'2022-02-22 23:30:00'),
		 ('383.838.383-83','333.333.333-33',021,'2022-07-03 08:20:45');
	
	
	


### 9	TABELAS E PRINCIPAIS CONSULTAS<br>
    https://colab.research.google.com/drive/16b3oBZUtT7vv-7eI0l2TMzgiczN3K4W_?usp=sharing
    
    
#### 9.1	CONSULTAS DAS TABELAS COM TODOS OS DADOS INSERIDOS (Todas) <br>
![image](https://user-images.githubusercontent.com/92343021/204108916-657c90b9-e9ea-45a5-b786-f6e15d56d823.png)

![image](https://user-images.githubusercontent.com/92343021/204108926-205d2cc8-ae7e-47c9-8305-b0bd1d25e54e.png)<br>
![image](https://user-images.githubusercontent.com/92343021/204108976-bee3e263-9bd6-45a8-8501-c317b8ecdced.png)

![image](https://user-images.githubusercontent.com/92343021/204109029-e1ff809e-f8b1-4ed4-bfe1-c1aaa438f151.png)
	
![image](https://user-images.githubusercontent.com/92343021/204109045-117547bc-8aae-4675-a24e-073983706073.png)<br>
![image](https://user-images.githubusercontent.com/92343021/204109056-8d97689b-da45-4993-8181-d20bcb75950a.png)

![image](https://user-images.githubusercontent.com/92343021/204109062-2f24e779-a40c-4e01-96e3-19b474879d55.png)

![image](https://user-images.githubusercontent.com/92343021/204109068-efb3712a-d92c-474a-9e3b-4bb3711a5b9c.png)

![image](https://user-images.githubusercontent.com/92343021/204109085-97f07c5b-ddd2-4f8b-bc12-468c38cfd235.png)

![image](https://user-images.githubusercontent.com/92343021/204109141-a5b4c960-bf92-4a04-a319-f49ddac314d6.png)

![image](https://user-images.githubusercontent.com/92343021/204109160-ce8d064f-1bc5-40fe-a024-95dc0ceb096b.png)<br>
![image](https://user-images.githubusercontent.com/92343021/204109172-e263bd8d-279a-4d42-b57c-0dabcdc094b4.png)

	
># Marco de Entrega 01: Do item 1 até o item 9.1<br>

#### 9.2	CONSULTAS DAS TABELAS COM FILTROS WHERE (Mínimo 4)
select * from Pedido where preco_total > 30;<br>
![image](https://user-images.githubusercontent.com/92343021/204094028-576f1410-c522-464d-b90f-88b8c4684fb8.png)


select  FK_PESSOA_cpf ,tipo_logradouro,telefone from Cliente_Endereco where telefone <> '987657668';<br>
![image](https://user-images.githubusercontent.com/92343021/204094456-c1b484b9-0b3f-49b5-ac7e-2e947edb616c.png)


select *from Entregador where turno <> 'Matutino';<br>
![image](https://user-images.githubusercontent.com/92343021/204094090-e34c3324-4a3f-4625-95b7-b9d5b4fa2719.png)


select *from Produto where preco > 10.00 ;<br>
![image](https://user-images.githubusercontent.com/92343021/204094112-3e3b491b-12e6-4a5a-abd5-73e253fe785b.png)


#### 9.3	CONSULTAS QUE USAM OPERADORES LÓGICOS, ARITMÉTICOS E TABELAS OU CAMPOS RENOMEADOS (Mínimo 11)
    a) Criar 5 consultas que envolvam os operadores lógicos AND, OR e Not
    
select *from Produto where preco > 10.00 and preco <30.00 ;<br>
![image](https://user-images.githubusercontent.com/92343021/204094219-3ac12668-0cf0-4322-8f4c-5db65c035bdc.png)

select *from Pedido where(data_hora <>'2022-07-26 18:06:39'and data_hora='2022-09-12 12:20:50') or FK_ENTREGADOR_FK_PESSOA_cpf<>'444.444.444-55';<br>
![image](https://user-images.githubusercontent.com/92343021/204094333-630ba929-4066-4eed-a77f-62ed95259548.png)

select *from Entregador where(turno<>'Noturno'or turno='Matutino') and salario >=1200.00;<br>
![image](https://user-images.githubusercontent.com/92343021/204094505-2d19f3a4-c51b-4159-9ff3-428c3f488e62.png)

select *from Entregador where(turno<>'Noturno'or turno='Vespertino') and salario >=1300.00;<br>
![image](https://user-images.githubusercontent.com/92343021/204094541-a4d5206a-43a6-46da-a915-6ee70e5e7f02.png)

select *from Pedido where preco_total < 20.00 or cod_pedido<>005;<br>
![image](https://user-images.githubusercontent.com/92343021/204094593-71b43ef9-1767-4f22-a44e-a58c80079c59.png)

select *from Cliente_Endereco where (tipo_logradouro<>'rua' or bairro<>'Nova Almeida')and not nome_logradouro='Rua do Rosário';<br>
![image](https://user-images.githubusercontent.com/92343021/204094654-bc36526d-863c-4f82-895c-a65c44358a44.png)

select *from Pedido where not preco_total =50.00 or FK_ENTREGADOR_FK_PESSOA_cpf<>'222.222.222-33';<br>
![image](https://user-images.githubusercontent.com/92343021/204094694-7de60b04-27d7-44dd-b6d8-91a525642eb4.png)

	
	b) Criar no mínimo 3 consultas com operadores aritméticos 
    
PRIMEIRO:
select fk_pessoa_cpf,salario, salario * 12 as salario_anual from entregador;
![image](https://user-images.githubusercontent.com/92343021/204095924-3e3f3518-2ac3-4b90-989d-416da43cb998.png)

SEGUNDO:
select fk_pessoa_cpf, salario, salario + salario * 0.1 as salario_com_bonus from entregador;<br>
![image](https://user-images.githubusercontent.com/92343021/204095996-9b9f794f-93b0-446b-80db-050286a333fc.png)

TERCEIRO:
select *, preco + preco * 0.2 as preco_inflacao from produto;
![image](https://user-images.githubusercontent.com/92343021/204096067-f58f13c5-8f5b-49d2-965e-4a27d41a47b6.png)


	c) Criar no mínimo 3 consultas com operação de renomear nomes de campos ou tabelas
PRIMEIRO:
select fk_PRODUTO_cod_produto as Codigo_Produto, fk_PEDIDO_cod_pedido as Codigo_Pedido from PRODUTO_PEDIDO where fk_PRODUTO_cod_produto > 3 and fk_PEDIDO_cod_pedido < 6;

![image](https://user-images.githubusercontent.com/92343021/204096474-829e9ac9-cb87-434d-bfce-d0d7a7b5755a.png)

SEGUNDO:
select fk_ENTREGADOR_FK_PESSOA_cpf as cpf_entregador, FK_PEDIDO_cod_pedido as cod_pedido from ENTREGADOR_CLIENTE where FK_PEDIDO_cod_pedido > 5; 

![image](https://user-images.githubusercontent.com/92343021/204096515-7be5f22d-5937-42af-b818-6cff79b12c8b.png)

TERCEIRO:
select cod_pedido,FK_RESTAURANTE_cnpj as cnpj_Restaurante,FK_ENTREGADOR_FK_PESSOA_cpf as cpf_entregador,FK_CLIENTE_ENDERECO_FK_PESSOA_cpf as cpf_Cliente from PEDIDO where cod_pedido > 5;

![image](https://user-images.githubusercontent.com/92343021/204096544-b833dc5e-a965-47c3-9001-dbe0b0d6ff4b.png)




#### 9.4	CONSULTAS QUE USAM OPERADORES LIKE E DATAS (Mínimo 12) <br>
    a) Criar outras 5 consultas que envolvam like ou ilike
    
select * from produto where nome like '%a';<br>
![image](https://user-images.githubusercontent.com/92343021/204099474-3a58e6af-ac8c-4e86-9a09-66f6c3872d80.png)

select * from cliente_endereco where bairro like 'B%';<br>
![image](https://user-images.githubusercontent.com/92343021/204099634-97a34cc7-6a81-4af9-bb11-b20b37d331d4.png)

select * from entregador where turno like 'V%';<br>
![image](https://user-images.githubusercontent.com/92343021/204099657-838b3625-ba52-4917-92e0-a88e9428b869.png)

select * from restaurante where nome like '%u%';<br>
![image](https://user-images.githubusercontent.com/92343021/204099693-5e71f341-c938-4b35-af95-9838ec3ab4d9.png)

select * from pessoa where nome like 'P%' or nome like 'A%';<br>
![image](https://user-images.githubusercontent.com/92343021/204099725-4ac019e7-49fb-48f9-b598-56381ff8a182.png)
    
    b) Criar uma consulta para cada tipo de função data apresentada.

select *, current_date - data_hora as tempo from pedido;<br>
![image](https://user-images.githubusercontent.com/92343021/204100028-54e128e0-83ab-4216-9f86-4a0d4a7c9588.png)

select *, now() - data_hora as tempo from entregador_cliente;<br>
![image](https://user-images.githubusercontent.com/92343021/204100059-c22a3dc1-8d7b-4b0e-9086-1fc2365f10e5.png)

select *, age(current_date,data_hora) as tempo from pedido;<br>
![image](https://user-images.githubusercontent.com/92343021/204100074-ce8e4bd6-2585-4452-8090-cd9c52c604ba.png)

select *, date_part('month',age(current_date,data_hora)) as "tempo em meses" from entregador_cliente;<br>
![image](https://user-images.githubusercontent.com/92343021/204100097-b36ad806-9c10-442c-972e-17e70df8df28.png)

select * from entregador_cliente where (extract(day from current_date-data_hora) < 20);<br>
![image](https://user-images.githubusercontent.com/92343021/204100118-fe330cd3-87e7-4704-ac31-3ca7104d14eb.png)

select * from pedido where extract(hour from data_hora) < 12;<br>
![image](https://user-images.githubusercontent.com/92343021/204100152-7cb11ed3-5d1a-48c6-8290-c03581b52ba1.png)

select * from entregador_cliente where extract(hour from data_hora) < 12;<br>
![image](https://user-images.githubusercontent.com/92343021/204100161-7734be3c-369f-4ee5-9669-4b31dc275e6d.png)



#### 9.5	INSTRUÇÕES APLICANDO ATUALIZAÇÃO E EXCLUSÃO DE DADOS (Mínimo 6)<br>
    a) Criar minimo 3 de exclusão
DELETE FROM Entregador_cliente 
where data_hora='2022-09-12 12:50:00';
select * from Entregador_cliente;<br>
![image](https://user-images.githubusercontent.com/92343021/204109789-a75a631d-8c84-4a0d-b7dc-0b17b8375e5c.png)

DELETE FROM Pessoa where nome = 'Jorge Pereira Alves' ;
select * from Pessoa<br>
![image](https://user-images.githubusercontent.com/92343021/204109860-aa70519f-5a65-4b7d-a337-e4388ba1ce9f.png)

DELETE FROM Cliente_Endereco where  tipo_logradouro='Avenida' or bairro = 'Porto Canoa' ;
select * from Cliente_Endereco<br>
![image](https://user-images.githubusercontent.com/92343021/204109843-4fd0a0c0-3922-4061-8503-374cfb853078.png)


	b) Criar minimo 3 de atualização

update Pessoa set nome='Fernanda Fagundes' where cpf='555.555.555-66';
select * from Pessoa;<br>
![image](https://user-images.githubusercontent.com/92343021/204107950-86f56bb4-572a-4773-99d6-2dbc83a8c36a.png)

update Produto set nome='Tortilhas' where cod_produto='06';
select * from Produto;<br>
![image](https://user-images.githubusercontent.com/92343021/204108031-19ab3637-0fa9-4c22-9113-edf1e8f189f4.png)

update CLIENTE_ENDERECO set tipo_logradouro='rua' where Bairro='Barcelona';
select * from CLIENTE_ENDERECO;<br>
![image](https://user-images.githubusercontent.com/92343021/204108052-f260817a-0eb1-46d0-95e6-3cdb1a87a3ab.png)

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

![image](https://user-images.githubusercontent.com/92343021/204110405-e4ce906a-c595-4dc7-b07f-4378b8b3d989.png)

    b) Outras junções que o grupo considere como sendo as de principal importância para o trabalho
select r.nome as restaurante,p.nome as produto, p.preco<br>
from restaurante as r<br>
inner join restaurante_produto as rp<br>
on(rp.fk_restaurante_cnpj = r.cnpj)<br>
inner join produto as p<br>
on(rp.fk_produto_cod_produto = p.cod_produto)<br>
order by p.preco<br>
![image](https://user-images.githubusercontent.com/91472785/204110596-47840bf9-a760-46a6-b22e-c431920377dd.png)


select fk_pessoa_cpf,nome<br>
from entregador as e<br>
inner join pessoa as p<br>
on(p.cpf = e.fk_pessoa_cpf)<br>
order by nome<br>
![image](https://user-images.githubusercontent.com/91472785/204110605-d985be30-64ae-46ea-b7d8-60d129310ef9.png)

select nome,cod_pedido<br>
from entregador as e<br>
inner join pessoa<br>
on(pessoa.cpf = e.fk_pessoa_cpf)<br>
inner join pedido as p<br>
on(e.fk_pessoa_cpf = p.fk_entregador_fk_pessoa_cpf)<br>
order by cod_pedido desc<br>
![image](https://user-images.githubusercontent.com/91472785/204110616-ce4c1914-eb0f-48d4-86ef-7a8a2f2e21f9.png)

select fk_pessoa_cpf,nome<br>
from cliente_endereco as ce<br>
inner join pessoa<br>
on(pessoa.cpf = ce.fk_pessoa_cpf)<br>
order by nome desc<br>
![image](https://user-images.githubusercontent.com/91472785/204110632-7b2b916a-4dec-45aa-b435-447d19ed3ba1.png)

select nome,cod_pedido<br>
from cliente_endereco as ce<br>
inner join pessoa<br>
on(ce.fk_pessoa_cpf = pessoa.cpf)<br>
inner join pedido as p<br>
on(p.fk_cliente_endereco_fk_pessoa_cpf = ce.fk_pessoa_cpf)<br>
order by cod_pedido desc<br>
![image](https://user-images.githubusercontent.com/91472785/204110643-0dc58f3b-e66e-4df4-9d59-45347fddcc10.png)



#### 9.7	CONSULTAS COM GROUP BY E FUNÇÕES DE AGRUPAMENTO (Mínimo 6)<br>
    a) Criar minimo 2 envolvendo algum tipo de junção
select pessoa.nome, count(pedido.cod_pedido) as qtd_entregas<br>
from entregador<br>
inner join pessoa<br>
on (pessoa.cpf = entregador.fk_pessoa_cpf)<br>
inner join pedido<br>
on (entregador.fk_pessoa_cpf = pedido.fk_entregador_fk_pessoa_cpf)<br>
group by pessoa.nome;<br>
![image](https://user-images.githubusercontent.com/92343021/204104755-3e17c59e-b988-4c7f-a327-6c841cd03855.png)

select restaurante.nome, count(pedido.cod_pedido) as qtd_pedidos, sum(pedido.preco_total) as valor_total<br>
from restaurante<br>
inner join pedido<br>
on (restaurante.cnpj = pedido.fk_restaurante_cnpj)<br>
group by restaurante.nome;<br>
![image](https://user-images.githubusercontent.com/92343021/204104806-c7ec82d9-5d69-4bef-bef2-507c0857ff00.png)

select pessoa.nome, sum(pedido.preco_total) as valor_total<br>
from pessoa<br>
inner join cliente_endereco<br>
on (pessoa.cpf = cliente_endereco.fk_pessoa_cpf)<br>
inner join pedido<br>
on (cliente_endereco.fk_pessoa_cpf = pedido.fk_cliente_endereco_fk_pessoa_cpf)<br>
group by pessoa.nome;<br>
![image](https://user-images.githubusercontent.com/92343021/204104853-236117dd-7b1e-4c8f-91e9-2d5f6201c016.png)

select cliente_endereco.bairro,<br>
count(cliente_endereco.fk_pessoa_cpf) as qtd_clientes<br>
from cliente_endereco<br>
group by bairro;<br>
![image](https://user-images.githubusercontent.com/92343021/204104877-bcb8a501-9bd1-4fb2-9f36-cf6b5003c7c6.png)

select entregador.turno,<br>
count(entregador.fk_pessoa_cpf) as qtd_entregadores,<br> 
sum(entregador.salario) as soma_salario<br>
from entregador<br>
group by turno;<br>
![image](https://user-images.githubusercontent.com/92343021/204104920-ebf3f60d-4ae7-4213-99fd-1288973c7525.png)

select produto_pedido.fk_pedido_cod_pedido,<br> 
count(produto.cod_produto) as qtd_produtos<br>
from produto_pedido<br>
inner join produto<br>
on (produto.cod_produto = produto_pedido.fk_produto_cod_produto)<br>
group by produto_pedido.fk_pedido_cod_pedido<br>
order by produto_pedido.fk_pedido_cod_pedido;<br>

![image](https://user-images.githubusercontent.com/92343021/204104962-77263aa5-61dd-4aea-9b48-6e219e29b241.png)

#### 9.8	CONSULTAS COM LEFT, RIGHT E FULL JOIN (Mínimo 4)<br>
    a) Criar minimo 1 de cada tipo
select pessoa.cpf,<br>
pessoa.nome,<br>
entregador.salario,<br>
entregador.turno<br>
from entregador<br>
right outer join pessoa<br>
on(pessoa.cpf = entregador.fk_pessoa_cpf);<br>	

![image](https://user-images.githubusercontent.com/92343021/204105035-87da4d0a-b8eb-4817-9eb3-0ffc9f442cbf.png)

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

![image](https://user-images.githubusercontent.com/92343021/204105248-e807e340-2e9d-482a-8210-f58011f33595.png)

select * <br> 
from entregador<br> 
full outer join entregador_cliente<br> 
on(entregador.fk_pessoa_cpf = entregador_cliente.fk_entregador_fk_pessoa_cpf);<br> 

![image](https://user-images.githubusercontent.com/92343021/201439000-a538a7f1-468f-4358-9238-499562796d17.png)

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

![image](https://user-images.githubusercontent.com/92343021/204107267-4d10bcdd-0af8-4d05-ad64-899af9d28718.png)


#### 9.9	CONSULTAS COM SELF JOIN E VIEW (Mínimo 6)<br>
	a) Uma junção que envolva Self Join (caso não ocorra na base justificar e substituir por uma view)
As tabelas não possuem informações suficientes para que seja feito um auto relacionamento. Não existem atributos relacionáveis dentro de uma mesma tabela no nosso banco de dados.

create view contato_cliente as<br>
select pessoa.cpf,pessoa.nome,<br>
cliente_endereco.telefone<br>
from pessoa<br>
inner join cliente_endereco<br>
on(pessoa.cpf = cliente_endereco.fk_pessoa_cpf)<br>

![image](https://user-images.githubusercontent.com/92343021/204107384-df130128-03e6-4973-ba06-6f807c07da02.png)

	b) Outras junções com views que o grupo considere como sendo de relevante importância para o trabalho

create view salario_anual_entregador as<br>
select pessoa.cpf,pessoa.nome,<br> 
(entregador.salario * 12) as salario_anual<br>
from pessoa<br>
inner join entregador<br>
on(pessoa.cpf = entregador.fk_pessoa_cpf);<br>

![image](https://user-images.githubusercontent.com/92343021/204107413-3396fa36-1d22-4a39-9e03-00ab561a7406.png)

create view cpf_e_nome_entregador as<br>
select pessoa.cpf,pessoa.nome<br>
from pessoa<br>
inner join entregador<br>
on(pessoa.cpf = entregador.fk_pessoa_cpf);<br>

![image](https://user-images.githubusercontent.com/92343021/204107439-9918f1b9-21e3-4f3e-9321-1b91ee1a68c0.png)

create view cpf_e_nome_cliente as<br>
select pessoa.cpf,pessoa.nome<br>
from pessoa<br>
inner join cliente_endereco<br>
on(pessoa.cpf = cliente_endereco.fk_pessoa_cpf)<br>

![image](https://user-images.githubusercontent.com/92343021/204107475-786ebbb5-66b1-467e-b6dd-58b080c91752.png)

create view cliente_pagamento_pedido as<br>
select pessoa.cpf, pessoa.nome, sum(pedido.preco_total) as pagamento_total<br>
from pedido<br>
inner join pessoa<br>
on(pedido.fk_cliente_endereco_fk_pessoa_cpf = pessoa.cpf)<br>
group by pessoa.cpf, pessoa.nome;<br>

![image](https://user-images.githubusercontent.com/92343021/204107564-c8ba597b-bcb8-410d-ae82-f2480287eb52.png)

create view restaurante_produto_vendas as<br>
select restaurante.cnpj as restaurante_cnpj,<br>
restaurante.nome as restaurante_nome,<br>
sum(pedido.preco_total) as valor_total_vendas,<br> 
count(produto_pedido.fk_produto_cod_produto) as qtd_produtos<br>
from pedido<br>
inner join restaurante<br>
on(pedido.fk_restaurante_cnpj = restaurante.cnpj)<br>
inner join produto_pedido<br>
on(produto_pedido.fk_pedido_cod_pedido = pedido.cod_pedido)<br>
group by restaurante.cnpj;<br>

![image](https://user-images.githubusercontent.com/92343021/204107604-eed664da-8429-44d5-bd2e-ad80d35904e3.png)

#### 9.10	SUBCONSULTAS (Mínimo 4)<br>

select * from entregador
where turno in('Matutino','Vespertino');<br>
![image](https://user-images.githubusercontent.com/92343021/204107681-e084b116-2748-4e89-a28a-4f65301bfca4.png)

select * 
from cliente_endereco
where bairro not in('Nova Almeida','Barcelona');<br>
![image](https://user-images.githubusercontent.com/92343021/204107695-68325229-747e-4a30-8724-3766cdfe1dc1.png)

     a) Criar minimo 1 envolvendo GROUP BY

select nome,count(cod_produto)<br>
from produto<br>
inner join produto_pedido as pp<br>
on(produto.cod_produto = pp.fk_produto_cod_produto)<br>
where nome in('Pizza','Refrigerante')<br>
group by nome<br>
order by count(cod_produto) desc;<br>
![image](https://user-images.githubusercontent.com/92343021/204107744-e5258cd7-c8f6-4ead-bb44-5b4d1311ff40.png)

     
     b) Criar minimo 1 envolvendo algum tipo de junção
     
select cod_pedido,nome from produto<br>
inner join produto_pedido as pp<br>
on(pp.fk_produto_cod_produto = produto.cod_produto)<br>
inner join pedido<br>
on(pp.fk_pedido_cod_pedido = pedido.cod_pedido)<br>
where nome in('Hambúrguer','Batata Frita');<br>
![image](https://user-images.githubusercontent.com/92343021/204107769-bf81b2f6-27a1-466b-9ec1-a4d19da80a51.png)



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


