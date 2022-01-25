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
| PURCHASES                        | Valor de compras realizadas                                  |
| ONEOFFPURCHASES                  | Valor de compras realizadas                                  |
| INSTALLMENTS_PURCHASES           | Valor de compras parceladas                                  |
| CASH_ADVANCE                     | Dinheiro adiantado                                           |
| PURCHASES_FREQUENCY              | Frequência das compras (entre 1 e 0)                         |
| ONEOFF_PURCHASES_FREQUENCY       | Frequência de compras à vista (entre 1 e 0)                  |
| PURCHASES_INSTALLMENTS_FREQUENCY | Frequência de compras parceladas (entre 1 e 0)               |
| CASH_ADVANCE_FREQUENCY           | Frequência de saques de dinheiro adiantado                   |
| CASH_ADVANCE_TRX                 | Número de transações feitas como "Cash in Advance" (foi no caixa eletrônico e solicitou dinheiro adiantado) |
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
> *Os centróides possuem o valor médio do grupo que ele pertence, ou seja, ele possui a idade média do grupo e o valor economico médio do grupo*
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

# Análise dos 9 grupos criados

> **BALANCE**
>
> G1: Cliente com menos saldo em conta (104,33)
>
> G4: Clientes com maior saldo em conta (5448,2)

> **BALANCE_FREQUENCY**

> **PURCHASES**
>
> G3: Efetuam compras mais baratas (246,05)
>
> G4: Efetuam compras mais caras (27916,56)

> **ONEOFFPURCHASES**
>
> G4: Efetuam compras mais caras a vista (22354,31)
>
> G5: Efetuam compras mais baratas a vista (142,23)

> **INSTALLMENTS_PURCHASES**
>
> G3: Efetuam compras mais baratas parceladas (50,36)
>
> G3/G8: Efetuam compras mais caras parceladas (5562,24 & 2810,14)

> **CASH_ADVANCE**
>
> G2: Realizam valores altos de empréstimos no cartão de crédito (5139,99)
>
> G1/G6: Realizam valores baixos de empréstimos no cartão de crédito (282,68 & 221,18)

> **PURCHASES_FREQUENCY**
>
> G1/G3: Realizam compras com pouca frequência (0,27 & 0,15)
>
> G4/G8: Realizam compras frequentemente (0,91 & 0,96)

> **ONEOFF_PURCHASES_FREQUENCY**
>
> G1/G3/G5/G6: Realizam compras a vista com pouca frequência ( |- 0,04 and 0,09 -|)
>
> G0/G4: Realizam compras a vista com muita frequência (0,77 & 0,85)

> **PURCHASES_INSTALLMENTS_FREQUENCY**
>
> G3: Realizam compras parceladas com pouca frequência (0,07)
>
> G6/G8: Realizam compras parceladas com mais frequência (0,84 & 0,86)

> **CASH_ADVANCE_FREQUENCY**
>
> G2: Realizam empréstimo no cartão de crédito com mais frequência (0,52)

> **CREDIT_LIMIT**
>
> G4: Possuem limite de crédito muito alto (16043,48)
>
> G7: Possuem limite de crédito baixo (2446,42)

> **MINIMUM_PAYMENTS**
>
> G5: Efetuam muitos pagamentos com o valor mínimo da fatura (27628,63)

> **PRC_FULL_PAYMENT**
>
> G2/G3/G5: Pagam o valor total da fatura com pouca frequência (|- 0 and 0,02 -|)
>
> G4: Pagam o valor total da fatura com mais frequência (0,52)

> **TENURE**
>
> G7: Clientes novos (7 anos)

| Grupo | Descrição                                                    |
| ----- | ------------------------------------------------------------ |
| G0    | Realizam compras a vista com muita frequência (0,77)         |
| G1    | Clientes possuem menos saldo em conta(104,33); Realizam valores baixos de empréstimos no cartão de crédito (282,68); Realizam compras com pouca frequência (0,27); Realizam compras a vista com pouca frequência. |
| G2    | Realizam valores altos de empréstimos no cartão de crédito (5139,99); Realizam empréstimo no cartão de crédito com mais frequência (0,52); Pagam o valor total da fatura com pouca frequência. |
| G3    | Efetuam compras mais baratas (246,05); Efetuam compras mais baratas parceladas (50,36); Realizam compras com pouca frequência (0,15); Realizam compras a vista com pouca frequência; Realizam compras parceladas com pouca frequência; Pagam o valor total da fatura com pouca frequência. |
| G4    | Clientes com maior saldo em conta (5448,2); Efetuam compras mais caras (27916,56); Efetuam compras mais caras a vista (22354,31); Realizam compras frequentemente (0,91); Realizam compras a vista com muita frequência (0,85); Possuem limite de crédito muito alto (16043,48); Pagam o valor total da fatura com mais frequência (0,52). |
| G5    | Efetuam compras mais baratas a vista (142,23); Realizam compras a vista com pouca frequência; Efetuam muitos pagamentos com o valor mínimo da fatura (27628,63); Pagam o valor total da fatura com pouca frequência. |
| G6    | Realizam valores baixos de empréstimos no cartão de crédito (221,18); Realizam compras a vista com pouca frequência; Realizam compras parceladas com mais frequência (0,84) |
| G7    | Possuem limite de crédito baixo (2446,42); Clientes novos (7 anos). |
| G8    | Efetuam compras mais caras parceladas (2810,14); Realizam compras frequentemente (0,96); Realizam compras parceladas com mais frequência (0,86). |

