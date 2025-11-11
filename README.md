# Estudo Exploratório (AED): Pinguins de Palmer

Este projeto é um exercício de Análise Exploratória de Dados (AED) focado em estatística descritiva (univariada) e análise de relações (bivariada). O objetivo é aplicar conceitos fundamentais de estatística para extrair insights de um conjunto de dados real.

# Objetivos do Estudo

O projeto buscou responder às seguintes perguntas:
- Qual é a composição geral do dataset? (tipos de dados, valores ausentes, distribuição de espécies).
- Quais são as características centrais e a dispersão das medidas numéricas (massa, comprimento da nadadeira, etc.)?
- Existem correlações lineares fortes entre as medidas corporais dos pinguins?
- Como as medidas corporais (ex: comprimento do bico) diferem entre as diferentes espécies?
- Como as espécies estão distribuídas geograficamente entre as ilhas?

# O Conjunto de Dados

Foi utilizado o dataset "Palmer Penguins", disponibilizado originalmente pela Dr. Kristen Gorman e o Palmer LTER.
Os dados foram carregados diretamente através da biblioteca seaborn (sns.load_dataset("penguins")).
O dataset contém 344 observações de 3 espécies diferentes de pinguins, com as seguintes variáveis principais:
- species: A espécie do pinguim (Adelie, Chinstrap, Gentoo).
- island: Ilha onde o pinguim foi observado (Torgersen, Biscoe, Dream).
- bill_length_mm: Comprimento do bico (em mm).
- bill_depth_mm: Profundidade do bico (em mm).
- flipper_length_mm: Comprimento da nadadeira (em mm).
- body_mass_g: Massa corporal (em g).
- sex: Sexo do pinguim.

Pré-processamento: Linhas com valores ausentes (NaN) foram removidas usando .dropna() para garantir a precisão das análises estatísticas subsequentes, resultando em 333 observações completas.

# Metodologia e Ferramentas

O projeto foi desenvolvido inteiramente em Python dentro de um ambiente Jupyter Notebook.
As principais bibliotecas utilizadas foram:
- Pandas: Para manipulação e agregação dos dados (ex: .describe(), .groupby(), .corr(), .crosstab()).
- Matplotlib & Seaborn: Para a geração de todas as visualizações (ex: histplot, boxplot, scatterplot, heatmap, countplot).
- Numpy: Para suporte a operações numéricas.

# Principais Descobertas (Insights)

A análise exploratória revelou diversos padrões interessantes:
- Correlação Forte (Numérico-Numérico): Existe uma correlação linear positiva muito forte (r = 0.87) entre o flipper_length_mm (comprimento da nadadeira) e o body_mass_g (massa corporal). Pinguins com nadadeiras maiores tendem a ser significativamente mais pesados.
- Mistério Bimodal Resolvido (Categórico-Numérico): Uma análise inicial (univariada) do bill_length_mm (comprimento do bico) mostrou uma distribuição bimodal (com dois picos). A análise bivariada (usando boxplot agrupado por species) resolveu o mistério: a espécie Adelie tem bicos significativamente mais curtos (mediana ~39mm) do que as espécies Gentoo e Chinstrap (medianas ~47-49mm).
- Relação Fraca (Numérico-Numérico): A suspeita de que bicos mais longos (bill_length_mm) seriam menos profundos (bill_depth_mm) foi investigada. A correlação geral é negativa, porém muito fraca (r = -0.23), indicando que essa não é uma relação forte quando o dataset é analisado como um todo. Além disso, aprofundando no Scatterplot e adicionando a variável species ao scatterplot (usando o parâmetro hue), verificou-se inclusive que dentro de cada espécie parece haver uma correlação positiva entre "bill_length_mm" e "bill_depth_mm", mostrando que, analisando espécie por espécie, os bicos mais longos tendem a ser mais profundos.
- Distribuição Geográfica (Categórico-Categórico): As espécies não estão distribuídas aleatoriamente. Um countplot (gráfico de contagem) mostrou que a ilha Torgersen é habitada exclusivamente pela espécie Adelie, enquanto a ilha Biscoe é a única que abriga a espécie Gentoo.