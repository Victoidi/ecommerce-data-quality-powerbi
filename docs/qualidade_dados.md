# Resumo de Qualidade dos Dados

## Diagnóstico da fonte

- Tipo da fonte: CSV estático / cold data.
- Classificação: dados estruturados.
- Registros: 105.000.
- Duplicidades encontradas: 0.
- Tratamento e transformação: necessários.

## Problemas identificados

### Categoria de produto

- 132 valores nulos.
- 14 registros com espaços à esquerda/direita.
- 22 representações distintas na fonte, reduzidas para 12 categorias válidas após padronização.
- Nulos convertidos para `Não informado`.

### Quantidade

- 38 registros com valor menor ou igual a zero.
- Desses, 26 são zero e 12 negativos.
- 7 registros incluem texto junto ao número, como `1 qtd.`.
- O tratamento separa o componente numérico e corrige valores inconsistentes.

### Método de pagamento

A fonte apresenta 11 variações textuais:

- `pix` / `PIX`
- `boleto` / `Boleto` / `B0let0`
- `crédito` / `Crédito` / `Crédit0`
- `débito` / `Débito` / `Débit0`

Após tratamento, foram consolidadas em quatro categorias:

- Pix
- Boleto
- Crédito
- Débito

### Prazo de entrega

- 14 registros fora da regra aceitável de 1 a 365 dias.
- Há valores negativos, zero e valores extremos como 999 dias.
- Os valores inconsistentes foram tratados usando uma medida representativa da distribuição.

### Avaliação do cliente

- 9 registros fora da escala válida de 1 a 5.
- Valores inconsistentes foram tratados para preservar coerência analítica.

### Desconto

- 68 registros possuem desconto igual a zero.
- Esses valores foram classificados como outliers saudáveis, pois representam pedidos sem desconto e não devem ser removidos.

## Resultado da camada Gold

- 105.000 registros preservados.
- 0 valores nulos nas 14 colunas analíticas.
- 0 registros duplicados.
- Prazo de entrega entre 1 e 28 dias na camada final.
- Avaliações entre 1 e 5.
- Métodos de pagamento padronizados em quatro categorias.
