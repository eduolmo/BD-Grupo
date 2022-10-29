# TRABALHO 01:  Título do Trabalho
Trabalho desenvolvido durante a disciplina de Banco de dados

# Sumário

### 1. COMPONENTES<br>
Integrantes do grupo<br>
Eduardo Olmo Santana:eduardo.olmosantana@gmail.com<br>
Nycolly do Nascimento Mendes:nycollydonascimentomendes@gmail.com<br>
Paulo Cezar Rocha Futado:paulocezarrf@hotmail.com<br>
Elisa Andrade de Jesus:moon.anonimos.es@gmail.com<br>

### 2.INTRODUÇÃO E MOTIVAÇÃO<br>

> A empresa "AiQueFome!" busca alimentar seus clientes não so com comida, mas com cultura. É uma empresa de delivery de comida que busca levar aos seus clientes novas experiencias em forma de pratos caracteristicos de diversas nações, para que eles possam sentir um gostinhos das outras culturas dentro do conforto de seu proprio lar. Para alcançar seu objetivo a empresa está querendo criar um aplicativo que irá permitir seus clientes pedirem suas refeições de forma fácil e prática. Para gerenciar os pedidos, o aplicativo irá armazenar as informações relativas ao Cliente, ao Pedido, ao Restaurante, ao Entregador e a Refeição. 
 

### 3.MINI-MUNDO<br>

>O aplicativo "AiQueFome!" foi feito para facilitar e otimizar os serviços de delivery de restaurantes e possibilitar que o clientes tenham acesso a diversos produtos alimentícios em um só lugar. Dessa forma o "AiQueFome!" criou um sistema que funciona da seguinte forma: Restaurante produz produto, o qual compõe o pedido, que é retirado pelo Entregador para ser entregue ao cliente, que possui um endereço. Do restaurante será armazenado o CNPJ (atributo identificador), e nome. Do produto armazenaremos código do produto(identificador), nome e preço. Do pedido armazenaremos código do pedido, seu atributo identificador, e o seu preço total. Do entregador armazenaremos cpf, que é seu identificador, turno, salário e nome. Do cliente armazenaremos: cpf(identificador), nome e telefone. Do endereço armazenaremos as informações de rua, número e bairro. Da relação de entrega armazenaremos a data e hora.<br>
Um restaurante pode produzir um ou vários produtos, enquanto um produto pode ser produzido por um ou vários restaurantes. Um produto pode compor um ou vários pedidos, assim como um pedido pode ser composto por um ou vários produtos. Um cliente pode fazer um ou vários pedidos, mas um pedido só pode ser feito por apenas um único cliente. Um entregador pode retirar um ou vários pedidos, porém um pedido só pode ser retirado por apenas um entregador. Um entregador pode entregar para um ou vários clientes, e um cliente pode receber de um ou vários entregadores. Por fim, um  cliente possui apenas um endereço, e um endereço só pode estar relacionado a apenas um cliente.

### 4.PERGUNTAS A SEREM RESPONDIDAS E TABELA DE DADOS<br>
#### 4.1 QUAIS PERGUNTAS PODEM SER RESPONDIDAS COM O SISTEMA PROPOSTO?
    
> A Empresa "AiQueFome!" precisa inicialmente dos seguintes relatórios:
* Relatório que mostre o nome de cada entregador e a quantidade de entregas feitas por ele.
* Relatório que apresente o nome do restaurante, a quantidade de produtos vendidos por ele e o valor total desses produtos.
* Relatório que mostre a quantidade das entregas feitas após certo horário.
* Relatório que mostre o nome de cada cliente e o valor total dos pedidos que esse cliente pediu.
* Relatório que mostre o nome do bairro e a quantidade de clientes que residem nele, agrupando pelo bairro.

 ### 5.MODELO CONCEITUAL<br>
    
