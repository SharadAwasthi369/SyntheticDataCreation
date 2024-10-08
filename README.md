
# Product Review Generator using Cohere API

## Overview
This project generates product reviews using the Cohere language model API. The project leverages existing product categories and historical reviews to analyze patterns and create new review texts. The generated reviews are informed by historical data, helping simulate realistic feedback for a given product category.

## Key Steps

### 1. Data Cleansing
- **Category Extraction**: The project extracts unique product category chains from the products dataset. Invalid or missing category entries (e.g., `None` or `NaN`) are removed.
- **Review Data**: Historical review data is cleaned by eliminating missing or invalid reviews to ensure better analysis of patterns.

### 2. Review Pattern Analysis
- Historical review data is analyzed to identify common patterns and structures used by real users.
- The dataset includes columns such as `review_text`, `asin`, `user_id`, `helpful_votes`, etc.

### 3. Review Generation
- Cohere API is used to generate new reviews based on:
  - Product category chains.
  - Common review patterns observed in the dataset.

### 4. Experiments and Results
- `CohereLLM.ipynb`
- Multiple iterations of review generation were conducted, and results were compared against historical reviews for realism and coherence although the hard limit is 1000(`max_reviews`) here in `def generate_reviews(self, products_df: pd.DataFrame, max_reviews: int = 1000) -> pd.DataFrame:`
- `generate_products` is for only product generation not used functionally but can be used as a functionallity for relational database modelling of synthtic data and Testing.
- Insights include the ability of the model to adapt to different product types based on category input and learned patterns.

### 5. Insights
- The generated reviews closely follow real review patterns but may require additional tuning for products in niche categories.
- The structure and length of reviews are adjustable, allowing for flexible use in different contexts.

## Running the Project
To run this project, you will need:
- A valid Cohere API key.
- A dataset of products and historical reviews.

### Instructions
1. Install necessary dependencies:
   ```bash
   %pip install cohere pandas
   ```
2. Set up the environment with your Cohere API key.
3. Run the `LLMReviewGenerator` class to generate reviews.

## Future Work
- Fine-tuning the review generation process for better customization across different categories.
- Exploring additional patterns, such as sentiment analysis, to improve review quality.
- There can be additional ways to solve it as well by using SDV HMDSythesizer, have done some work on it as well refer fileName:`SDVHMA.ipynb`

## Another Experiment
- Have Used SDV Libraries as well in another experiment and they can be used to model multitable scenarios along with relationship intact but takes a lot of time in respect of the time that was available only the script is available
