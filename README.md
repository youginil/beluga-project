# Beluga Project

## Mdict likely

| Title                   | Structure                                                                                                              |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Metadata                | (length-2B)(json)                                                                                                      |
| Word block index length | (4B)                                                                                                                   |
| Word block index        | (first word length-2B)(first word)(last word length-2B)(last word)(block compress offset-8B)(block compress length 2B) |
| Word block              | (length-2B)(word)(definition uncompress offset-8B)...                                                                  |
| Definition block index  | (uncompress offset-8B)(uncompress length 4B)(compress offset-8B)(compress length 4B)...                                |
| Definition block        | (xml compressed by deflate)...                                                                                         |

## References

#### Mdict

- https://github.com/csarron/mdict-analysis
- https://github.com/zhansliu/writemdict/blob/master/fileformat.md
- https://github.com/fengdh/mdict-js
- https://github.com/ilius/pyglossary

#### Fulltext Index

- https://github.com/stanfordnlp/CoreNLP
- https://github.com/hankcs/HanLP
- https://github.com/nltk/nltk
- https://github.com/RaRe-Technologies/gensim
- https://github.com/explosion/spaCy
- https://github.com/keras-team/keras
- https://github.com/thunlp/THULAC
- https://github.com/yanyiwu/cppjieba
- @ https://github.com/fxsjy/jieba
- https://github.com/HIT-SCIR/ltp
- https://github.com/NLPchina/ansj_seg

#### Dictionary Online

- https://www.thesaurus.com/
- https://www.dictionary.com/
- https://dictionary.cambridge.org/
- https://www.collinsdictionary.com/
- https://www.macmillandictionary.com/
- https://www.ldoceonline.com/
- https://www.oxfordlearnersdictionaries.com/
