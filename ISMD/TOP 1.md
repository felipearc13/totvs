Para selecionar apenas a segunda linha de uma consulta no SQL Server basta utilizar alguns artifícios como limitar a quantidade de registros retornados excluindo também os registros indesejados. Para isto utilizaremos o TOP e o NOT IN. Já expliquei aqui um pouco sobre estes comandos, inclusive em outras linguagens.


Veja um exemplo.

```
SELECT TOP 1 nome_dos_campos FROM nome_tabela
WHERE     (campo_chave NOT IN
     (SELECT TOP 1 campo_chave FROM nome_tabela)
)
```
Do mesmo modo, para selecionar a terceira, quarta ou qualquer linha basta alterar o valor do TOP da sub-select.
Por exemplo, para pegar a 15ª linha faça:
```

SELECT TOP 1 nome_dos_campos FROM nome_tabela
WHERE     (campo_chave NOT IN
     (SELECT TOP 14 campo_chave FROM nome_tabela)
)
```