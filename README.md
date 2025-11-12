# OPT004-TrabalhoFinal

## Instalar 
pip install pandas duckdb matplotlib scikit-learn

## Informações 
https://sidra.ibge.gov.br/tabela/1612

https://dados.gov.br/dados/conjuntos-dados/pa-producao-agricola-municipal

https://ftp.ibge.gov.br/Pib_Municipios/


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

## Perguntas de Pesquisa 

**1. Qual a probabilidade de uma Unidade da Federação (UF) apresentar um crescimento anual no valor total da produção agrícola acima da média nacional, considerando seus dados históricos de produção e o tipo de produto predominante?**

Explicação: Esta pergunta busca entender se é possível prever o desempenho de uma UF em relação à média do país. Ela transforma o problema em uma tarefa de classificação. O objetivo é construir um modelo que, dadas as características de uma UF (histórico de produção, produtos cultivados, etc.), possa classificar se ela terá um crescimento acima ou abaixo da média nacional no próximo ano. Isso é fundamental para identificar UFs com potencial de alto crescimento ou aquelas que podem precisar de intervenção.
**2. Quais fatores (como tipo de produto, região, e valor da produção em anos anteriores) são os mais influentes na previsão do valor da produção agrícola de uma UF para o ano seguinte?**

Explicação: Esta pergunta foca na identificação das variáveis mais importantes para prever o valor exato da produção agrícola. Isso a caracteriza como um problema de regressão. Ao responder a esta pergunta, o objetivo é desenvolver um modelo que possa estimar o valor da produção futura e, mais importante, entender quais dos preditores (as features que criamos, como valor_produto_prev_ano, crescimento_anual_uf, participacao_produto_uf, etc.) têm o maior impacto nessa previsão. Isso oferece insights sobre os impulsionadores econômicos da produção agrícola.


## Hipóteses Testáveis 

- **H1 (Classificação)**: Unidades da Federação com maior diversidade de produtos agrícolas e um histórico de crescimento consistente terão uma probabilidade significativamente maior de superar a média nacional de crescimento anual no valor da produção agrícola.
Explicação: Esta hipótese sugere que a diversidade de produtos e a consistência no crescimento passado são indicadores-chave para prever um desempenho superior de uma UF. Para testá-la, o modelo de classificação (da Pergunta 1) precisaria mostrar que features relacionadas à diversidade de produtos (que poderiam ser criadas, como um índice de diversidade) e ao histórico de crescimento (crescimento_anual_uf_lag1) são preditores importantes e que sua presença aumenta a acurácia da previsão de crescimento acima da média.

- **H2 (Regressão)**: Features que representam o valor da produção de produtos-chave (soja, milho, cana-de-açúcar) em anos anteriores, juntamente com a região geográfica da UF, apresentarão uma performance superior na previsão do valor total da produção agrícola para o ano seguinte, em comparação com modelos que utilizam apenas dados agregados.
Explicação: Esta hipótese postula que a granularidade dos dados (valores de produtos específicos e a localização geográfica) é mais eficaz para a previsão do valor total da produção do que apenas dados gerais. Para testá-la, o modelo de regressão (da Pergunta 2) precisaria demonstrar que preditores como valor_produto_prev_ano (para produtos-chave), is_produto_alto_valor, e local_encoded (que representa a região) contribuem significativamente para a precisão da previsão do valor da produção do ano seguinte, superando modelos mais simples.

- **H3 (Feature Engineering)**: A criação de features como a taxa de variação anual do valor da produção por produto/UF e a participação percentual de cada produto no valor total da UF aumentará o número de preditores para mais de 15 e melhorará a capacidade preditiva dos modelos de classificação e regressão.
Explicação: Esta hipótese aborda diretamente a importância do Feature Engineering (engenharia de características). Ela afirma que as novas variáveis que criamos (crescimento_produto_anual, participacao_produto_uf, media_movel_3_anos, etc.) não apenas cumprem o requisito de ter mais de 15 preditores, mas também são cruciais para aprimorar o desempenho dos modelos preditivos. Para testá-la, seria necessário comparar o desempenho dos modelos com e sem essas features, esperando que as features engenheiradas resultem em modelos mais precisos e robustos.
Essas perguntas e hipóteses fornecem um roteiro claro para as próximas etapas do seu projeto, guiando a seleção de modelos, a avaliação de desempenho e a interpretação dos resultados.

