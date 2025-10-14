# OPT004-TrabalhoFinal

## Instalar 
pip install pandas duckdb matplotlib scikit-learn

## Informações 
https://sidra.ibge.gov.br/tabela/1612

https://dados.gov.br/dados/conjuntos-dados/pa-producao-agricola-municipal

Os 16 preditores criados e disponíveis para modelagem no arquivo tabela1612_features.csv são:
- ano: O ano da observação.
- valor_total_uf: O valor total da produção agrícola para a Unidade da Federação (UF) naquele ano.
- crescimento_anual_uf: A taxa de crescimento anual do valor total da produção da UF.
- valor_produto_prev_ano: O valor da produção do produto específico na UF no ano anterior (lag de 1 ano).
- participacao_produto_uf: A participação percentual do valor de um produto específico no valor total da produção da UF.
- media_movel_3_anos: A média móvel do valor da produção do produto específico nos últimos 3 anos (lag de 1 ano).
- valor_total_uf_lag1: O valor total da produção da UF no ano anterior (lag de 1 ano).
- crescimento_anual_uf_lag1: A taxa de crescimento anual do valor total da produção da UF no ano anterior (lag de 1 ano).
- local_encoded: A codificação numérica da Unidade da Federação (UF).
- produto_encoded: A codificação numérica do produto agrícola.
- interacao_produto_ano: Uma feature de interação entre o produto codificado e o ano.
- diferenca_media_movel: A diferença entre o valor atual do produto e sua média móvel de 3 anos.
- is_produto_alto_valor: Uma flag binária indicando se o produto é considerado de alto valor (Soja, Milho, Cana-de-açúcar).
- valor_produto_prev_2anos: O valor da produção do produto específico na UF há 2 anos (lag de 2 anos).
- crescimento_produto_anual: A taxa de crescimento anual do valor da produção do produto específico.
- valor_produto_prev_3anos: O valor da produção do produto específico na UF há 3 anos (lag de 3 anos).
