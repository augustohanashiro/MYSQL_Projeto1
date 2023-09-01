
# Melhorias Solicitadas📈

## Cliente PJ e PF – Uma conta pode ser PJ ou PF, mas não pode ter as duas informações 🏭/👦

Para distinguir se o cliente é PJ ou PF, adicionei uma coluna Enum("PJ","PF") unique na tabela cliente

```
SELECT * FROM cliente;
```
![Cliente](https://github.com/augustohanashiro/MYSQL_Projeto1/assets/49253803/31ef1c46-939d-47b4-8581-5970fa733d8f)


## Pagamento – Pode ter cadastrado mais de uma forma de pagamento 💵

Para pagamentos, foi criado uma tabela chamada formapagamento, contendo o registro das opções disponivilizadas

```
SELECT * FROM formapagamento;
```
![FormaPagamento](https://github.com/augustohanashiro/MYSQL_Projeto1/assets/49253803/196a19e1-c2b9-420a-b88c-753a98bed770)

## Entrega – Possui status e código de rastreio;

A tabela de entrega já foi criada com status durante as aulas, porém sem código de rastreio.
Este por sua vez foi adicionado como coluna na tabela de pedido

```
SELECT * FROM pedido;
```


![pedido](https://github.com/augustohanashiro/MYSQL_Projeto1/assets/49253803/dcb54835-135a-4176-8adb-19b77be52e14)
