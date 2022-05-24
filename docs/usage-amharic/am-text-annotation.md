---
sidebar_position: 1
---

# Annotation

Annotating Amharic text is very simple;

- Amharic Document aims to provide access to common text-processing operations through a familiar interface.

- You can simply pass the text to the `Amharic` Document and access all annotations from the returned `Amharic` Document object:
- An `Amharic` Document object holds the annotation of an entire document. It contains a collection of `Sentences` and `AmharicWord`.

## 1. Text Cleaning with Amharic Document

```python
from etnltk import Amharic

sample_text = """
  ሚያዝያ 14፣ 2014 ዓ.ም 🤗 በአገር ደረጃ የሰው ሰራሽ አስተውሎት /Artificial Intelligence/ አሁን ካለበት ዝቅተኛ ደረጃ ወደ ላቀ ደረጃ ለማድረስ፣ ሃገርኛ ቋንቋዎችን ለዓለም ተደራሽ ለማድረግ፣ አገራዊ አቅምን ለማሳደግ እና ተጠቃሚ ለመሆን በጋራ አብሮ መስራቱ እጅግ ጠቃሚ ነው፡፡ 
  
  በማሽን ዓስተምሮ (Machine Learning) አማካኝነት የጽሁፍ ናሙናዎች በአርቲፊሻል ኢንተለጀንስ ሥርዓት ለማሰልጠን፣ የጽሁፍ ዳታን መሰብሰብ እና ማደራጀት፤ የናቹራል ላንጉዌጅ ፕሮሰሲንግ ቱሎችን /Natural Language Processing Tools/ በመጠቀም የጽሁፍ ዳታን ፕሮሰስ ማድረግ ተቀዳሚ እና መሰረታዊ ጉዳይ ነው።
"""

# Annotating Amharic Text
doc = Amharic(sample_text)

# print the `clean` text:
print(doc)
  
# output: Amharic("ሚያዝያ ዓመተ ምህረት በአገር ደረጃ የሰው ሰራሽ አስተውሎት አሁን ካለበት ዝቅተኛ ደረጃ ወደ ላቀ ደረጃ ለማድረስ ሀገርኛ ቋንቋዎችን ለአለም ተደራሽ ለማድረግ አገራዊ አቅምን ለማሳደግ እና ተጠቃሚ ለመሆን በጋራ አብሮ መስራቱ እጅግ ጠቃሚ ነው በማሽን አስተምሮ አማካኝነት የፅሁፍ ናሙናዎች በአርቲፊሻል ኢንተለጀንስ ስርአት ለማሰልጠን የፅሁፍ ዳታን መሰብሰብ እና ማደራጀት የናቹራል ላንጉዌጅ ፕሮሰሲንግ ቱሎችን በመጠቀም የፅሁፍ ዳታን ፕሮሰስ ማድረግ ተቀዳሚ እና መሰረታዊ ጉዳይ ነው")
```

## 2. Sentence Tokenization with Amharic Document

- Within `Amharic` Document, annotations are further stored in `Sentences`
- A `Sentence` object represents a sentence.

