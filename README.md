# O que será abordado nesse projeto?
- De forma introdutória, Design patterns(Padrões de projeto)
- Usando o padrão DAO(Data Access Object)
- Usando o padrão Factory
- Java Persistence API(JPA)
- Hibernate

# Design patterns(Padrões de projeto)

 - **Design patterns(Padrões de projeto)**: são soluções reutilizáveis para problemas comuns que surgem durante o desenvolvimento de software. Eles são como um guia ou uma receita para resolver questões de design em diferentes contextos, promovendo melhores práticas e facilitando a manutenção e a escalabilidade do código.

# DAO (Data Access Object)

 - **O padrão DAO (Data Access Object)** é um dos muitos padrões de design (design patterns) utilizados na programação orientada a objetos. Ele se enquadra na categoria dos padrões estruturais. DAO é especialmente útil para separar a lógica de negócios da lógica de acesso a dados, promovendo uma melhor organização e manutenção do código.
 - Ideia geral do padrão DAO: para cada entidade, haverá um objeto responsável por fazer acesso a dados relacionado a esta entidade. Por exemplo:
    - `Cliente`: `ClienteDao`
    - `Produto`: `ProdutoDao`
    - `Pedido`: `PedidoDao`
 - Nesse projeto, cada **DAO** será definido por uma interface

# Factory 
- **O padrão Factory (Factory Method)** é um dos muitos padrões de design (design patterns) utilizados na programação orientada a objetos. Ele se enquadra na categoria dos padrões de criação. O Factory é especialmente útil para encapsular a lógica de criação de objetos, promovendo uma melhor organização e manutenção do código.
- Ideia geral do **padrão Factory**: Para cada tipo de objeto que precisa ser instanciado, haverá uma fábrica responsável por criar esse objeto. A fábrica encapsula a lógica de criação, permitindo que o código cliente não precise conhecer os detalhes de como os objetos são criados. 
- Nesse projeto, a injeção de dependência vai ocorrer por meio do **Factory**

# Java Persistence API (JPA)

 - O **Java Persistence API (JPA)** é a especificação padrão da plataforma Java EE (pacote `jakarta.persistence`) para mapeamento objeto-relacional e persistência de dados. JPA é definido pela **JSR 338**. Para trabalhar com JPA, você precisa incluir uma implementação da API, como o **Hibernate**.
[Saiba mais](http://download.oracle.com/otn-pub/jcp/persistence-2_1-fr-eval-spec/JavaPersistence.pdf)
### Aplicação
#
 ![imagem](diagrama-jpa.png)
#
# Como está dividido o projeto?
 - pacote *application*
    - Aqui há duas aplicações testes para mostrar o uso;
 - pacote *db*
    - Aqui estão as configurações de conexão com o banco de dados;
    - E também as exceções para lidar com falhas;
- pacote *model*, com seus subpacotes
    - *model.dao*
        - Que contém as interfaces DAOs;
    - *model.dao.impl*
        - Que contém as implementações DAOs;
    - *model.entities*
        - Onde ficam as entidades do negócio, que nesse exemplo são, Department e Seller

## Classes do JPA que estão em uso aqui:

1. **EntityManager**:
    [EntityManager](http://download.oracle.com/otn-pub/jcp/persistence-2_1-fr-eval-spec/JavaPersistence.pdf)
   - Encapsula uma conexão com o banco de dados.
   - Realiza operações de acesso a dados (inserção, remoção, atualização, deleção) em entidades (clientes, produtos, pedidos etc.) monitoradas no mesmo contexto de persistência.
   - Escopo: Normalmente, mantém-se uma instância única de `EntityManager` por thread do sistema (em aplicações web, uma por requisição).

2. **EntityManagerFactory**:
    [EntityManagerFactory](https://docs.oracle.com/javaee/7/api/javax/persistence/EntityManagerFactory.html)
   - Utilizado para instanciar objetos `EntityManager`.
   - Escopo: Normalmente, mantém-se uma instância única de `EntityManagerFactory` para toda a aplicação.

## Como usar: 
  - Clone o repositório
  - Usando o MySQL Workbench, crie uma base de dados chamada "coursejdbc"
  - Baixar o MySQL Java Connector
  - Caso ainda não exista, criar uma User Library contendo o arquivo .jar do driver do MySQL
    - Window -> Preferences -> Java -> Build path -> User Libraries
    - Dê o nome da User Library de MySQLConnector
    - Add external JARs -> (localize o arquivo jar)
  - Certifique-se que o arquivo `db.properties` contém as informações corretas da sua conexão com o MySQL
    - user=developer
    - password='suasenhaaqui'
    - dburl=jdbc:mysql://localhost:3306/coursejdbc
    - useSSL=false






