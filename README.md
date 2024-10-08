
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

## Questions

### 1. Why choose this model?
Used the **Cohere language model** because it’s really good at generating text that sounds human. It takes into account real patterns from existing data, but still adds its own creativity to make each review unique. It can also handle both the structure (like the product details) and the free-form text (the actual review) really well. most importantly its free no credit/debit details paywall.

### 2. What factors were considered when making the dataset?
Here are some of the main things we looked at:
- **Review Length**: wanted reviews that weren’t too long or too short, so we put a limit on how much the model could write.
- **Variety**: generated reviews across a range of product categories to keep things interesting and ensure different types of content.
- **Ratings**: made sure the ratings (e.g., 5 stars) followed a realistic pattern, just like how people rate products in real life.
- **Quality**: The generated reviews had things like helpful votes and whether the product was verified, just like in real reviews.

### 3. How do we know if the dataset is good?
- **Realism**: The reviews should feel like something a real person would write.
- **Diversity**: There should be a good mix of topics and styles so that it doesn’t feel repetitive.
- **Stats**: Can compare things like review lengths and ratings to real data to see if they match up.
- **Model Performance**: If this data is used for training a model, We can see how well the model performs afterward.

### 4. How do we make sure it’s not just copying the real data?
Here’s what to avoid copying:
- **Learning Patterns**: Instead of directly copying reviews, the model learns how reviews are generally written and then creates something new based on that.
- **Randomness**: added some randomness to parts like user IDs and helpful votes, so the dataset isn’t an exact match to the real data.
- **Creative Output**: Using the Cohere model lets us generate new text every time, which keeps things fresh and prevents replication.

### 5. What were the biggest challenges?
- **Making it Real but Different**: It’s tricky to strike a balance between reviews that are realistic and making sure they aren’t too similar to each other.
- **Meaningful Reviews**: Some product categories had less data, so it was harder to generate good reviews for them.
- **Not Overfitting**: To be careful not to directly inject real data to make it more bias towards one way of giving reviews and it just repeats the same patterns.
- **API Limits**: Was free but not sure if can concurrently hit APIs consistently so applied `time.sleep()`

###  The Problem could be done in more ways than imagined like using SDV or some other GAN/VAE techniques that could be implemented for the use case or could use pre implemented libraries and make some moderate modifications.
