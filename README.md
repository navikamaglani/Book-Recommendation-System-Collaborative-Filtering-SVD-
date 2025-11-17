
---

# **Book Recommendation System (Collaborative Filtering + SVD)**

This project builds a book recommendation system using multiple machine learning approaches, including popularity-based methods, user-based collaborative filtering, item-based collaborative filtering, and dimensionality reduction using SVD. The system analyzes user–book interactions to generate personalized, data-driven book recommendations.

---

## **1. Project Overview**

The goal is to recommend books based on:

* Overall popularity
* Similarity between users
* Similarity between books
* Latent features extracted using **Singular Value Decomposition (SVD)**

Multiple similarity metrics and matrix decomposition techniques were evaluated to understand which models produce the best recommendations.

---

## **2. Dataset**

The system uses three files from the Book-Crossing dataset:

| File            | Rows      | Columns | Description            |
| --------------- | --------- | ------- | ---------------------- |
| **Books.csv**   | 271,360   | 8       | Book metadata          |
| **Users.csv**   | 278,858   | 3       | User demographics      |
| **Ratings.csv** | 1,149,780 | 3       | User–book interactions |

Key attributes include ISBN, title, author, publication year, user ID, location, age, and rating scores.

---

## **3. Methods**

### **3.1 Popularity-Based Recommender**

* Recommends books with the highest number of ratings
* Filters books with **at least 250 ratings**
* Produces a list of **top 50 popular books**

---

### **3.2 User-Based Collaborative Filtering**

* Keeps users with **≥ 200 ratings**
* Keeps books with **≥ 50 ratings**
* Computes similarity using:

  * Cosine Similarity
  * Euclidean Distance
* Predicts missing ratings using user–user similarity
* Evaluated using **RMSE**

---

### **3.3 Item-Based Collaborative Filtering (Your Contribution)**

* Retains users with **≥ 10 ratings**
* Keeps books with **≥ 20 ratings**
* Builds a **user–item ratings matrix**
* Uses **Cosine Similarity** for item–item comparisons
* Predicts ratings using weighted averages of similar items
* Generates book–book recommendations

---

### **3.4 SVD-Based Dimensionality Reduction (Your Contribution)**

* Applies **Truncated SVD** to reduce matrix dimensionality
* Reconstructs similarity matrix using latent features
* Evaluates the performance trade-offs
* Compares accuracy vs. non–SVD item-based CF

---

## **4. Results**

### **RMSE Comparison**

| Method                      | RMSE      |
| --------------------------- | --------- |
| User-Based CF (Cosine)      | **3.898** |
| User-Based CF (Euclidean)   | 3.952     |
| Item-Based CF (No SVD)      | **6.892** |
| Item-Based CF (SVD Reduced) | 7.531     |

### **Key Insights**

* **Cosine Similarity** outperformed Euclidean Distance
* User-based CF had the highest accuracy but is slow
* Item-based CF produced strong personalized results
* SVD improved scalability but slightly reduced accuracy

---

## **5. My Contribution**

My specific work in this project:

* Developed **item-based collaborative filtering**
* Implemented **Cosine Similarity** for item–item comparisons
* Built the **rating prediction algorithm** for item-based CF
* Applied **Truncated SVD** to reduce matrix sparsity
* Evaluated accuracy before and after dimensionality reduction
* Wrote analysis and technical explanations for these sections

---

## **6. Future Work**

* Integrate book metadata (genres, authors, embeddings)
* Add demographic-aware recommendations
* Use kNN or clustering for faster similarity search
* Deploy as a web app or API
* Explore hybrid recommenders (content + collaborative filtering)

---

## **7. Repository Structure**

```
book-recommender-system/
│
├── book_recommender.ipynb
├── Books.csv
├── Users.csv
├── Ratings.csv
│
└── README.md
```

---

## **8. How to Run**

Install dependencies:

```
pip install pandas numpy scikit-learn
```

Open notebook:

```
jupyter notebook book_recommender.ipynb
```

Run all cells to reproduce the results.

---

