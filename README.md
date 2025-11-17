

# **Book Recommendation System (Collaborative Filtering + SVD)**

This project builds a book recommendation system using popularity-based methods, user-based collaborative filtering, item-based collaborative filtering, and dimensionality reduction using SVD. The system analyzes user–book rating patterns to generate personalized recommendations.

---

## **1. Project Overview**

The goal is to recommend books based on:

* Overall popularity
* User–user similarity
* Item–item similarity
* Latent features learned through **Singular Value Decomposition (SVD)**

Multiple similarity metrics and recommendation strategies were evaluated to determine which produced the most accurate results.

---

## **2. Dataset**

This project uses the **Book-Crossing Dataset**, which contains:

* **Books**: metadata such as title, author, publication year
* **Users**: demographics such as age and location
* **Ratings**: explicit 1–10 user ratings for books

📌 **Note:**
The dataset is **not included in this repository** due to size constraints.
The full dataset can be downloaded from public sources (e.g., Kaggle or official Book-Crossing archive).

The notebook assumes the dataset has been loaded as DataFrames during preprocessing.

---

## **3. Methods**

### **3.1 Popularity-Based Recommender**

* Ranks books by the number of ratings and average rating
* Uses books with **≥ 250 ratings**
* Provides a ranked list of top 50 overall books

---

### **3.2 User-Based Collaborative Filtering**

* Filters users with **≥ 200 ratings** and books with **≥ 50 ratings**
* Computes similarities using:

  * Cosine Similarity
  * Euclidean Distance
* Predicts ratings using weighted ratings from similar users
* Evaluated using **RMSE**

---

### **3.3 Item-Based Collaborative Filtering** *(My contribution)*

* Filters users with **≥ 10 ratings** and books with **≥ 20 ratings**
* Builds a user–item ratings matrix
* Computes **item–item similarity** using Cosine Similarity
* Predicts user ratings from weighted averages of similar items

---

### **3.4 SVD-Based Dimensionality Reduction** *(My contribution)*

* Uses **Truncated SVD** on the item–user matrix
* Reduces dimensionality to latent features
* Reconstructs similarity matrix
* Compares accuracy vs. original item-based CF

---

## **4. Results**

### **RMSE Comparison**

| Method                      | RMSE      |
| --------------------------- | --------- |
| User-Based CF (Cosine)      | **3.898** |
| User-Based CF (Euclidean)   | 3.952     |
| Item-Based CF (No SVD)      | **6.892** |
| Item-Based CF (SVD Reduced) | 7.531     |

### **Insights**

* Cosine Similarity performs best overall
* Item-based collaborative filtering provides strong personalized recommendations
* SVD helps scalability but slightly reduces accuracy

---

## **5. My Contribution**

In this group project, I worked on:

* **Item-based collaborative filtering implementation**
* Computing **Cosine Similarity** for item–item comparisons
* Developing the **rating prediction logic** for item-based CF
* Applying **Truncated SVD** for dimensionality reduction
* Evaluating accuracy (RMSE before/after SVD)
* Writing analysis and technical explanations for these modules

---

## **6. Future Work**

* Add content-based features (genres, authors, embeddings)
* Try demographic-based recommendations
* Use k-NN or clustering for faster nearest-neighbor searches
* Deploy the system as an API or web app
* Explore hybrid recommenders (content + collaborative filtering)

---

## **7. Repository Structure**

```
book-recommender-system/
│
├── book_recommender.ipynb        # Main notebook (preprocessing, CF models, SVD)
└── README.md
```

---

## **8. How to Run**

Install dependencies:

```
pip install pandas numpy scikit-learn
```

Open the notebook:

```
jupyter notebook book_recommender.ipynb
```



---

