<h1 align="center">🍿 Movie Recommendation System 🎥</h1>

<p align="center">
  <img src="https://media.giphy.com/media/WoD6JZnwap6s8/giphy.gif" width="180" />
</p>

<p align="center">
  <b>An intelligent, content-based engine that helps you discover your next favorite movie</b> <br>
  Built with 💡 <b>Python, Pandas, Scikit-learn, TMDB API</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.9-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/ML-Scikit--Learn-yellow?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Engine-Cosine%20Similarity-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge" />
</p>

---

## ✨ Features

✨ Recommends top 5 similar movies  
🔍 Uses **cosine similarity** on movie metadata (genres, cast, keywords)  
🎞️ Fetches movie posters using **TMDB API**  
🧠 Powered by **NLP-based vectorization** (TF-IDF/CountVectorizer)  
📦 Efficient & production-ready code with modular design

---

## 📂 Folder Structure


> 💡 *Organized for reproducibility and easy extension*

---

## 📥 Sample Input

> 🎦 **Selected Movie:** `The Dark Knight (2008)`

## 📤 Output Recommendations

| 🔢 Rank | 🎬 Movie              |
|--------|-----------------------|
| 1️⃣     | Batman Begins         |
| 2️⃣     | The Dark Knight Rises |
| 3️⃣     | Man of Steel          |
| 4️⃣     | Watchmen              |
| 5️⃣     | Iron Man              |

> 🖼️ Posters fetched using movie ID via TMDB API.

---

## 🧠 How It Works

<p align="center">
  <img src="https://media.giphy.com/media/26n6WywJyh39n1pBu/giphy.gif" width="600" />
</p>

1. Combine movie metadata: genres, keywords, cast, crew  
2. Vectorize using `CountVectorizer`  
3. Compute **cosine similarity matrix**  
4. Recommend 5 closest matches

---

## 🧾 Code Logic (Snippet)

```python
def recommend(movie):
    index = movies[movies['title'] == movie].index[0]
    distances = sorted(
        list(enumerate(similarity[index])),
        reverse=True, key=lambda x: x[1]
    )
    recommendations = []
    for i in distances[1:6]:
        movie_id = movies.iloc[i[0]].movie_id
        poster = fetch_poster(movie_id)
        recommendations.append((movies.iloc[i[0]].title, poster))
    return recommendations


