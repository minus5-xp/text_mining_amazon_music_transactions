# Text Mining — Amazon Music Reviews

## Descripción
Notebook de análisis de texto sobre reseñas del mercado musical de Amazon (`Music_Market.csv`, 50 000 registros).
Combina **Análisis de Sentimiento** con VADER y **Modelado de Temas** con LDA (Gensim).

---

## Contenido del notebook

### 1. Análisis de Sentimiento — VADER
| Paso | Descripción |
|------|-------------|
| Inicialización | `SentimentIntensityAnalyzer` de `vaderSentiment` |
| Puntuaciones | `pos`, `neg`, `neu` y `compound` (escala −1 a +1) |
| Sensibilidad | Detecta signos de exclamación, emoticonos y mayúsculas |

### 2. Modelado de Temas — LDA

```
Texto crudo
    → Limpieza (lower, regex)
    → Tokenización (NLTK word_tokenize)
    → Eliminación de stopwords
    → Lematización POS-aware (WordNetLemmatizer)
    → Vectorización BoW (CountVectorizer + gensim Sparse2Corpus)
    → Entrenamiento LDA (10 temas, 50 passes)
```

| Parámetro | Valor |
|-----------|-------|
| `num_topics` | 10 |
| `passes` | 50 |
| `num_words` por tema | 4–50 |

### 3. Visualización

| Visualización | Librería |
|---------------|----------|
| Treemap por tema | `squarify` + `matplotlib` |
| Nube de palabras ponderada | `wordcloud` |

---

## Requisitos

```bash
pip install gensim vaderSentiment wordcloud squarify
```

Descargas NLTK:
```python
nltk.download(['punkt', 'stopwords', 'wordnet',
               'averaged_perceptron_tagger',
               'punkt_tab', 'averaged_perceptron_tagger_eng',
               'vader_lexicon'])
```

---

## Dataset

| Campo | Detalle |
|-------|---------|
| Archivo | `Music_Market.csv` |
| Registros | 50 000 |
| Columna | `text` (reseñas de música) |

El CSV **no se incluye** en el repo. Cárgalo desde Drive:
```python
csv_path = "/content/drive/MyDrive/<tu_ruta>/Music_Market.csv"
```

---

## Estructura del repositorio

```
text_mining_amazon_music_transactions/
├── Análisis de Sentimientos y Modelado de Temas Musica Amazon.ipynb
├── README.md
└── .gitignore
```

---

## Autor
**minus5-xp** · [github.com/minus5-xp](https://github.com/minus5-xp)