```python
from etnltk import Amharic

sample_text = """
የማሽን ለርኒንግ ስልተ-ቀመሮች  (Algorithms) በመጠቀም ቋንቋዎችን መለየት እና መረዳት፣ የጽሁፍ ይዘቶችን መለየት፣ የቋንቋን መዋቅር መተንተን የሚያስችሉ የሃገሪኛ ናቹራል ላንጉዌጅ ፕሮሰሲንግ ቱሎች (NLP tools) ፣ ስልተ-ቀመሮች እና ሞዴሎችን ማዘጋጀት ተገቢ ነው። በዚህም መሰረት አማርኛ፣ አፋን ኦሮሞ፣ ሶማሊኛ እና ትግርኛ ቋንቋዎችን ለማሽን የማስተማር ሂደትን ቀላልና የተቀላተፍ እንዲሆን ያስችላል፡፡
"""

# Annotating Amharic Text
doc = Amharic(sample_text)

# print all list of `Sentence` in a document:
print(doc.sentences)
# output: [Sentence("የማሽን ለርኒንግ ስልተቀመሮች በመጠቀም ቋንቋዎችን መለየት እና መረዳት የፅሁፍ ይዘቶችን መለየት የቋንቋን መዋቅር መተንተን የሚያስችሉ የሀገሪኛ ናቹራል ላንጉዌጅ ፕሮሰሲንግ ቱሎች ስልተቀመሮች እና ሞዴሎችን ማዘጋጀት ተገቢ ነው"), Sentence("በዚህም መሰረት አማርኛ አፋን ኦሮሞ ሶማሊኛ እና ትግርኛ ቋንቋዎችን ለማሽን የማስተማር ሂደትን ቀላልና የተቀላተፍ እንዲሆን ያስችላል")]
```

## 3. Word Tokenization with Amharic Document

- Within `Amharic` Document, annotations are further stored in `AmharicWord`
- A `AmharicWord` object holds a word string

```python
from etnltk import Amharic

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

# Annotating Amharic Text
doc = Amharic(sample_text)

# print all list of `AmharicWord` in a document:
print(doc.words)
# output: ['ተረኛ', 'ተረኛ', 'አለ', 'ነርሱ', 'ወይዘሮ', 'ታሪኳ', 'አቤት', 'ብለው', 'የሁለት', 'አመት', 'ልጃቸውን', 'ይዘው', 'ገቡ', 'ምኑን', 'ነው', 'ያመመው', 'ዶክተሯ', 'ጠየቁ', 'አያዩትም', 'ፀጉሩ', 'ሳስቷል', 'ሆዱ', 'ተነፍቷል', 'ድዱም', 'ይደማል', 'አሉ', 'ወይዘሮ', 'ታሪኳ', 'ዶክተሯም', 'በጣም', 'ያሳዝናል', 'እንደዚህ', 'ያደረገው', 'የተመጣጠነ', 'ምግብ', 'አለማግኘቱ', 'ነው', 'አሁንም', 'ወተት', 'እንቁላል', 'ማር', 'አትክልትና', 'ፍራፍሬ', 'ይመግቡት', 'ቶሎ', 'ይሻለዋል', 'ለአሁኑ', 'ግን', 'መድሀኒት', 'አዝለታለሁ', 'በማለት', 'አስረዷቸው', 'ወይዘሮ', 'ታሪኳም', 'ወይ', 'አለማወቅ', 'ልጄን', 'በምግብ', 'እጥረት', 'ገድዬው', 'ነበር', 'በማለት', 'አለቀሱ']
```

## 4. Remove stopwords with AmharicWord

- Within `Amharic` Document, annotations are further stored in `AmharicWord`
- A `AmharicWord` object holds a word string and `is_stopword` property

