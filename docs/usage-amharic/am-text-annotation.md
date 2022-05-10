---
sidebar_position: 1
---

# Annotation

Amharic text preprocessing with **AmharicDocument**

- Preprocessing amharic text is very simple: you can simply pass the text to the AmharicDocument and access all annotations from the returned AmharicDocument object:

## 1. Text Cleaning with AmharicDocument

```python
from etltk import AmharicDocument

sample_text = """
  ሚያዝያ 14፣ 2014 ዓ.ም 🤗 በአገር ደረጃ የሰው ሰራሽ አስተውሎት /Artificial Intelligence/ አሁን ካለበት ዝቅተኛ ደረጃ ወደ ላቀ ደረጃ ለማድረስ፣ ሃገርኛ ቋንቋዎችን ለዓለም ተደራሽ ለማድረግ፣ አገራዊ አቅምን ለማሳደግ እና ተጠቃሚ ለመሆን በጋራ አብሮ መስራቱ እጅግ ጠቃሚ ነው፡፡ 
  
  በማሽን ዓስተምሮ (Machine Learning) አማካኝነት የጽሁፍ ናሙናዎች በአርቲፊሻል ኢንተለጀንስ ሥርዓት ለማሰልጠን፣ የጽሁፍ ዳታን መሰብሰብ እና ማደራጀት፤ የናቹራል ላንጉዌጅ ፕሮሰሲንግ ቱሎችን /Natural Language Processing Tools/ በመጠቀም የጽሁፍ ዳታን ፕሮሰስ ማድረግ ተቀዳሚ እና መሰረታዊ ጉዳይ ነው።
"""

# Annotating Amharic Text
doc = AmharicDocument(sample_text)

# print the `clean` text:
print(doc)
  
# output: AmharicDocument("ሚያዝያ ዓመተ ምህረት በአገር ደረጃ የሰው ሰራሽ አስተውሎት አሁን ካለበት ዝቅተኛ ደረጃ ወደ ላቀ ደረጃ ለማድረስ ሀገርኛ ቋንቋዎችን ለአለም ተደራሽ ለማድረግ አገራዊ አቅምን ለማሳደግ እና ተጠቃሚ ለመሆን በጋራ አብሮ መስራቱ እጅግ ጠቃሚ ነው በማሽን አስተምሮ አማካኝነት የፅሁፍ ናሙናዎች በአርቲፊሻል ኢንተለጀንስ ስርአት ለማሰልጠን የፅሁፍ ዳታን መሰብሰብ እና ማደራጀት የናቹራል ላንጉዌጅ ፕሮሰሲንግ ቱሎችን በመጠቀም የፅሁፍ ዳታን ፕሮሰስ ማድረግ ተቀዳሚ እና መሰረታዊ ጉዳይ ነው")
```

## 2. Sentence Tokenization with AmharicDocument

- Within AmharicDocument, annotations are further stored in `Sentences`

```python
from etltk import AmharicDocument

sample_text = """
የማሽን ለርኒንግ ስልተ-ቀመሮች  (Algorithms) በመጠቀም ቋንቋዎችን መለየት እና መረዳት፣ የጽሁፍ ይዘቶችን መለየት፣ የቋንቋን መዋቅር መተንተን የሚያስችሉ የሃገሪኛ ናቹራል ላንጉዌጅ ፕሮሰሲንግ ቱሎች (NLP tools) ፣ ስልተ-ቀመሮች እና ሞዴሎችን ማዘጋጀት ተገቢ ነው። በዚህም መሰረት አማርኛ፣ አፋን ኦሮሞ፣ ሶማሊኛ እና ትግርኛ ቋንቋዎችን ለማሽን የማስተማር ሂደትን ቀላልና የተቀላተፍ እንዲሆን ያስችላል፡፡
"""

# Annotating Amharic Text
doc = AmharicDocument(sample_text)

# print all list of `Sentence` in a document:
print(doc.sentences)
# output: [Sentence("የማሽን ለርኒንግ ስልተቀመሮች በመጠቀም ቋንቋዎችን መለየት እና መረዳት የፅሁፍ ይዘቶችን መለየት የቋንቋን መዋቅር መተንተን የሚያስችሉ የሀገሪኛ ናቹራል ላንጉዌጅ ፕሮሰሲንግ ቱሎች ስልተቀመሮች እና ሞዴሎችን ማዘጋጀት ተገቢ ነው"), Sentence("በዚህም መሰረት አማርኛ አፋን ኦሮሞ ሶማሊኛ እና ትግርኛ ቋንቋዎችን ለማሽን የማስተማር ሂደትን ቀላልና የተቀላተፍ እንዲሆን ያስችላል")]
```

## 3. Word Tokenization with AmharicDocument

- Within AmharicDocument, annotations are further stored in `Words`

```python
from etltk import AmharicDocument

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
doc = AmharicDocument(sample_text)

# print all `WordList` in a document:
print(doc.words)
# output: WordList(['ተረኛ', 'ተረኛ', 'አለ', 'ነርሱ', 'ወይዘሮ', 'ታሪኳ', 'አቤት', 'ብለው', 'የሁለት', 'አመት', 'ልጃቸውን', 'ይዘው', 'ገቡ', 'ምኑን', 'ነው', 'ያመመው', 'ዶክተሯ', 'ጠየቁ', 'አያዩትም', 'ፀጉሩ', 'ሳስቷል', 'ሆዱ', 'ተነፍቷል', 'ድዱም', 'ይደማል', 'አሉ', 'ወይዘሮ', 'ታሪኳ', 'ዶክተሯም', 'በጣም', 'ያሳዝናል', 'እንደዚህ', 'ያደረገው', 'የተመጣጠነ', 'ምግብ', 'አለማግኘቱ', 'ነው', 'አሁንም', 'ወተት', 'እንቁላል', 'ማር', 'አትክልትና', 'ፍራፍሬ', 'ይመግቡት', 'ቶሎ', 'ይሻለዋል', 'ለአሁኑ', 'ግን', 'መድሀኒት', 'አዝለታለሁ', 'በማለት', 'አስረዷቸው', 'ወይዘሮ', 'ታሪኳም', 'ወይ', 'አለማወቅ', 'ልጄን', 'በምግብ', 'እጥረት', 'ገድዬው', 'ነበር', 'በማለት', 'አለቀሱ'])
```
