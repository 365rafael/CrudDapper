# Trabalhando com DAPPER e .NET

O Dapper é um ORM (Object Relational Mapping) voltado para o desenvolvimento .NET, onde seu principal objetivo é melhorar o desempenho das consultas ao banco de dados. Ele não conta com toda a gama de um ORM mais facilita muito o desenvolvimento de aplicações com melhor desempenho.

[Saiba mais](https://thiagoborges.net.br/o-que-e-o-dapper-e-como-utilizar/)

          public async Task<IEnumerable<Livro>> CreateLivro(Livro livro)
      {
          using (var con = new SqlConnection(getConnection))
          {
              var sql = "insert into livros (titulo, autor) values (@titulo, @autor)";
              await con.ExecuteAsync(sql, livro);
              return await con.QueryAsync<Livro>("select * from livros");
          }
      }

            public async Task<IEnumerable<Livro>> DeleteLivro(int livroId)
      {
          using (var con = new SqlConnection(getConnection))
          {
              var sql = "delete from livros where id = @id";
              await con.ExecuteAsync(sql, new {id = livroId});
    
              return await con.QueryAsync<Livro>("select * from livros");
          }
      }
