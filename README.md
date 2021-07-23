<h2> Simple delivery manager API </h2>

<details>
   <summary>Delivery API Flow</summary>

```
title Delivery Flow

participant Mailer
participant Buyer
participant Producer
participant API
participant MS

Buyer -> Producer:requisita a compra \ndo produto
Producer -> API: Envia dados de entrega \npara o serviço
API -> MS: Valida e registra \nos dados para delivery
MS --> Producer: Devolve o sucesso da transação
Mailer -> API: Consulta lista de produtos disponiveis para delivery
API --> Mailer: Devolve lista de produtos
Mailer -> API: Requisita um produto para entregar
API -> MS: Atualiza status e dados de \do entregador
API -->Mailer: Confirma a solicitação
Mailer ->API: Atualiza status da entrega
API -->Mailer: Confirma a solicitação
Mailer ->API: Confirma a entrega
API -> MS: Registra dados da entrega
MS->API: Confirma atualizacao do registro
API -->Mailer: Confirma a finalização do serviço
```
</details>

  ![image](https://user-images.githubusercontent.com/4924002/126730780-80b2db6b-7689-4682-b0b7-1029209e7a2b.png)
