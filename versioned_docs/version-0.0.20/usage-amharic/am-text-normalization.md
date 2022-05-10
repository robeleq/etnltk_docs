---
sidebar_position: 3
---

# Normalization

etltk supports Character Level, Labialized, Punctuation and Short Form Expansion.

- Character Level Normalization such as "`ጸ`ሀይ" and "`ፀ`ሐይ"
- Labialized Character Normalzation such as "ሞል`ቱዋ`ል" to "ሞል`ቷ`ል"
- Short Form Expansion such as "`አ.አ`" to "`አዲስ አበባ`"
- Punctuation Normalization such as `::` to `።`

## 1. Performing normalization using `normalize` function

```python
from etltk.lang.am import normalize

sample_text = """
  ሚያዝያ 14፣ 2014 ዓ.ም በዓገር ደረጃ የሰው ሰራሽ አስተውሎት የውይይት መድረክ ላይ
  የሃገርኛ ቋንቋዎች ትርጉም አገልግሎት፣ 
  ቻትቦት (የውይይት መለዋወጫ ሮቦት): 
  የፅሁፍ ሰነዶች ለመለየት፣ የቃላት ትክክለኛነትን ለማረጋገጥ፣ 
  በቋንቋን ሕግጋት መሠረት ጽሑፎችን ለማዋቀር እና ለመመስረት፣ 
  ረጅም ጽሁፎችን ለማሳጠር፣ አንኳር ጉዳዮችን መለየት ወይም ጥቅል ሃሳብ ለማውጣት፣ 
  ንግግርን ወደ ጽሁፍ ለመቀየር የሚያስችሉ መተግበሪያዎችን ማልማት አስረላጊነቱ ተገልጹዋል::
"""

# normalization
normalized_text = normalize(sample_text)

# The following example shows how to print all normalized in a document:
print(normalized_text)
# output: ሚያዝያ 14፣ 2014 አመተ ምህረት በአገር ደረጃ የሰው ሰራሽ አስተውሎት የውይይት መድረክ ላይ
# የሀገርኛ ቋንቋዎች ትርጉም አገልግሎት፣ 
# ቻትቦት (የውይይት መለዋወጫ ሮቦት)፡ 
# የፅሁፍ ሰነዶች ለመለየት፣ የቃላት ትክክለኛነትን ለማረጋገጥ፣ 
# በቋንቋን ህግጋት መሰረት ፅሁፎችን ለማዋቀር እና ለመመስረት፣ 
# ረጅም ፅሁፎችን ለማሳጠር፣ አንኳር ጉዳዮችን መለየት ወይም ጥቅል ሀሳብ ለማውጣት፣ 
# ንግግርን ወደ ፅሁፍ ለመቀየር የሚያስችሉ መተግበሪያዎችን ማልማት አስረላጊነቱ ተገልጿል።
```

The default pipeline for the `normalize` method is the following:

1. `normalize_labialized()` Labialized character normalzation such as ሞልቱዋል to ሞልቷል
2. `normalize_shortened()` Short form expansion such as ጠ/ሚ to ጠቅላይ ሚኒስተር
3. `normalize_punct()` Punctuation normalization such as :: to ።
4. `normalize_char()` Character level normalization such as ጸሀይ and ፀሐይ
  
## 2. Performing normalization using `normalize_char`, `normalize_punct`, `normalize_labialized`, `normalize_shortened` functions

```python
from etltk.lang.am.normalizer import ( 
  normalize_labialized, 
  normalize_shortened,
  normalize_punct,
  normalize_char
)

# normalize labialized 
normalized_text = normalize_labialized("ንግግርን ወደ ጽሁፍ ለመቀየር የሚያስችሉ መተግበሪያዎችን ማልማት አስረላጊነቱ ተገልጹዋል")
print(normalized_text)
# output: ንግግርን ወደ ፅሁፍ ለመቀየር የሚያስችሉ መተግበሪያዎችን ማልማት አስረላጊነቱ ተገልጿል

# normalize short forms
normalized_text = normalize_shortened("ሚያዝያ 14፣ 2014 ዓ.ም በዓገር ደረጃ የሰው ሰራሽ አስተውሎት የውይይት መድረክ")
print(normalized_text)
# output: ሚያዝያ 14፣ 2014 ዓመተ ምህረት በአገር ደረጃ የሰው ሰራሽ አስተውሎት የውይይት መድረክ

# normalize punctuation
normalized_text = normalize_punct("መተግበሪያዎችን ማልማት አስረላጊነቱ ተገልጹዋል::")
print(normalized_text)
# output: መተግበሪያዎችን ማልማት አስረላጊነቱ ተገልጿል።

# normalize characters
normalized_text = normalize_char("በቋንቋዉ ሕግጋት መሠረት ጽሑፎችን ማዋቀር እና መመሥረት")
print(normalized_text)
# output: በቋንቋዉ ህግጋት መሰረት ፅሁፎችን ማዋቀር እና መመስረት
```

### Normalization API

The complete normalization API can be found at the following address: [normalization functions](./functions/#2-text-normalization-functions)
