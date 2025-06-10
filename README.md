# Projeto CRUD em Go com MySQL

## Descrição
Este projeto é um exemplo prático de como realizar operações CRUD (Create, Read, Update e Delete) em uma base de dados MySQL utilizando a linguagem Go. Ele demonstra o uso da biblioteca padrão `database/sql` em conjunto com o driver `go-sql-driver/mysql` para interagir com o banco de dados, além de utilizar o pacote `google/uuid` para geração de identificadores únicos para os produtos.

## Funcionalidades
- **Criação de Produtos**: Gera um UUID para cada novo produto e insere no banco de dados.
- **Atualização de Produtos**: Atualiza o nome e preço de um produto existente.
- **Leitura de Produtos**: 
  - Recupera todos os produtos do banco de dados.
  - (Comentado) Recupera um produto específico pelo ID.
- **Exclusão de Produtos**: Remove um produto do banco de dados pelo ID.

## Requisitos
- [Go](https://golang.org/dl/) instalado (versão 1.16+ recomendada).
- Banco de dados MySQL rodando localmente.
- Banco de dados chamado `godatabase` configurado com a tabela `products`.

### Estrutura da Tabela `products`
```sql
CREATE DATABASE godatabase;

USE godatabase;

CREATE TABLE products (
    id VARCHAR(36) PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    price DECIMAL(10,2) NOT NULL
);
```

## Instalação
1. Clone o repositório:
   ```bash
   git clone https://github.com/TonyOps/CRUD-em-GO.git
   cd CRUD-em-GO
   ```

2. Instale as dependências:
   ```bash
   go mod tidy
   ```

3. Certifique-se de ter o MySQL rodando e configure o usuário `root` com senha `root` ou ajuste as credenciais no código.

## Uso
1. Execute o programa:
   ```bash
   go run main.go
   ```

2. O programa realizará as seguintes ações:
   - Insere um produto chamado "Notebook" com preço R$ 999,99.
   - Atualiza o preço para R$ 899,99.
   - Lista todos os produtos cadastrados.
   - Exclui o produto após a listagem.

## Exemplo de Saída
```
Product Notebook, possui o valor de R$ 899.99
```

## Estrutura do Código
- **Struct `Product`**: Representa um produto com campos ID (UUID), Name e Price.
- **Função `NewProduct`**: Cria uma nova instância de `Product` com ID gerado automaticamente.
- **Funções de CRUD**:
  - `insertProduct`: Insere um novo produto no banco de dados.
  - `updateProduct`: Atualiza os dados de um produto existente.
  - `selectProduct` (comentado): Recupera um produto pelo ID (desativado por padrão).
  - `selectAllProducts`: Recupera todos os produtos cadastrados.
  - `deleteProduct`: Remove um produto do banco de dados.
