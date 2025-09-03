# Amazon Product Recommendation System

## Project Overview
This project develops a recommendation system that suggests products to users based on their past ratings, utilizing the Amazon product reviews dataset. The dataset includes user IDs, product IDs, ratings, and timestamps. The goal is to provide personalized product recommendations using various techniques, including:

- **Rank-Based Recommendation System**: Recommends products based on average ratings and the number of ratings.
- **User-User Collaborative Filtering**: Recommends products based on the preferences of similar users.
- **Item-Item Collaborative Filtering**: Recommends products based on similarities between items.
- **Matrix Factorization (SVD)**: Uses latent factors to provide personalized recommendations.

The project evaluates models using metrics like RMSE, Precision@k, Recall@k, and F1-score@k, with hyperparameter tuning to optimize performance.

## Dataset
The dataset (`ratings_Electronics.csv`) contains:
- **user_id**: Unique identifier for users.
- **prod_id**: Unique identifier for products.
- **rating**: User rating for a product (1 to 5).
- **timestamp**: Time of the rating (not used in this project).

The dataset is filtered to include users with at least 50 ratings and products with at least 5 ratings, resulting in 65,290 rows, 1,540 unique users, and 5,689 unique products.

## Prerequisites
- Python 3.8+
- Google Colab (recommended due to potential issues with the `scikit-surprise` library in Jupyter)
- Required libraries (listed in `requirements.txt`)

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/RashaAbuRkab/amazon-product-recommendation.git
   cd amazon-product-recommendation
   ```
2. Install the required libraries:
   ```bash
   pip install -r requirements.txt
   ```
3. Download the dataset (`ratings_Electronics.csv`) and place it in the project directory.

## Usage
1. Open the notebook `Amazon Product Recommendation System.ipynb` in Google Colab or a compatible environment.
2. Run the cells sequentially to:
   - Load and preprocess the dataset.
   - Perform exploratory data analysis.
   - Build and evaluate the recommendation models (Rank-Based, User-User, Item-Item, and SVD).
   - Tune hyperparameters for collaborative filtering and SVD models.
   - Generate recommendations for specific users.
3. Example commands to generate recommendations:
   ```python
   # Top 5 products with at least 50 interactions (Rank-Based)
   print(*top_n_products(final_rating, 5, 50), sep=', ')

   # Recommendations for a user using optimized SVD
   recommendations = get_recommendations(df_final, "A3LDPF5FMB782Z", 5, svd_algo_optimized)
   print(recommendations)
   ```

## Models and Performance
- **Rank-Based**: Simple but non-personalized, recommends top-rated products with sufficient interactions.
- **User-User Collaborative Filtering**:
  - Baseline RMSE: 1.0260, Precision: 0.844, Recall: 0.862, F1-score: 0.853
  - Optimized RMSE: 0.9759, Precision: 0.834, Recall: 0.896, F1-score: 0.864
- **Item-Item Collaborative Filtering**:
  - Baseline RMSE: 1.0147, Precision: 0.826, Recall: 0.853, F1-score: 0.839
  - Optimized RMSE: 0.9751, Precision: 0.829, Recall: 0.892, F1-score: 0.859
- **SVD (Matrix Factorization)**:
  - Baseline RMSE: 0.9104, Precision: 0.837, Recall: 0.880, F1-score: 0.858
  - Optimized RMSE: 0.9014, Precision: 0.841, Recall: 0.880, F1-score: 0.860

The optimized SVD model performs best, with the lowest RMSE and balanced precision/recall.

## Recommendations
- **Deploy SVD**: Use the optimized SVD model for production due to its superior performance.
- **Enhance with Metadata**: Incorporate product metadata for content-based filtering.
- **Address Cold Start**: Use rank-based recommendations for new users/products.
- **Optimize Scalability**: Implement approximate nearest neighbor techniques for large-scale deployment.
- **Monitor Feedback**: Continuously refine the model based on user feedback.

## Repository Structure
```
amazon-product-recommendation/
├── Amazon Product Recommendation System.ipynb  # Main notebook
├── README.md                         # Project documentation
├── requirements.txt                  # Required libraries
```
