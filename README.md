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
Este documento contém a especificação do projeto do banco de dados <nome do projeto> 
<br>e motivação da escolha realizada. <br>

> A empresa "AiQueFome!" busca alimentar seus clientes não so com comida, mas com cultura. É uma empresa de delivery de comida que busca levar aos seus clientes novas experiencias em forma de pratos caracteristicos de diversas nações, para que eles possam sentir um gostinhos das outras culturas dentro do conforto de seu proprio lar. Para alcançar seu objetivo a empresa está querendo criar um aplicativo que irá permitir seus clientes pedirem suas refeições de forma fácil e prática. Para gerenciar os pedidos, o aplicativo irá armazenar as informações relativas ao Cliente, ao Pedido, ao Restaurante, ao Entregador e a Refeição. 
 

### 3.MINI-MUNDO<br>

Descrever o mini-mundo! (Não deve ser maior do que 30 linhas, se necessário resumir para justar) <br>
Entrevista com o usuário e identificação dos requisitos.(quando for o caso de sistemas com cliente  real)<br>
Descrição textual das regras de negócio definidas como um  subconjunto do mundo real 
cujos elementos são propriedades que desejamos incluir, processar, armazenar, 
gerenciar, atualizar, e que descrevem a proposta/solução a ser desenvolvida.

> O sistema proposto para a "Devcom Projetos conterá as informacões aqui detalhadas. Dos Projetos serão armazenados o número, nome e cidade. Dos Departamentos serão armazenados o número e nome. O cliente destacou que cada projeto pode ter vários departamentos auxiliando no seu desenvolvimento, e cada departamento pode estar envolvido em vários projetos. Os dados relativos aos empregados que serão armazenados são: rg, nome, cpf, salário, data inicial do salario e supervisor de cada empregado. É importante destacar que cada empregado pode ser supervisionado por outro empregado, e obrigatoriamente deve estar alocado a um único departamento, mas pode gerenciar vários departamentos ou não gerenciar nenhum. Um empregado também pode participar de vários projetos, caso seja necessário, mas não precisa obrigatoriamente estar alocado em algum projeto. Com relação aos dependentes serão armazenadas as informações de nome do dependente, data de nascimento, sexo e grau de parentesco. Cada empregado pode ter vários dependentes, mas um dependente esta associado apenas a um único empregado. Com relação ao histórico de salário devemos armazenar as informações de valor do salário, data de início do salário no período e data final do salário no período. É importante lembrar que cada funcionario pode ter diversos eventos de histórico de salário associados a ele visto que este dado pode ser alterado várias vezes. 

### 4.PERGUNTAS A SEREM RESPONDIDAS E TABELA DE DADOS<br>
#### 4.1 QUAIS PERGUNTAS PODEM SER RESPONDIDAS COM O SISTEMA PROPOSTO?
    a) O sistema proposto poderá fornecer quais tipos de relatórios e informaçes? 
    b) Crie uma lista com os 5 principais relatórios que poderão ser obtidos por meio do sistema proposto!
    
