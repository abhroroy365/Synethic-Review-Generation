# Synthetic Review Generation

## Problem
A common challenge in AI tasks like intent detection, sentiment analysis, slot filling, or recommendation algorithms is the limited availability of datasets for model training. The objective of this project is to create synthetic datasets  which can mimic realistic human-written text to aid in training, designing, and evaluating these AI systems. \
Given a large data of real ecommerce reviews, we need to generate synthetic reviews. 
### Dataset

**Amazon reviews dataset**: https://amazon-reviews-2023.github.io/main.html
For fine tuning the model a subset (“Supplements/Vitamins”) of the data has been used. Download link
https://drive.google.com/file/d/1o9IvevRbxKagdE-Op1BJRl8iJUc-0kJ4/view?usp=sharing

### Approach
Pre-trained GPT-2 117M has been fine-tuned on the real reviews. \
•	Number of epochs = 30, time taken: 2 hrs 10 mins (on NVIDIA Tesla P100 GPU) \
•	Few-shot Learning was also used. For every product, we take 2 sample data of the same product title from train data, then make use of it to perform 2-shot prompting. 

## Evaluation
•	Using a classifier to check it it detects synthetic data or not. After generating the synthetic data, we mix it with real data and add label to both real and synthetic data (real = 0, synthetic=1). We train a BERT model to classify them. The results came out that BERT was able to classify them quite well. Thus the synthetic texts were identifiable. \
•	We check the term frequency distribution of both real data and synthetic data. If we check top 10 frequent terms, their distribution is quite similar, not that much though. \
![image](https://github.com/user-attachments/assets/9613a618-7e49-4e69-a3c7-dc107f7c5e7e)

• We also check the semantic similarity. The mean semantic similarity score for real – synthetic is 0.1878. It suggests that synthetic reviews are somewhat similar to real reviews, yet not that much.
![image](https://github.com/user-attachments/assets/d2d64c24-01e4-4ee1-92eb-54f79919ecd4)

**We need to work more on our synthetic data preparation strategy**


### Fine Tuned Model

Fine tuned GPT-2 117M model can be downloaded from the link below. 
https://drive.google.com/file/d/1aNz5GdHRR1fPKhs5pAHxQzqkQlYy88_u/view?usp=sharing
