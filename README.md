# english_japanese_diffsinger_guide

this guide is pretty much just my workflow when it comes to making my model, plus a list of phonemes that will need to be changed to make sure that the accents of the languages will not affect each other.

for this guide, I will assume you are using nnsvs style databases (minus the .ust files) that will be converted to diffsinger format.

you want to decide which language you would like to be the "main" language, as in like, which language the voicebank will be mainly used for. the "main" language should probably be the language you're most used to, as it's easier to gather data for that language. the only thing that having a "main" language does is specify which language will have altered phonemes.

when creating an AI dataset, it's important not to spread your data out too much over too many phonemes, so if 2 phonemes are identical in every way, it's good to keep them together.

if 2 phonemes share an alias but are separate, you're going to want to change said aliases. whether that'll be into a different alias that shares said phoneme, or if none exists, a new phoneme.

vowels should always be separated no matter what though. context is extremely powerful when it comes to AI synths and diffsinger especially, so a lot of the heavy lifting is handled by that when it comes to accent.

in general, you want to make sure both languages are contained in 2 separate folders until being converted to diffsinger format.

# phonemes that share the same name, but are separate phonetically
| phoneme        | ipa english   | Ipa Japanese  |
| -------------- | ------------- | ------------- |
| r              | ɹ             | ɾ             |
| d              | d or ɾ        | d             |
| t              | t or ɾ        | t             |
| f              | f             | ɸ             |

t and d are both realized differently in English compared to Japanese, if you use the same t and d from your main language, feel free to leave it as is. if want to do this, and your main language is English, you have to make sure there are not any dx phonemes labeled as t or d, as not having them separated will make the Japanese voice say "r" instead of what is intended.

# phonemes that are the same phonetically, but have different names
| phoneme(IPA)   | arpa English  | Japanese romaji|
| -------------- | ------------- | -------------- |
| ɾ              | dx            | r              |
| dʒ             | jh            | j              |
| h              | hh            | h              |

this list assumes you use only standard pronunciation, if you use any allophones, such as "ʒ" for "j" in Japanese, make sure you replace the correct phoneme, in this case "zh".

from here, you want to download Notepad++ and open all .lab files for the language that you want to switch phonemes out with. you also need to figure out how you want to name some of your phonemes that don't have an equivalent in the opposite language.
hit Ctrl+h or go to search and click on "replace", this is the same as the notepad version, but it can search through files so it makes things easier.

this is what I personally do for my voicebanks, English is my "main" language (main is being used very lightly) so this is how I change my Japanese phonemes.

| old  jp | new engish |
| -------------- | ----------- |
| r      to      | dx          |
| d      to      | dj          |
| t      to      | tj          |
| f      to      | fj          |
| j      to      | jh          |
| h      to      | hh          |

it may also be worth it to change the Japanese v to vj, as if you pronounced Japanese v as a voiced Japanese f, then it would be different to English, but v isn't in Japanese normally so I keep it as is.

feel free to use this or modify it to your needs i don't care lol

# ACTUALY TRAINING
You can keep each language as a separate singer via multisinger, however, I recommend keeping them together as it really makes no difference.

# Dictionary
After getting everything set up, you are going to want to set up the dsdict.yaml file that's contained inside the dsdur folder.

you can switch languages via changing Phonemizer in the track view, currently, there is no way to change languages in the same track (other than maybe putting the dictionary for Japanese into the English dsdict and only having hiragana, but I don't got time to explain how to do that now.)
anyways it's "Diffs" for Japanese, and "Diffs EN" for English.

also im just going to assume you have a Japanese dictionary file. if you don't just steal it from pjs or something idk.

If you change the Japanese phonemes, you can just find and replace everything inside the dictionary with the corresponding phoneme.

If you change the English phonemes, you can make use of the "replacements:" section in a dsdict.

the DIFFS EN phonemizer reads from a file called "dsdict-en.yaml" in the dsdur folder, so just make a text file called that and paste the following part into there.

<pre>
  replacements:
- {from: before, to: after}
</pre>
copy and paste this however many times you need. the "before" is the starting phoneme, and "after" is what it turns into, so for example, if i turned jh into j, i would put
<pre>
  replacements:
- {from: jh, to: j}
</pre>

# TLDR BECAUSE I DEFINITELY DID NOT EXPLAIN THINGS CORRECTLY

when making a multilanguage model, it is important to
  1. keep different phonemes separate so as to not cause bleed between phonemes
  2. keep identical phonemes together so as to not spread out the dataset as much as possible
  3. change the phonemes in the dictionary

anyways yeah that's pretty much it go crazy.
