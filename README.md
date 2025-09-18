---
# Simulação de Pedido com Step Functions, DynamoDB e Lambda

## 📖 Descrição do Projeto

Esse projeto é inspirado no canal **"Be A Better Dev"**.

Ele simula a entrada de um pedido no **Step Function**, representando uma compra no valor de **\$200**.

Além disso, uma **função Lambda** foi utilizada para **deletar automaticamente** o pedido sempre que o valor for **maior que \$200**, removendo-o do DynamoDB.

---

## ⚙️ Tecnologias e Conceitos Utilizados

### 🌀 Step Functions

O **AWS Step Functions** é um serviço da AWS que permite orquestrar diferentes serviços em fluxos de trabalho automatizados.
Ele ajuda a criar processos complexos (como aprovar ou rejeitar pedidos) organizando várias etapas em sequência ou em paralelo.

No contexto deste projeto:

* O Step Function simula o fluxo de entrada de um pedido.
* Ele controla o processo de validação do valor da transação.

---

### 🗄️ DynamoDB

O **Amazon DynamoDB** é um banco de dados NoSQL totalmente gerenciado pela AWS, altamente escalável e de baixa latência.
Ele armazena dados em formato de tabelas com **chave-valor** e **documentos JSON**.

Neste projeto:

* A tabela DynamoDB guarda as informações do pedido.
* Estrutura básica de cada item:

  ```JSON
  {
    "orderID": "oID-100",
    "customerID": "001",
    "transactionAmount": 200.00,
    "ordercreatedTimestamp": "2025-09-17T13:30:00.123456+00:00",
    "customerAddress": "123 Fake St"
  }
  ```

---

### ⚡ Função Lambda

O **AWS Lambda** é um serviço serverless que executa código em resposta a eventos, sem necessidade de gerenciar servidores.

Neste projeto:

* A Lambda é acionada quando um pedido é inserido.
* Se o valor for **acima de \$200**, a função automaticamente **deleta o pedido** do DynamoDB.

---

## 🚀 Como esse fluxo funciona

1. Um pedido de \$200 é simulado na Step Function.
2. O pedido é salvo no DynamoDB com os dados do cliente.
3. A Lambda verifica o valor da transação:

   * Se **≤ \$200**, o pedido permanece no banco.
   * Se **> \$200**, a Lambda deleta o registro do DynamoDB.

---


