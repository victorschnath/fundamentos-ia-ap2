# Análise de sentimento com PLN

Atividade individual de Fundamentos de Inteligência Artificial.

## Ambiente

Python 3.14.6. As versões das bibliotecas estão em `requirements.txt`.

Para preparar o ambiente no Windows, execute na pasta do projeto:

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
```

## Execução

Na pasta do projeto, execute no Windows:

```powershell
.\.venv\Scripts\python.exe main.py
```

Com o ambiente virtual ativo, use `python main.py`. Em outro ambiente limpo com a mesma versão do Python, instale primeiro as dependências com `python -m pip install -r requirements.txt`.

O programa executa todas as etapas e recria os sete arquivos de `resultados/`. As respostas do relatório devem ser preenchidas em `RELATORIO.md` usando os resultados gerados.

## Método

- Os textos são convertidos para minúsculas e tokenizados mantendo letras acentuadas. Pontuação e números são removidos. A lista própria tem 30 stopwords e preserva a palavra "não".
- Uma divisão estratificada separa 75% das avaliações para treino e 25% para teste, com `random_state=42`.
- A e B mantêm as stopwords; C e D removem. A e C usam Bag of Words; B e D usam TF-IDF. Todas usam regressão logística com `max_iter=1000` e `random_state=42`.
- A validação cruzada usa 5 folds estratificados, com embaralhamento e `random_state=42`, somente no treino. O vetorizador e o classificador ficam em uma `Pipeline`, ajustada novamente dentro de cada fold.
- A escolha usa o maior F1 médio da classe positiva na validação cruzada. Os desempates usam a maior acurácia média e, por último, a ordem A–D. O desvio padrão usa `ddof=0`. O vocabulário registrado é o aprendido no treino completo.
- A configuração escolhida é treinada no conjunto de treino inteiro e avaliada no teste. Os casos difíceis são processados depois e ficam fora do treino e da seleção.

## Arquivos gerados

- `exploracao.txt` — distribuição das classes, tamanho médio dos textos e três exemplos por classe. A contagem usa palavras separadas por espaços em branco nos textos originais.
- `comparacao.csv` — vocabulário, média e desvio padrão da acurácia e do F1 em validação cruzada, nas quatro configurações.
- `matriz_confusao.csv` — linhas com as classes reais e colunas com as previstas, na ordem negativo e positivo.
- `relatorio_classificacao.txt` — configuração escolhida, métricas de teste e relatório por classe.
- `erros.csv` — erros do teste. A coluna `probabilidade` corresponde à classe prevista.
- `palavras_influentes.csv` — dez palavras com os maiores coeficientes positivos e dez com os mais negativos. O sinal é interpretado em relação à classe positiva.
- `casos_dificeis_predicoes.csv` — previsões e probabilidade da classe positiva. Os rótulos esperados "misto" e "neutro" são preservados para análise, embora o modelo só preveja positivo ou negativo.

## Material da atividade

Os dados e o modelo do relatório foram copiados do [repositório da disciplina](https://github.com/paulo-hoff/IAPLN2026-2). O arquivo de avaliações foi salvo como `data/avaliacoes.csv`, seguindo o nome usado no enunciado.
