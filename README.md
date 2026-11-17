# Análise de sentimento com PLN

Atividade individual de Fundamentos de Inteligência Artificial.

## Ambiente

Python 3.14.6. As versões das bibliotecas estão em `requirements.txt`.

Para preparar o ambiente no Windows, execute na pasta do projeto:

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
```

## Desenvolvimento

A etapa de exploração dos dados está implementada. Ela gera `resultados/exploracao.txt` com o total de avaliações, a distribuição das classes, o tamanho médio dos textos em palavras e três exemplos de cada classe.

Para executar no Windows:

```powershell
.\.venv\Scripts\python.exe main.py
```

Com o ambiente virtual ativo, o comando equivalente é `python main.py`. O arquivo de exploração é gerado novamente a cada execução.

Os módulos ficam em `src/`, e as respostas devem ser preenchidas em `RELATORIO.md`.

## Material da atividade

Os dados e o modelo do relatório foram copiados do [repositório da disciplina](https://github.com/paulo-hoff/IAPLN2026-2). O arquivo de avaliações foi salvo como `data/avaliacoes.csv`, seguindo o nome usado no enunciado.
