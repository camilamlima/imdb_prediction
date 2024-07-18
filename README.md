# IMDb Rating Predictor

Este projeto tem como objetivo prever a nota de filmes no IMDb a partir de dados fornecidos. Inclui análise exploratória de dados (EDA), construção de modelos de previsão e salvamento do modelo final.

## Estrutura do Projeto

- `EDA_analysis.ipynb`: Notebook contendo a análise exploratória de dados.
- `model_training.ipynb`: Notebook contendo o treinamento e avaliação do modelo de previsão.
- `imdb_rating_predictor.pkl`: Arquivo contendo o modelo treinado.
- `requirements.txt`: Lista de pacotes e versões necessários para rodar o projeto.
- `reports/EDA_report.pdf`: Relatório da análise exploratória de dados.

## Instalação

Para executar este projeto, siga os passos abaixo:

1. Clone este repositório:
    ```bash
    git clone https://github.com/seu-usuario/imdb-rating-predictor.git
    cd imdb-rating-predictor
    ```

2. Crie um ambiente virtual:
    ```bash
    python -m venv venv
    source venv/bin/activate  # No Windows use `venv\Scripts\activate`
    ```

3. Instale as dependências:
    ```bash
    pip install -r requirements.txt
    ```

## Uso

### Análise Exploratória de Dados

Abra o notebook `EDA_analysis.ipynb` para visualizar a análise exploratória dos dados. Este notebook inclui gráficos e insights sobre as variáveis do dataset.

### Treinamento do Modelo

Para treinar e avaliar o modelo de previsão, abra e execute o notebook `model_training.ipynb`. Este notebook inclui a preparação dos dados, treinamento do modelo e avaliação de performance.

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