```python
from etnltk import Amharic

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

# Annotating Amharic Text
doc = Amharic(sample_text)

# print all list of `AmharicWord` in a document:
print(doc.words)
# output: ['ተረኛ', 'ተረኛ', 'አለ', 'ነርሱ', 'ወይዘሮ', 'ታሪኳ', 'አቤት', 'ብለው', 'የሁለት', 'አመት', 'ልጃቸውን', 'ይዘው', 'ገቡ', 'ምኑን', 'ነው', 'ያመመው', 'ዶክተሯ', 'ጠየቁ', 'አያዩትም', 'ፀጉሩ', 'ሳስቷል', 'ሆዱ', 'ተነፍቷል', 'ድዱም', 'ይደማል', 'አሉ', 'ወይዘሮ', 'ታሪኳ', 'ዶክተሯም', 'በጣም', 'ያሳዝናል', 'እንደዚህ', 'ያደረገው', 'የተመጣጠነ', 'ምግብ', 'አለማግኘቱ', 'ነው', 'አሁንም', 'ወተት', 'እንቁላል', 'ማር', 'አትክልትና', 'ፍራፍሬ', 'ይመግቡት', 'ቶሎ', 'ይሻለዋል', 'ለአሁኑ', 'ግን', 'መድሀኒት', 'አዝለታለሁ', 'በማለት', 'አስረዷቸው', 'ወይዘሮ', 'ታሪኳም', 'ወይ', 'አለማወቅ', 'ልጄን', 'በምግብ', 'እጥረት', 'ገድዬው', 'ነበር', 'በማለት', 'አለቀሱ']

without_stopwords = [word for word in doc.words if not word.is_stopword]

# print all list of `AmharicWord` in a document with out the stop words:
print(without_stopwords)
# output: ['ተረኛ', 'ተረኛ', 'ነርሱ', 'ወይዘሮ', 'ታሪኳ', 'አቤት', 'የሁለት', 'አመት', 'ልጃቸውን', 'ይዘው', 'ገቡ', 'ምኑን', 'ያመመው', 'ዶክተሯ', 'ጠየቁ', 'አያዩትም', 'ፀጉሩ', 'ሳስቷል', 'ሆዱ', 'ተነፍቷል', 'ድዱም', 'ይደማል', 'ወይዘሮ', 'ታሪኳ', 'ዶክተሯም', 'ያሳዝናል', 'ያደረገው', 'የተመጣጠነ', 'ምግብ', 'አለማግኘቱ', 'አሁንም', 'ወተት', 'እንቁላል', 'ማር', 'አትክልትና', 'ፍራፍሬ', 'ይመግቡት', 'ቶሎ', 'ይሻለዋል', 'ለአሁኑ', 'መድሀኒት', 'አዝለታለሁ', 'አስረዷቸው', 'ወይዘሮ', 'ታሪኳም', 'ወይ', 'አለማወቅ', 'ልጄን', 'በምግብ', 'እጥረት', 'ገድዬው', 'አለቀሱ']
```

## 5. Word frequencies using Amharic

- The `word_counts` returns the number of counts of a particular word.

```python
from etnltk import Amharic

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

# Annotating Amharic Text
doc = Amharic(sample_text)

# print all list of `AmharicWord` in a document:
print(doc.words)
# output: ['ተረኛ', 'ተረኛ', 'አለ', 'ነርሱ', 'ወይዘሮ', 'ታሪኳ', 'አቤት', 'ብለው', 'የሁለት', 'አመት', 'ልጃቸውን', 'ይዘው', 'ገቡ', 'ምኑን', 'ነው', 'ያመመው', 'ዶክተሯ', 'ጠየቁ', 'አያዩትም', 'ፀጉሩ', 'ሳስቷል', 'ሆዱ', 'ተነፍቷል', 'ድዱም', 'ይደማል', 'አሉ', 'ወይዘሮ', 'ታሪኳ', 'ዶክተሯም', 'በጣም', 'ያሳዝናል', 'እንደዚህ', 'ያደረገው', 'የተመጣጠነ', 'ምግብ', 'አለማግኘቱ', 'ነው', 'አሁንም', 'ወተት', 'እንቁላል', 'ማር', 'አትክልትና', 'ፍራፍሬ', 'ይመግቡት', 'ቶሎ', 'ይሻለዋል', 'ለአሁኑ', 'ግን', 'መድሀኒት', 'አዝለታለሁ', 'በማለት', 'አስረዷቸው', 'ወይዘሮ', 'ታሪኳም', 'ወይ', 'አለማወቅ', 'ልጄን', 'በምግብ', 'እጥረት', 'ገድዬው', 'ነበር', 'በማለት', 'አለቀሱ']

counts = doc.word_counts['ወይዘሮ']

# print the number of counts
print(counts)
# output: 3
```
