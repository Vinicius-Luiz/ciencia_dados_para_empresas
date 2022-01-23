# Departamento de Marketing

## Contexto geral

A empresa precisa realizar campanhas personalizadas para cada tipo de perfil de cliente.

O objetivo maior é entender os hábitos do cliente, para que assim possamos agrupá-los por área de interesse. 

- entender os clientes e identificar suas necessidades
- entendendo os consumidores, podemos enviar campanhas específicas para necessidades específicas

| Coluna                           | Descrição                                                    |
| -------------------------------- | ------------------------------------------------------------ |
| CUSTID                           | Identificação do cliente                                     |
| BALANCE                          | Saldo para fazer compras                                     |
| BALANCE_FREQUENCY                | Frequência que o saldo é atualizado (1 = frequente, 0 = não frequente) |
| PURCHASES                        | Quantidade de compras realizadas                             |
| ONEOFFPURCHASES                  | Quantidade de compras realizadas                             |
| INSTALLMENTS_PURCHASES           | Quantidade de compras parceladas                             |
| CASH_ADVANCE                     | Dinheiro adiantado                                           |
| PURCHASES_FREQUENCY              | Frequência das compras (entre 1 e 0)                         |
| ONEOFF_PURCHASES_FREQUENCY       | Frequência de compras à vista (entre 1 e 0)                  |
| PURCHASES_INSTALLMENTS_FREQUENCY | Frequêncica de compras parceladas (entre 1 e 0)              |
| CASH_ADVANCE_FREQUENCY           | Frequência de saques de dinheiro adiantado                   |
| CASH_ADVANCE_TRX                 | Número de transações feitas como "Cash in Advance" (foi no caixa eletronico e solicitou dinheiro adiantado) |
| PURCHASES_TRX                    | Número de compras                                            |
| CREDIT_LIMIT                     | Limite do cartão de crédito                                  |
| PAYMENTS                         | Valor pago                                                   |
| MINIMUM_PAYMENTS                 | Valor mínimo pago                                            |
| PRC_FULL_PAYMENT                 | Percentual de pagamentos da fatura completa                  |
| TENURE                           | Posse do titular do cartão                                   |

## K-means

Algoritmo para trabalhar com agrupamento de dados.

<img src="graph2.png" style="zoom: 50%;" />

- Algoritmo não supervisionado (clustering - agrupamento)
  - Não temos uma classe, o objetivo não é previsões
- Os registros são agrupados baseado em atributos similares, por meio do cálculo da Distância Euclidiana
  - Formula matemática que vai medir o quanto dois pontos são parecidos

### Exemplo

> **Queremos encontrar dois grupos**
>
> ![](graph1.png)

> **Criaremos K centróides, sendo k=2. Os centróides são pontos que são inicializados aleatoriamente na base de dados**
>
> ![](graph3.png)

> **Após a criação dos centróides, verificamos os pontos que estão mais próximos de algum centróide existente**
>
> ![](graph4.png)

> **Vamos calcular um novo centróide para cada grupo**
>
> <img src="graph5.png" style="zoom:50%;" />

> **Vamos repetir da atualização dos centróides, o que pode acontecer é um dado mudar de grupo nessas atualizações da posição dos centróides**
>
> <img src="graph6.png" style="zoom:50%;" />



## Qual a quantidade adequada de grupos?

<img src="graph7.png"/>

Quando o valor do WCSS não possui uma queda tão brusca, não é interessante aumentar o número de grupos. Por isso esse método é chamado de método do cotovelo

<img src="graph8.png"/>