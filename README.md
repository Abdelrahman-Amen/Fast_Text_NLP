# FastText Overview 🌴
FastText is a word embedding technique developed by Facebook AI Research (FAIR) that builds on top of popular models like Word2Vec but with improvements. While Word2Vec uses fixed-sized vectors for each word, FastText breaks words into subword n-grams (character-based components) and then represents a word as the sum of its subword embeddings. This makes FastText particularly effective at handling rare words, misspellings, and morphologically rich languages, as it considers parts of words rather than only whole words.
![12](https://github.com/user-attachments/assets/6988aba8-d955-4937-a5f0-a65b210eaadc)




## FastText is used for efficient learning of word representations and sentence classification.

![1](https://github.com/user-attachments/assets/473b54f9-c648-431a-9251-8e3baa764bd2)




# Advantages of FastText:
## 1. Handling Rare and Out-of-Vocabulary (OOV) Words:

   ● FastText can handle rare and unseen words by breaking them into subwords. Unlike traditional models where OOV words are ignored, FastText can infer meanings from subword patterns.

## 2. Morphology-Aware:

   ● For languages with rich morphology (e.g., conjugations or compound words), FastText performs better than Word2Vec, as it captures internal word structure.

## 3. Pre-trained Embeddings:

   ● FastText provides pre-trained word vectors for 157 languages, making it easy to use for multilingual projects and text processing tasks.

## 4. Speed and Scalability:

   ● FastText can train models quickly and efficiently, even on large datasets.

# CBOW, Skip-Gram, and FastText:
## CBOW (Continuous Bag of Words):

   ● CBOW predicts the target word from its surrounding context. It averages the context words and tries to predict the central word. This method is faster because it 
    reduces multiple words into a single prediction task.
## Skip-Gram:

  ● Skip-gram does the opposite of CBOW—it predicts surrounding context words from a single target word. This method works well with smaller datasets and rare words 
    because it explicitly focuses on the target word and its neighbors.
## FastText vs. CBOW and Skip-Gram:

●   Unlike CBOW and Skip-gram, which treat words as atomic entities, FastText works with subword n-grams. While CBOW and Skip-gram fail with OOV words, FastText 
    remains effective, thanks to its subword-level understanding.

![50](https://github.com/user-attachments/assets/4b4b5c74-bef0-45b0-8284-514d1c75fe5a)


    
# FastText vs. Stemming vs. Lemmatization:
## Stemming:

  ● Stemming reduces a word to its base or root form, often chopping off endings without considering grammar rules (e.g., "running" to "run"). This is a more 
     aggressive approach, and it may lead to the loss of some meaning in the text.

     
## Lemmatization:

●      Lemmatization is a more refined version of stemming, as it uses a vocabulary and morphological analysis of words to return the base or dictionary form (lemma) 
      of a word. For example, "better" becomes "good," which is more accurate than stemming.

![20](https://github.com/user-attachments/assets/6f308a20-f542-4e4c-bf3c-f7180ea8d307)

## FastText:

● FastText doesn't directly deal with stemming or lemmatization. Instead, it breaks words into subword n-grams. So, it doesn't need explicit stemming or lemmatization since the subword embeddings capture multiple forms of words inherently.



# Training a FastText Model with Gensim vs. Using a Pre-trained FastText Model from Facebook


## Training with Gensim:
When you train a FastText model using Gensim, you tailor the model specifically to your dataset. This custom training allows you to adjust various parameters like vector size, window size (the context around a word), and subword n-grams (breaking down words into smaller chunks), which is essential for capturing relationships between rare words or misspellings. For example, you can train a FastText model on medical or technical text where domain-specific terms might not be present in general-purpose models. This training ensures that your model learns the nuances of your data, potentially improving performance on specialized tasks.

![2](https://github.com/user-attachments/assets/463e7023-5651-4484-8c0a-a74b6cd1c199)
![3](https://github.com/user-attachments/assets/a0834b09-67d1-4faa-a8fb-52229d94f1f9)


## Advantages of Custom Training:
● Domain-Specific Data: If you're working with a specialized dataset, like legal documents or biomedical research, the model can learn to represent uncommon terms better than a general pre-trained model.

● Fine-Tuned Parameters: Custom training allows you to adjust the model for optimal performance, tuning factors like the size of word vectors and how far the model looks into the word’s context.

● Control Over Vocabulary: You control the frequency threshold (e.g., how often a word needs to appear in the text) to include rare or highly specialized words, which may be ignored in pre-trained models.

## Using Pre-trained FastText Models (Facebook):
Facebook provides pre-trained FastText models that have been trained on large datasets like Wikipedia, Common Crawl, or other general corpora. These models are widely available for many languages, including English, and they are pre-built to represent the structure of common words effectively.

![33](https://github.com/user-attachments/assets/9c9ac040-b351-4ba4-8365-15d326c494a2)

![4](https://github.com/user-attachments/assets/57e93eee-b46a-4cce-8a4b-a0a8d8565b1b)

Pre-trained models can be loaded quickly and are especially helpful when time or computational resources are limited. Since they’ve already been trained on large corpora, they come with rich word embeddings that capture semantic relationships between words. This is particularly useful for common tasks like sentiment analysis, topic modeling, or even machine translation, where general language understanding is sufficient.



## Advantages of Using Pre-trained Models:
● Instant Deployment: Since these models are already trained, you can quickly load them and start using them without spending time or resources on training.

● Large Corpus Knowledge: Pre-trained models are built on huge datasets, which helps in learning robust word relationships, including for uncommon words that are still present in the general language.

● Sufficient for Common Languages: If your task involves a well-resourced language like English, pre-trained models usually perform well for a variety of tasks without the need for further customization.

## When to Use Pre-trained Models:
● General-Purpose Applications: If your task involves common language (e.g., English or French) and general text analysis, pre-trained FastText models will likely suffice. They’re a great starting point when working with tasks like sentiment analysis, text classification, or even machine translation for widely-used languages.

● Limited Resources: Pre-trained models are ideal if you don't have the computational resources to train a model from scratch or if you're working under tight time constraints.

● Broad Language Tasks: If your task involves everyday language or conversational text, the pre-trained models will likely cover a broad spectrum of words and phrases.


## When to Train a Custom FastText Model:
● Domain-Specific Tasks: If your dataset involves highly specialized or technical language (e.g., legal, medical, or scientific), a custom model trained on your specific text will likely yield better embeddings. This is because pre-trained models might not capture rare or context-specific terms effectively.

● Niche Languages or Low-Resource Languages: For languages or dialects that don’t have much representation in pre-trained models, or for very specialized subfields, training your own FastText model ensures that you can handle rare or unknown words.

● Customization of Parameters: If you need to experiment with different hyperparameters to optimize the model for your specific use case, custom training is essential.

# PDF Report and Tabulate Usage:

I make use of Tabulate to create formatted tables of similar and dissimilar (opposite) words based on the FastText model. The results for each word's similarity and dissimilarity are displayed in a well-structured table format, which enhances readability and can be easily exported to different formats.

FPDF is then used to generate a PDF report from these tables. For each word analyzed, the similar and dissimilar word tables are added to a chapter in the PDF. Here's how the process is handled:

● Header and Title: Each page in the PDF starts with a consistent header and the chapter title, specifying which word is being analyzed.

● Content: For each word, the analysis (similar and opposite words) is printed in table format. Tabulate ensures the data is formatted well before embedding it into the PDF.

● Multiple Chapters: Each word is treated as a separate chapter in the PDF, making it easy to navigate and understand the similarity and dissimilarity analysis.

# Why Use Tabulate and PDF:
● Tabulate: It offers a clean and readable format to display word similarity analysis results, enhancing the understanding of model outputs.

● FPDF: Automates the generation of PDF reports, useful for sharing analysis results with others in a professional format.

# Summary:
● Pre-trained FastText models from Facebook are powerful and ready-to-use for general language tasks. They are ideal when working with common languages or when you need a quick, efficient solution without extensive training.


● Training your own FastText model with Gensim is more appropriate for specialized or niche tasks, giving you the flexibility to control the training process, especially when dealing with domain-specific data or languages that aren’t well-represented in pre-trained corpora.
