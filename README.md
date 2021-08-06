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


<h3>Geração de códigos</h3>

**Comando de exempo para gerar client java com springframework**
```
npx @openapitools/openapi-generator-cli generate   \
 -i delivery-api/swagger-openapi-3.json  \
 --api-package com.rafaelbarros.delivery.client.api  \
 --model-package com.rafaelbarros.delivery.client.model  \
 --invoker-package com.rafaelbarros.delivery.client.invoker  \
 --group-id com.rafaelbarros  \
 --artifact-id spring-swagger-codegen-api-client  \
 --artifact-version 0.0.1-SNAPSHOT   -g java  \
 --library resttemplate   -o spring-swagger-codegen-api-client

```
**Comando de exempo para gerar server em nodejs com express**
```
npx @openapitools/openapi-generator-cli generate \
 -i delivery-api/swagger-openapi-3.json \
 -g nodejs-express-server \
 -o node-srv-delivery-api
```