![image](https://user-images.githubusercontent.com/91472785/198836936-49d3cccc-66fb-4ca6-8d36-9e037e484eac.png)
    
#### 5.1 Validação do Modelo Conceitual
    Grupo 1: Ilanna,Mariana,Bruna,Daianny
    

#### 5.2 Descrição dos dados 

    RESTAURANTE: Tabela que armazena os dados de cada restaurante. 
    Atributos: CNPJ(identificador) e nome.
    
    PRODUTO: Tabela que armazena as informações dos produtos.
    Atributos: código do produto(identificador), nome e preço.
    
    PEDIDO: Tabela que armazena as informações referentes dos pedidos.
    Atributos: código do pedido(identificador) e preço total.
    
    ENTREGADOR: Tabela que armazena os dados do entregador.
    Atributos: CPF(identificador), nome, salário, e turno.
    
    CLIENTE: Tabela que armazena os dados dos clientes.
    Atributos: CPF(identificador), nome e telefone.
    
    ENDERECO: Tabela que armazena o endereço dos clientes.
    Atributos: número, rua e bairro.
    
    RESTAURANTE/PRODUTO(Produz): Um restaurante pode produzir um ou vários produtos, enquanto um produto pode ser produzido por um ou vários restaurantes.
    
    PRODUTO/PEDIDO(Compoe): Um produto pode compor um ou vários pedidos, assim como um pedido pode ser composto por um ou vários produtos. 
    
    PEDIDO/CLIENTE(Feito): Um cliente pode fazer um ou vários pedidos, ao mesmo tempo que um pedido pode ser feito por um ou vários clientes. 
    
    PEDIDO/ENTREGADOR(Retira): Um entregador pode retirar um ou vários pedidos, porém um pedido só pode ser retirado por apenas um entregador. 
    
    ENTREGADOR/CLIENTE(Entrega): Um entregador pode entregar para um ou vários clientes, e um cliente pode receber de um ou vários entregadores. Esse relacionamento possui o atributo data e hora.
    
    CLIENTE/ENDERECO(Possui): Um cliente possui apenas um endereço, e um endereço só pode estar relacionado a apenas um cliente.
    

### 6	MODELO LÓGICO<br>
        
![image](https://user-images.githubusercontent.com/91472785/198837789-d64e5826-a901-40cd-94b1-2a75dec99db6.png)

### 7	MODELO FÍSICO<br>
        
    drop table if exists CLIENTE_ENDERECO,PRODUTO,RESTAURANTE,ENTREGADOR,PEDIDO,Produz,Compoe,Entrega,Feito;

    CREATE TABLE CLIENTE_ENDERECO (
            cpf VARCHAR(100) PRIMARY KEY,
            nome VARCHAR(100),
            telefone INTEGER,
            rua VARCHAR(100),
            numero INTEGER,
            bairro VARCHAR(100)
        );

    CREATE TABLE PRODUTO (
        cod_produto INTEGER PRIMARY KEY,
        nome VARCHAR(100),
        preco FLOAT
    );

    CREATE TABLE RESTAURANTE (
        cnpj VARCHAR(100) PRIMARY KEY,
        nome VARCHAR(100)
    );

    CREATE TABLE ENTREGADOR (
        cpf VARCHAR(100) PRIMARY KEY,
        nome VARCHAR(100),
        turno VARCHAR(100),
        salario FLOAT
    );

    CREATE TABLE PEDIDO (
        cod_pedido INTEGER PRIMARY KEY,
        preco_total FLOAT,
        FK_ENTREGADOR_cpf VARCHAR(100)
    );

    CREATE TABLE Produz (
        fk_RESTAURANTE_cnpj VARCHAR(100),
        fk_PRODUTO_cod_produto INTEGER
    );

    CREATE TABLE Compoe (
        fk_PRODUTO_cod_produto INTEGER,
        fk_PEDIDO_cod_pedido INTEGER
    );

    CREATE TABLE Entrega (
        fk_ENTREGADOR_cpf VARCHAR(100),
        fk_CLIENTE_ENDERECO_cpf VARCHAR(100),
        data_hora TIMESTAMP
    );

    CREATE TABLE Feito (
        fk_PEDIDO_cod_pedido INTEGER,
        fk_CLIENTE_ENDERECO_cpf VARCHAR(100)
    );

    ALTER TABLE PEDIDO ADD CONSTRAINT FK_PEDIDO_2
        FOREIGN KEY (FK_ENTREGADOR_cpf)
        REFERENCES ENTREGADOR (cpf)
        ON DELETE RESTRICT;

    ALTER TABLE Produz ADD CONSTRAINT FK_Produz_1
        FOREIGN KEY (fk_RESTAURANTE_cnpj)
        REFERENCES RESTAURANTE (cnpj)
        ON DELETE RESTRICT;

    ALTER TABLE Produz ADD CONSTRAINT FK_Produz_2
        FOREIGN KEY (fk_PRODUTO_cod_produto)
        REFERENCES PRODUTO (cod_produto)
        ON DELETE RESTRICT;

    ALTER TABLE Compoe ADD CONSTRAINT FK_Compoe_1
        FOREIGN KEY (fk_PRODUTO_cod_produto)
        REFERENCES PRODUTO (cod_produto)
        ON DELETE RESTRICT;

    ALTER TABLE Compoe ADD CONSTRAINT FK_Compoe_2
        FOREIGN KEY (fk_PEDIDO_cod_pedido)
        REFERENCES PEDIDO (cod_pedido)
        ON DELETE RESTRICT;

    ALTER TABLE Entrega ADD CONSTRAINT FK_Entrega_1
        FOREIGN KEY (fk_ENTREGADOR_cpf)
        REFERENCES ENTREGADOR (cpf)
        ON DELETE RESTRICT;

    ALTER TABLE Entrega ADD CONSTRAINT FK_Entrega_2
        FOREIGN KEY (fk_CLIENTE_ENDERECO_cpf)
        REFERENCES CLIENTE_ENDERECO (cpf)
        ON DELETE RESTRICT;

    ALTER TABLE Feito ADD CONSTRAINT FK_Feito_1
        FOREIGN KEY (fk_PEDIDO_cod_pedido)
        REFERENCES PEDIDO (cod_pedido)
        ON DELETE RESTRICT;

    ALTER TABLE Feito ADD CONSTRAINT FK_Feito_2
        FOREIGN KEY (fk_CLIENTE_ENDERECO_cpf)
        REFERENCES CLIENTE_ENDERECO (cpf)
        ON DELETE RESTRICT;



       
### 8	INSERT APLICADO NAS TABELAS DO BANCO DE DADOS<br>
        a) inclusão das instruções de inserção dos dados nas tabelas criadas pelo script de modelo físico
        (Drop para exclusão de tabelas + create definição de para tabelas e estruturas de dados + insert para dados a serem inseridos)
        b) Criar um novo banco de dados para testar a restauracao 
        (em caso de falha na restauração o grupo não pontuará neste quesito)
        c) formato .SQL


