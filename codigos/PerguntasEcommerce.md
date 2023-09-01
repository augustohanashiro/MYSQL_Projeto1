# Perguntas do Projeto
## Quantos pedidos foram feitos por cada cliente?

Para descobrir o numero de pedidos por cliente, foi feito uma query sobre a tabela pedido, agrupando todos os pedidos por IdCliente ordenado pelo número de pedidos

```
Select IdCliente, count(*) as N_Pedido from pedido
group by IdCliente
order by N_Pedido;

```

![PedidosPorCliente](https://github.com/augustohanashiro/MYSQL_Projeto1/assets/49253803/dcb54835-135a-4176-8adb-19b77be52e14)

## Algum vendedor também é fornecedor?

Para responder essa pergunta, podemos fazer por dois métodos: Ou com a cláusula Where, ou com inner join

```

Select IdFornecedor, RazãoSocial from fornecedor
	where CNPJ in (select CNPJ from vendedorterceiro);

--                  OU

select f.IdFornecedor, f.RazãoSocial from fornecedor f
    inner join vendedorterceiro using (cnpj);
```

Com isso podemos verificar que apenas um vendedor é fornecedor


![VendedorFornecedor](https://github.com/augustohanashiro/MYSQL_Projeto1/assets/49253803/3d25e0d8-bbc0-4f18-8791-6e8984fd0257)


## Relação de produtos fornecedores e estoques

### Relação produto x fornecedor
Para pegar a relação de produtos ofertado por cada fornecedor, foi feito a relação de 3 tabelas: Produto x fornecedor x ProdutoFornecedor
```
select f.RazãoSocial, p.Pnome from produtofornecedor as pf
inner join fornecedor f on f.IdFornecedor = pf.IdFornecedor
inner join produto p on p.IdProduto = pf.IdProduto;
``` 
![ProdutoFornecedor](https://github.com/augustohanashiro/MYSQL_Projeto1/assets/49253803/ab441a0d-d411-4a62-bb87-d39565c7d8d6)



### Relação produto x estoque

Para pegar a relação de produtos em cada estoque, foi feito a relação de 3 tabelas: Produto x Estoque x ProdutoEstoque 
```
select p.Pnome, e.IdEstoque, pe.localização from produtonoestoque as pe
inner join produto as p on p.idproduto = pe.idproduto
inner join estoque as e on e.Idestoque = pe.idestoque;
```
![ProdutoEstoque](https://github.com/augustohanashiro/MYSQL_Projeto1/assets/49253803/ee247d3c-55e3-422e-826a-6a588f8ebd4a)

## Relação de Fornecedores e produtos




Nesta pergunta, eu fiz o agrupamento dos produtos por categoria, e só exibi as categorias que possuem pelo menos 5 ou mais variedades;

```
select Categoria, count(*) as VariedadeProdutos from produto
group by categoria
having VariedadeProdutos >=5;
```
![VariedadeProdutos](https://github.com/augustohanashiro/MYSQL_Projeto1/assets/49253803/96245410-7461-4a9b-8fb0-dda25b2ff04d)