> A Empresa DevCom precisa inicialmente dos seguintes relatórios:
* Relatório que mostre o nome de cada supervisor(a) e a quantidade de empregados supervisionados.
* Relatório relativo aos os supervisores e supervisionados. O resultado deve conter o nome do supervisor e nome do supervisionado além da quantidade total de horas que cada supervisionado tem alocada aos projetos existentes na empresa.
* Relatorio que mostre para cada linha obtida o nome do departamento, o valor individual de cada salario existente no  departamento e a média geral de salarios dentre todos os empregados. Os resultados devem ser apresentados ordenados por departamento.
* Relatório que mostre as informações relacionadas a todos empregados de empresa (sem excluir ninguém). As linhas resultantes devem conter informações sobre: rg, nome, salario do empregado, data de início do salario atual, nomes dos projetos que participa, quantidade de horas e localização nos referidos projetos, numero e nome dos departamentos aos quais está alocado, informações do historico de salário como inicio, fim, e valores de salarios antigos que foram inclusos na referida tabela (caso possuam informações na mesma), além de todas informações relativas aos dependentes. 
>> ##### Observações: <br> a) perceba que este relatório pode conter linhas com alguns dados repetidos (mas não todos). <br>  b) para os empregados que não possuirem alguma destas informações o valor no registro deve aparecer sem informação/nulo. 
* Relatório que obtenha a frequencia absoluta e frequencia relativa da quantidade de cpfs únicos no relatório anterior. Apresente os resultados ordenados de forma decrescente pela frequencia relativa.

 ### 5.MODELO CONCEITUAL<br>
    A) Utilizar a Notação adequada (Preferencialmente utilizar o BR Modelo 3)
    B) O mínimo de entidades do modelo conceitual pare este trabalho será igual a 5 e o Máximo 7.
        * informe quais são as 3 principais entidades do sistema em densenvolvimento<br>(se houverem mais de 3 entidades, pense na importância da entidade para o sistema)       
    C) Principais fluxos de informação/entidades do sistema (mínimo 3). <br>Dica: normalmente estes fluxos estão associados as tabelas que conterão maior quantidade de dados 
    D) Qualidade e Clareza
        Garantir que a semântica dos atributos seja clara no esquema (nomes coerentes com os dados).
        Criar o esquema de forma a garantir a redução de informação redundante, possibilidade de valores null, 
        e tuplas falsas (Aplicar os conceitos de normalização abordados).   
        
![image](https://user-images.githubusercontent.com/91472785/198711788-aa7b48be-f355-4aaf-a5f5-96619f6fa9c5.png)

    
        
    
#### 5.1 Validação do Modelo Conceitual
    Grupo 1: Ilanna,Mariana,Bruna,Daianny
    [Grupo02]: [Nomes dos que participaram na avaliação]

#### 5.2 Descrição dos dados 

    RESTAURANTE: Tabela que armazena os dados de cada restaurante
    PRODUTO: Tabela que armazena as informações dos produtos
    PEDIDO: Tabela que armazena as informações referentes dos pedidos
    ENTREGADOR: Tabela que armazena os dados do entregador
    CLIENTE: Tabela que armazena os dados dos clientes
    ENDERECO: Tabela que armazena o endereço dos clientes


### 6	MODELO LÓGICO<br>
        
 ![image](https://user-images.githubusercontent.com/91472785/198712571-cf8d3a91-0a5e-47d0-a322-80c3e82724a5.png)


### 7	MODELO FÍSICO<br>
        /* logico - trab grupo: */
        CREATE TABLE CLIENTE_ENDERECO (
            cpf VARCHAR PRIMARY KEY,
            nome VARCHAR,
            telefone INTEGER,
            rua VARCHAR,
            numero INTEGER,
            bairro VARCHAR
        );

        CREATE TABLE PRODUTO (
            cod_produto INTEGER PRIMARY KEY,
            preco FLOAT
        );

        CREATE TABLE RESTAURANTE (
            cnpj VARCHAR PRIMARY KEY,
            nome VARCHAR
        );

        CREATE TABLE ENTREGADOR (
            cpf VARCHAR PRIMARY KEY,
            nome VARCHAR,
            turno VARCHAR,
            salario FLOAT
        );

        CREATE TABLE PEDIDO (
            cod_pedido INTEGER PRIMARY KEY,
            preco_total FLOAT,
            FK_ENTREGADOR_cpf VARCHAR
        );

        CREATE TABLE Produz (
            fk_RESTAURANTE_cnpj VARCHAR,
            fk_PRODUTO_cod_produto INTEGER
        );

        CREATE TABLE Compoe (
            fk_PRODUTO_cod_produto INTEGER,
            fk_PEDIDO_cod_pedido INTEGER
        );

        CREATE TABLE Entrega (
            fk_ENTREGADOR_cpf VARCHAR,
            fk_CLIENTE_ENDERECO_cpf VARCHAR,
            data_hora TIMESTAMP
        );

        CREATE TABLE Feito (
            fk_PEDIDO_cod_pedido INTEGER,
            fk_CLIENTE_ENDERECO_cpf VARCHAR
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