### 9	TABELAS E PRINCIPAIS CONSULTAS<br>
    OBS: Usar o colab para apresentar os resultados que devem incluir as instruções SQL + resultados em forma de tabela.<br>
#### 9.1	CONSULTAS DAS TABELAS COM TODOS OS DADOS INSERIDOS (Todas) <br>

># Marco de Entrega 01: Do item 1 até o item 9.1<br>

#### 9.2	CONSULTAS DAS TABELAS COM FILTROS WHERE (Mínimo 4)<br>
#### 9.3	CONSULTAS QUE USAM OPERADORES LÓGICOS, ARITMÉTICOS E TABELAS OU CAMPOS RENOMEADOS (Mínimo 11)
    a) Criar 5 consultas que envolvam os operadores lógicos AND, OR e Not
    b) Criar no mínimo 3 consultas com operadores aritméticos 
    c) Criar no mínimo 3 consultas com operação de renomear nomes de campos ou tabelas

#### 9.4	CONSULTAS QUE USAM OPERADORES LIKE E DATAS (Mínimo 12) <br>
    a) Criar outras 5 consultas que envolvam like ou ilike
    b) Criar uma consulta para cada tipo de função data apresentada.

#### 9.5	INSTRUÇÕES APLICANDO ATUALIZAÇÃO E EXCLUSÃO DE DADOS (Mínimo 6)<br>
    a) Criar minimo 3 de exclusão
    b) Criar minimo 3 de atualização

#### 9.6	CONSULTAS COM INNER JOIN E ORDER BY (Mínimo 6)<br>
    a) Uma junção que envolva todas as tabelas possuindo no mínimo 2 registros no resultado
    b) Outras junções que o grupo considere como sendo as de principal importância para o trabalho

#### 9.7	CONSULTAS COM GROUP BY E FUNÇÕES DE AGRUPAMENTO (Mínimo 6)<br>
    a) Criar minimo 2 envolvendo algum tipo de junção

#### 9.8	CONSULTAS COM LEFT, RIGHT E FULL JOIN (Mínimo 4)<br>
    a) Criar minimo 1 de cada tipo

#### 9.9	CONSULTAS COM SELF JOIN E VIEW (Mínimo 6)<br>
        a) Uma junção que envolva Self Join (caso não ocorra na base justificar e substituir por uma view)
        b) Outras junções com views que o grupo considere como sendo de relevante importância para o trabalho

#### 9.10	SUBCONSULTAS (Mínimo 4)<br>
     a) Criar minimo 1 envolvendo GROUP BY
     b) Criar minimo 1 envolvendo algum tipo de junção

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


