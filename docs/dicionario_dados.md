# Dicionário de Dados

## Fonte bruta - Bronze

Arquivo: `data/raw/dados_historicos_vendas_ecommerce.csv`

| Coluna original | Significado | Observações de qualidade |
|---|---|---|
| `ID do PEDIDO` | Identificador do pedido | 105.000 valores únicos |
| `DATA DO PEDIDO` | Data da realização do pedido | Fonte em formato americano e com necessidade de padronização |
| `fk_tbclientes_id_cliente` | Identificador do cliente | Campo numérico de referência |
| `CaTeGoRiA Produto` | Categoria do produto | Nulos, espaços excedentes e nomenclatura não padronizada |
| `nm_regiao` | Região brasileira | Sudeste, Sul, Nordeste, Centro-Oeste e Norte |
| `qtd.` | Quantidade vendida | Valores <= 0 e alguns registros contendo texto (`qtd.`) |
| `Preço Unitário (R$)` | Preço unitário | Valor monetário |
| `dixconto` | Percentual de desconto | Nome inconsistente; zero é considerado valor válido |
| `método-pagamento` | Método de pagamento | 11 variações textuais para 4 métodos lógicos |
| `dias_para_entrega` | Dias entre pedido e entrega | Outliers abaixo de 1 e acima de 365 |
| `nr_estrelas_cliente` | Avaliação do cliente | Valores fora da escala esperada de 1 a 5 |

## Camada analítica - Gold

Arquivo: `data/gold/analytics_data_ecommerce.csv`

| Coluna | Significado |
|---|---|
| `Data do Pedido` | Data do pedido padronizada |
| `Categoria Produto` | Categoria tratada do produto |
| `Região` | Região brasileira |
| `Quantidade Vedida` | Quantidade vendida (nome mantido como na implementação original) |
| `Preço Unitário` | Preço unitário do item |
| `Desconto` | Percentual de desconto |
| `Quantidade de Dias Entrega` | Prazo de entrega tratado |
| `Avaliação do Cliente` | Avaliação tratada do cliente |
| `Metodo de Pagamento` | Método de pagamento padronizado |
| `Valor total venda` | Valor de venda após desconto |
| `Valor total desconto aplicado` | Valor monetário do desconto aplicado |
| `Data do Pedido Dia` | Dia extraído da data |
| `Data do Pedido Mês` | Mês extraído da data |
| `Data do Pedido Ano` | Ano extraído da data |

## Fórmulas conceituais

### Valor total da venda

```text
quantidade * preço unitário * (1 - desconto)
```

### Valor do desconto aplicado

```text
quantidade * preço unitário * desconto
```
