---
sidebar_position: 2
---

# Preprocessing

Performing text cleaning using `clean_amharic` function and `preprocessing` module:

- it provides a solid pipeline to clean and represent text data.

## 1. Text Cleaning using `clean_amharic` function
  
```python
from etltk.lang.am import clean_amharic

sample_text = """
  ሚያዝያ 14፣ 2014 ዓ.ም 🤗 በአገር ደረጃ የሰው ሰራሽ አስተውሎት /Artificial Intelligence/ አሁን ካለበት ዝቅተኛ ደረጃ ወደ ላቀ ደረጃ ለማድረስ፣ ሃገርኛ ቋንቋዎችን ለዓለም ተደራሽ ለማድረግ፣ አገራዊ አቅምን ለማሳደግ እና ተጠቃሚ ለመሆን በጋራ አብሮ መስራቱ እጅግ ጠቃሚ ነው፡፡

  በማሽን ዓስተምሮ (Machine Learning) አማካኝነት የጽሁፍ ናሙናዎች በአርቲፊሻል ኢንተለጀንስ ሥርዓት ለማሰልጠን፣ የጽሁፍ ዳታን መሰብሰብ እና ማደራጀት፤ የናቹራል ላንጉዌጅ ፕሮሰሲንግ ቱሎችን /Natural Language Processing Tools/ በመጠቀም የጽሁፍ ዳታን ፕሮሰስ ማድረግ ተቀዳሚ እና መሰረታዊ ጉዳይ ነው።
"""

# `clean_amharic` function uses the default pipeline to clean text
cleaned = clean_amharic(input_text)

# print the `clean` text:
print(cleaned)
# output: ሚያዝያ ዓመተ ምህረት በአገር ደረጃ የሰው ሰራሽ አስተውሎት አሁን ካለበት ዝቅተኛ ደረጃ ወደ ላቀ ደረጃ ለማድረስ ሀገርኛ ቋንቋዎችን ለአለም ተደራሽ ለማድረግ አገራዊ አቅምን ለማሳደግ እና ተጠቃሚ ለመሆን በጋራ አብሮ መስራቱ እጅግ ጠቃሚ ነው በማሽን አስተምሮ አማካኝነት የፅሁፍ ናሙናዎች በአርቲፊሻል ኢንተለጀንስ ስርአት ለማሰልጠን የፅሁፍ ዳታን መሰብሰብ እና ማደራጀት የናቹራል ላንጉዌጅ ፕሮሰሲንግ ቱሎችን በመጠቀም የፅሁፍ ዳታን ፕሮሰስ ማድረግ ተቀዳሚ እና መሰረታዊ ጉዳይ ነው
```

The default pipeline for the `clean_amharic` method is the following:

1. `remove_links()` Replace all URLs.
2. `remove_tags()` Lowercase all HTML tags.
3. `remove_emojis()` Remove all emojis.
4. `remove_special_characters()` Remove all special characters (å¼«¥ª°©ð±§µæ¹¢³¿®ä£"”“`‘´’‚,„»«「」『』（）〔〕【】《》〈〉).
5. `remove_digits()` Remove all blocks of digits.
6. `remove_ethiopic_digits()` Remove ethiopic number.
7. `remove_english_chars()` Remove all english characters.
8. `remove_arabic_chars()` Remove all arabic characters.
9. `remove_chinese_chars()` Remove all chinese characters.
10. `normalize_punct()` Normalizes ethiopic punctuations.
11. `normalize_shortened()` Expands all short form.
12. `remove_punct()` Remove all string.punctuation and ethiopic punctuations (፠ ፡ ። ፣ ፤ ፥ ፦ ፧ ፨).
13. `remove_whitespaces()` Remove all white space between words.

## 2. Text Cleaning using a custom pipeline as argument to clean

- We can also pass a custom pipeline as argument to `clean_amharic` function

```python
from etltk.lang.am import (
  preprocessing,
  clean_amharic
)

sample_text = """
  ሚያዝያ 14፣ 2014 ዓ.ም 🤗 በአገር ደረጃ የሰው ሰራሽ አስተውሎት /Artificial Intelligence/ አሁን ካለበት ዝቅተኛ ደረጃ ወደ ላቀ ደረጃ ለማድረስ፣ ሃገርኛ ቋንቋዎችን ለዓለም ተደራሽ ለማድረግ፣ አገራዊ አቅምን ለማሳደግ እና ተጠቃሚ ለመሆን በጋራ አብሮ መስራቱ እጅግ ጠቃሚ ነው፡፡

  በማሽን ዓስተምሮ (Machine Learning) አማካኝነት የጽሁፍ ናሙናዎች በአርቲፊሻል ኢንተለጀንስ ሥርዓት ለማሰልጠን፣ የጽሁፍ ዳታን መሰብሰብ እና ማደራጀት፤ የናቹራል ላንጉዌጅ ፕሮሰሲንግ ቱሎችን /Natural Language Processing Tools/ በመጠቀም የጽሁፍ ዳታን ፕሮሰስ ማድረግ ተቀዳሚ እና መሰረታዊ ጉዳይ ነው።
"""

# Define a custom preprocessor pipeline
custom_pipeline = [
  preprocessing.remove_emojis, 
  preprocessing.remove_digits,
  preprocessing.remove_ethiopic_punct,
  preprocessing.remove_english_chars, 
  preprocessing.remove_punct
]

# `clean_amharic` function takes a custom pipeline, if not uses the default pipeline
cleaned = clean_amharic(input_text, abbrev=False, pipeline=custom_pipeline)
# print the `clean` text:
print(cleaned)
# output: ሚያዝያ ዓመተ ምህረት በአገር ደረጃ የሰው ሰራሽ አስተውሎት አሁን ካለበት ዝቅተኛ ደረጃ ወደ ላቀ ደረጃ ለማድረስ ሀገርኛ ቋንቋዎችን ለአለም ተደራሽ ለማድረግ አገራዊ አቅምን ለማሳደግ እና ተጠቃሚ ለመሆን በጋራ አብሮ መስራቱ እጅግ ጠቃሚ ነው በማሽን አስተምሮ አማካኝነት የፅሁፍ ናሙናዎች በአርቲፊሻል ኢንተለጀንስ ስርአት ለማሰልጠን የፅሁፍ ዳታን መሰብሰብ እና ማደራጀት የናቹራል ላንጉዌጅ ፕሮሰሲንግ ቱሎችን በመጠቀም የፅሁፍ ዳታን ፕሮሰስ ማድረግ ተቀዳሚ እና መሰረታዊ ጉዳይ ነው
```

### Preprocessing API

The complete preprocessing API can be found at the following address: [preprocessing functions](./functions/#1-text-preprocessing-functions)
