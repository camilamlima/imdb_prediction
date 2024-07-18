# IMDb Rating Predictor

Este projeto tem como objetivo prever a nota de filmes no IMDb a partir de dados fornecidos. Inclui análise exploratória de dados (EDA), construção de modelos de previsão e salvamento do modelo final.

## Estrutura do Projeto

- `Desafio_Indicium.ipynb`: Notebook contendo a análise exploratória de dados, treinamento e avaliação do modelo de previsão.
- `imdb_rating_predictor.pkl`: Arquivo contendo o modelo treinado.
- `Desafio_Indicium.pdf`: Relatório da análise exploratória de dados.

## Instalação

Para executar este projeto, siga os passos abaixo:

1. Clone este repositório:
    ```bash
    git clone https://github.com/camilamlima/imdb_prediction.git
    cd imdb_prediction
    ```


## Uso

### Análise Exploratória de Dados e Treinamento do Modelo

Abra o notebook `Desafio_Indicium.ipynb` para visualizar a análise exploratória dos dados. Este notebook inclui gráficos e insights sobre as variáveis do dataset. Este notebook inclui a preparação dos dados, treinamento do modelo e avaliação de performance.

### Previsão de Nota do IMDb

Para prever a nota de um filme específico, utilize o modelo salvo `imdb_rating_predictor.pkl`. Veja um exemplo de uso abaixo:

```python
import joblib
import pandas as pd

# Carregar o modelo
model = joblib.load('imdb_rating_predictor.pkl')

# Exemplo de dados de um filme
movie_data = {
    'Series_Title': 'The Shawshank Redemption',
    'Released_Year': '1994',
    'Certificate': 'A',
    'Runtime': '142 min',
    'Genre': 'Drama',
    'Overview': 'Two imprisoned men bond over a number of years, finding solace and eventual redemption through acts of common decency.',
    'Meta_score': 80.0,
    'Director': 'Frank Darabont',
    'Star1': 'Tim Robbins',
    'Star2': 'Morgan Freeman',
    'Star3': 'Bob Gunton',
    'Star4': 'William Sadler',
    'No_of_Votes': 2343110,
    'Gross': '28,341,469'
}

# Transformar dados em DataFrame
movie_df = pd.DataFrame([movie_data])

# Prever a nota do IMDb
predicted_rating = model.predict(movie_df)
print(f'A nota prevista do IMDb é: {predicted_rating[0]}')
