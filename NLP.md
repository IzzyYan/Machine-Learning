# Word Embeddings
## Vocabulary
1. Tokenization
```python
import tensorflow as tf
tokenizer = tf.keras.preprocessing.text.Tokenizer()
text_corpus = ['bob ate apples, and pears', 'fred ate apples!']
tokenizer.fit_on_texts(text_corpus)
new_texts = ['bob ate pears', 'fred ate pears']
print(tokenizer.texts_to_sequences(new_texts))
print(tokenizer.word_index)
'''
Output
[[3, 1, 5], [6, 1, 5]]
{'ate': 1, 'apples': 2, 'bob': 3, 'and': 4, 'pears': 5, 'fred': 6}
'''
```
texts_to_sequences: 将text转换成降序排列的词序
2. Tokenizer的parameter：
```python
tokenizer = tf.keras.preprocessing.text.Tokenizer(oov_token='OOV'，num_words=2)
```
-   新的text不在corpus里的都放在OOV(out-of-vocabulary)中.
-   num_words: Only use the 100 most frequent words in the vocabulary and filter out the remaining vocabulary words. 常用于词库很大并想提升training speed和避免过拟合.

Tokenization applies to class:
```python
import tensorflow as tf

# Skip-gram embedding model
class EmbeddingModel(object):
    # Model Initialization
    def __init__(self, vocab_size, embedding_dim):
        self.vocab_size = vocab_size
        self.embedding_dim = embedding_dim
        self.tokenizer = tf.keras.preprocessing.text.Tokenizer(num_words=self.vocab_size)

    # Convert a list of text strings into word sequences
    def tokenize_text_corpus(self, texts):
        # CODE HERE
        self.tokenizer.fit_on_texts(texts)
        sequences = self.tokenizer.texts_to_sequences(texts)

        return sequences
```
## Word Embedding
将word转换成数字形式："King" - "Man" + "Woman" = "Queen" 