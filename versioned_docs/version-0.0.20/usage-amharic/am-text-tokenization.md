---
sidebar_position: 3
---

# Tokenization

etltk supports **Sentence** and **Word** tokenization.

## 1. Performing sentence tokenization using `sentence_tokenize` function

```python
from etltk.tokenize.am import sent_tokenize

sample_text = """
  የማሽን ለርኒንግ ስልተ-ቀመሮች  (Algorithms) በመጠቀም ቋንቋዎችን መለየት እና መረዳት፣ የጽሁፍ ይዘቶችን መለየት፣ የቋንቋን መዋቅር መተንተን የሚያስችሉ የሃገሪኛ ናቹራል ላንጉዌጅ ፕሮሰሲንግ ቱሎች (NLP tools) ፣ ስልተ-ቀመሮች እና ሞዴሎችን ማዘጋጀት ተገቢ ነው። በዚህም መሰረት አማርኛ፣ አፋን ኦሮሞ፣ ሶማሊኛ እና ትግርኛ ቋንቋዎችን ለማሽን የማስተማር ሂደትን ቀላልና የተቀላተፍ እንዲሆን ያስችላል፡፡
"""

# split into sentences
sentences = sent_tokenize(sample_text)

# print all list of sentence:
print(sentences)
# output: ['የማሽን ለርኒንግ ስልተቀመሮች በመጠቀም ቋንቋዎችን መለየት እና መረዳት የፅሁፍ ይዘቶችን መለየት የቋንቋን መዋቅር መተንተን የሚያስችሉ የሀገሪኛ ናቹራል ላንጉዌጅ ፕሮሰሲንግ ቱሎች ስልተቀመሮች እና ሞዴሎችን ማዘጋጀት ተገቢ ነው', 'በዚህም መሰረት አማርኛ አፋን ኦሮሞ ሶማሊኛ እና ትግርኛ ቋንቋዎችን ለማሽን የማስተማር ሂደትን ቀላልና የተቀላተፍ እንዲሆን ያስችላል']
```

## 2. Performing word tokenization using `word_tokenize` function

```python
from etltk.tokenize.am import word_tokenize

sample_text = """
  “ተረኛ፣ ተረኛ!” አለ ነርሱ። ወይዘሮ
  ታሪኳ፣ “አቤት!” ብለው የሁለት
  ዓመት ልጃቸውን ይዘው ገቡ።
  “ምኑን ነው ያመመው?” ዶክተሯ
  ጠየቁ። “አያዩትም! ፀጉሩ ሳስቷል፤
  ሆዱ ተነፍቷል፤ ድዱም ይደማል”
  አሉ ወይዘሮ ታሪኳ። ዶክተሯም፣
  “በጣም ያሳዝናል፤ እንደዚህ
  ያደረገው የተመጣጠነ ምግብ አለማግኘቱ ነው። አሁንም ወተት፣
  እንቁላል፣ ማር፣ አትክልትና ፍራፍሬ ይመግቡት፤ ቶሎ ይሻለዋል፤
  ለአሁኑ ግን መድኃኒት አዝለታለሁ” በማለት አስረዷቸው። ወይዘሮ
  ታሪኳም “ወይ አለማወቅ! ልጄን በምግብ እጥረት ገድዬው ነበር"
  በማለት አለቀሱ።

"""
  
# split into words
words = word_tokenize(sample_text)

# print all list of word:
print(words)
# output: ['ተረኛ', 'ተረኛ', 'አለ', 'ነርሱ', 'ወይዘሮ', 'ታሪኳ', 'አቤት', 'ብለው', 'የሁለት', 'አመት', 'ልጃቸውን', 'ይዘው', 'ገቡ', 'ምኑን', 'ነው', 'ያመመው', 'ዶክተሯ', 'ጠየቁ', 'አያዩትም', 'ፀጉሩ', 'ሳስቷል', 'ሆዱ', 'ተነፍቷል', 'ድዱም', 'ይደማል', 'አሉ', 'ወይዘሮ', 'ታሪኳ', 'ዶክተሯም', 'በጣም', 'ያሳዝናል', 'እንደዚህ', 'ያደረገው', 'የተመጣጠነ', 'ምግብ', 'አለማግኘቱ', 'ነው', 'አሁንም', 'ወተት', 'እንቁላል', 'ማር', 'አትክልትና', 'ፍራፍሬ', 'ይመግቡት', 'ቶሎ', 'ይሻለዋል', 'ለአሁኑ', 'ግን', 'መድሀኒት', 'አዝለታለሁ', 'በማለት', 'አስረዷቸው', 'ወይዘሮ', 'ታሪኳም', 'ወይ', 'አለማወቅ', 'ልጄን', 'በምግብ', 'እጥረት', 'ገድዬው', 'ነበር', 'በማለት', 'አለቀሱ']
```

### Tokenization API

The complete tokenization API can be found at the following address: [tokenization functions](./functions/#3-text-tokenization-functions)
