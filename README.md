# english_japanese_diffsinger_guide

this guide is pretty much just my workflow when it comes to making my model, plus a list of phonemes that will need to be changed to make sure that the accents of the languages will not affect each other. this can be done via cross language synthesis, or via 

for this guide, I will assume you are using nnsvs style databases (minus the .ust files) that will be converted to diffsinger format.

in general, you want to make sure both languages are contained in 2 separate folders until being converted to diffsinger format.

then, you want to decide which language you would like to be the "main" language, as in like, which language the voicebank will be mainly used for. the "main" language should probably be the language your most used to, as its easier to gather data for that language. the only thing that having a "main" language does is specify which language will have altered phonemes.

changing phonemes is necessary for having a normal sounding accent in each language.

# phonemes that share the same name, but are seperate phoneticaly
| phoneme        | ipa english   | Ipa Japanese  |
| -------------- | ------------- | ------------- |
| r              | ɹ             | ɾ             |
| d              | d or ɾ        | d             |
| t              | t or ɾ        | t             |
| f              | f             | ɸ             |

t and d are both realised differently in english compared to Japanese, if you use the same t and d from your main language, feel free to leave it as is. if want to do this, and your main language is english, you have to make sure there are not any dx phonemes labeled as t or d, as not having them seperated will make the japanese voice say "r" instead of what is intended.

# phonemes that are the same phoneticaly, but have different names
| phoneme(ipa)   | arpa english  | Japanese romaji|
| -------------- | ------------- | -------------- |
| ɾ              | dx            | r              |
| dʒ             | jh            | j              |
| h              | hh            | h              |

this list assumes you use only standard pronunciation, if you use any allophones, such as "ʒ" for "j" in Japanese, make sure you replace the correct phoneme, in this case "zh".
