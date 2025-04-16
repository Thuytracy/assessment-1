# Text : Artificial intelligence is growing stronger and stronger, with many applications in life such as medicine, education, transportation, and manufacturing
import matplotlib.pyplot as plt
from collections import Counter
import re
import nltk
from wordcloud import WordCloud

# Make sure you have these:
# pip install nltk wordcloud matplotlib

# Download NLTK resources (only once needed)
nltk.download('punkt')
nltk.download('stopwords')

from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize

# 1. Input Text
text = """
Artificial intelligence is growing stronger and stronger, with many applications in life such as medicine, education, transportation, and manufacturing.
"""

# 2. Preprocess
text = text.lower()
tokens = word_tokenize(text)
words = [word for word in tokens if word.isalpha()]  # Remove punctuation
filtered_words = [word for word in words if word not in stopwords.words('english')]

# 3. Frequency Count
word_counts = Counter(filtered_words)

# 4. Visualization - Bar Chart
plt.figure(figsize=(10, 5))
plt.bar(word_counts.keys(), word_counts.values(), color='skyblue')
plt.title('Word Frequency in Text')
plt.ylabel('Frequency')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# 5. Word Cloud
wordcloud = WordCloud(width=800, height=400, background_color='white').generate_from_frequencies(word_counts)

plt.figure(figsize=(10, 5))
plt.imshow(wordcloud, interpolation='bilinear')
plt.axis('off')
plt.title('Word Cloud of Keywords')
plt.show()
