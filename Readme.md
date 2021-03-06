### 🚀 Sobre o desafio

Nesse desafio devemos desenvolver uma aplicação para armazenar transações financeiras de entrada e saída, que deve permitir o cadastro e a listagem dessas transações.

### Para rotas da aplicação, ficará dessa forma

- `POST /transactions`: A rota deve receber `title, value e type` dentro do corpo da requisição, sendo `type` o tipo da transação, que deve ser `income para entradas (depósitos)` e `outcome para saídas (retiradas)`. Ao cadastrar uma nova transação, ela deve ser armazenada dentro de um objeto com o seguinte formato :

```
  {
    "id": "uuid",
    "title": "Salário",
    "value": 3000,
    "type": "income"
  }
```

- `GET /transactions`: Essa rota deve retornar uma listagem com todas as transações que foi cadastrada até agora, junto com o valor de soma de entradas, retiradas e total de crédito. Essa rota deve retornar um objeto com o formato a seguir:

```
{
  "transactions": [
    {
      "id": "uuid",
      "title": "Salário",
      "value": 4000,
      "type": "income"
    },
    {
      "id": "uuid",
      "title": "Freela",
      "value": 2000,
      "type": "income"
    },
    {
      "id": "uuid",
      "title": "Pagamento da fatura",
      "value": 4000,
      "type": "outcome"
    },
    {
      "id": "uuid",
      "title": "Cadeira Gamer",
      "value": 1200,
      "type": "outcome"
    }
  ],
  "balance": {
    "income": 6000,
    "outcome": 5200,
    "total": 800
  }
}
```

### Para passar nos `Test` o legal que segui a as dicas

- `Dica 01`: Dentro de balance, o income é a soma de todos os valores das transações com `type` income. O outcome é a soma de todos os valores das transações com type outcome, e o total é o valor de income - outcome.

= `Dica 02`: Para fazer a soma dos valores, você pode usar a `função reduce` para agrupar as transações pela propriedade `type`, assim você irá conseguir somar todos os valores com facilidade e obter o retorno do balance.

<h3>Para esse desafio temos os seguintes Test:</h3>

`should be able to create a new transaction`: Para que esse teste passe, sua aplicação deve permitir que uma transação seja criada, e retorne um json com a transação criada.

`should be able to list the transactions`: Para que esse teste passe, sua aplicação deve permitir que seja retornado um objeto contendo todas as transações junto ao balanço de income, outcome e total das transações que foram criadas até o momento.

`should not be able to create outcome transaction without a valid balance`: Para que esse teste passe, sua aplicação não deve permitir que uma transação do tipo outcome extrapole o valor total que o usuário tem em caixa, retornando uma resposta com código HTTP 400 e uma mensagem de erro no seguinte formato: { error: string }

### Ao fim do Test, o ideal que faça aquele querido comando:

`yarn test`
