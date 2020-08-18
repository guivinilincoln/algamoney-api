  - # Projeto de API com Spring REST 

    #### O que é SOAFEA ? 
    Service-Oriented Front-End Architecture = Arquitetura de Front-End Orientada a Serviços

    #### Ideia básica:
    Remover toda a lógica de apresentação de apresentação do servidor e levar para o cliente.

    #### Benefícios:
      -  Desenvolvimento assíncrono do front-end e back-end;
      - Escalabilidade;
      - Interoperabilidade;
      - Melhor experiência do usuário e baixa latência;

    ####  O que é REST ?

    Rest, que é a abreviatura de Representational State Transfer, é um conjunto de restrições utilizadas para que as requisições HTTP atendam as diretrizes definidas na arquitetura. Basicamente, as restrições determinadas pela arquitetura Rest são:

    cliente-servidor: as aplicações existentes no servidor e no cliente devem ser separadas;
    sem estado: as requisições são feitas de forma independente, ou seja, cada uma executa apenas uma determinada ação;
    cache: a API deve utilizar o cache para evitar chamadas recorrentes ao servidor;
    interface uniforme: agrupa outros quatro conceitos em que determina que os recursos devem ser identificados, a manipulação dos recursos deve ser por meio de representação, com mensagens autodescritivas e utilizar links para navegar pelo aplicativo.

    Portanto, quando se fala em Rest API, significa utilizar uma API para acessar aplicações back-end, de modo que essa comunicação seja feita com os padrões definidos pelo estilo de arquitetura Rest.


    ####  Ambiente de desenvolvimento REST:

      -   Java 8 ou versões acima;
      -   Spring Tools 4 for Eclipse
      -   POSTMAN
      -   MYSQL
      -   Flyway

    ####  Criando um projeto spring no Eclipse:

    Obs: Lembrar de ir em "Help > Eclipse Marketplace > Find " e buscar por "Spring", localizar a opção "Spring Tools" clicar em "Installed", so aceitar todos os termos e aguardar a reinicialização da IDE.

    1. Com o eclipse aberto, selecionar "File > New > New Spring Starter Project ";
    2. Preencher os campos com as informações do projeto;
    3. Clicar em Next;
    4. No campo Availabe, buscar por Web, DevTools e JPA.
    5. Clicar em Finish;

    Será criado seu novo projeto em Spring.

    ####  Adicionando dependências: 
     Nesse projeto vamos utilizando o MYSQL e o Flyway, para podermos utilizar essas ferramentas dentro do projeto, devemos adicionar suas dependências no `pom.xml`.
    1. Abra o arquivo `pom.xml`;
    2. Dentro da hierarquia `<dependencies>` AQUI  `<dependencies>`, adicione as dependências abaixo;

    ```
            <dependency>
    			<groupId>mysql</groupId>
    			<artifactId>mysql-connector-java</artifactId>
    			<scope>runtime</scope>
    		</dependency> 
    		<dependency>
    		    <groupId>org.flywaydb</groupId>
    		    <artifactId>flyway-core</artifactId>
    		</dependency>
    ```
     3. Salvar o arquivo e fechar.

    Pronto nossas novas dependências estão instaladas.


    ####  Configurando application.properties para conexão com banco: 
    1. Abrir o arquivo `application.properties`;
    2. Adicionar os seguintes comandos:

    ```ruby 
    spring.jpa.database=MYSQL
    spring.datasource.url=jdbc:mysql://localhost/algamoneyapi?createDatabaseIfNotExist=true&useSSL=false&useTimezone=true&serverTimezone=UTC
    spring.datasource.username=root
    spring.datasource.password=root
    spring.jpa.show-sql=true 
    ```
     3. Salvar e pronto.
     Sua conexão com o banco de dados MYSQL esta feita.

    ####  Criando a migração para o flyway: 
    1. Dentro de `src/main/resources>`, criar uma pasta chamada "db";
    2. Dentro de "db" criar uma pasta chamada "migration";
    3. Dentro de "migration" criar um arquivo do tipo "File" e dar o nome de "V01_nome_a_escolha.sql".
        Esse arquivo será executado em tempo de execução pelo nosso programa, ele contem as queries para que nosso sistema utilizar.
    ##### Exemplo: 
    ```sql
        CREATE TABLE categoria(
        	codigo BIGINT(20) PRIMARY KEY AUTO_INCREMENT,
        	nome VARCHAR(50) NOT NULL
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
         
        INSERT INTO categoria (nome) values ('Lazer');
        INSERT INTO categoria (nome) values ('Alimentação');
        INSERT INTO categoria (nome) values ('Supermercado');
        INSERT INTO categoria (nome) values ('Farmácia');
        INSERT INTO categoria (nome) values ('Outros');
    ```
