---
sidebar_position: 5
---

# Functions

Functions and their descriptions are listed below.

## 1. Text preprocessing functions

```python
from etnltk.lang.am import preprocessing
```

| Function | Description |
-----------|-------------|
| remove_whitespaces | Remove extra spaces, tabs, and new lines from a text string
| remove_links | Remove URLs from a text string
| remove_tags | Remove HTML tags from a text string
| remove_emojis | Remove emojis from a text string
| remove_email | Remove email adresses from a text string
| remove_digits | Remove all digits from a text string
| remove_english_chars | Remove ascii characters from a text string
| remove_arabic_chars | Remove arabic characters and numerals from a text string
| remove_chinese_chars | Remove chinese characters from a text string
| remove_ethiopic_digits | Remove all ethiopic digits from a text string
| remove_ethiopic_punct | Remove ethiopic punctuations from a text string
| remove_non_ethiopic | Remove non ethioipc characters from a text string
| remove_stopwords | Remove stop words

## 2. Text normalization functions

```python
from etnltk.lang.am.normalizer import ( 
  normalize_labialized, 
  normalize_shortened,
  normalize_punct,
  normalize_char
)
```

| Function | Description |
-----------|-------------|
| normalize_labialized (e.g., ሞልቱዋል -> ሞልቷል) | labialized character normalization
| normalize_shortened (e.g., አ.አ -> አዲስ አበባ) | short form expansions
| normalize_punct (e.g., :: -> ።) | punctuation normalization
| normalize_char (e.g., ጸሀይ -> ፀሐይ) | character levels normalization

## 3. Text tokenization functions

```python
from etnltk.tokenize.am import (
  sent_tokenize,
  word_tokenize
)
```

| Function | Description |
-----------|-------------|
| sent_tokenize | splits the raw input text into sentences
| word_tokenize | splits the raw input text into word
