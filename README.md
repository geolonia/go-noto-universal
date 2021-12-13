# Go Noto Universal

Noto fonts go universal! Download Noto fonts combined to suit your region (South Asia, SE Asia,
Africa-MiddleEast, Europe-Americas).

This software combines/merges multiple [Noto Fonts](https://github.com/googlefonts/noto-fonts) to a
single, region-specific font.

## Download

If you simply want to _use_ the fonts, go to [Releases
page](https://github.com/satbyy/go-noto-universal/releases/) and download what you need.

Development builds are available from [GitHub
Actions](https://github.com/satbyy/go-noto-universal/actions) page.
Click on any workflow with green checkmark ✅ and under "Artifacts", download "GoNotoUniversal.zip"

## Build

If you want to _build_ the fonts yourself, create a virtual environment (venv) and call `./run.sh`.

```
python3 -m venv venv_fonty
source venv_fonty/bin/activate
./run.sh
deactivate
```

Font generation can take a few minutes to several hours, depending on your computer's capabilities.
The Go Noto South Asia takes the longest time to generate.

`run.sh` is designed to be reentrant, so you can run it multiple times without altering the working
state of the repository or downloading stuff again and again.

## Dependencies

There is no dependency other than [`nototools`](https://github.com/googlefonts/nototools) and
[`fonttools`](https://github.com/fonttools/fonttools/). Both are automatically fetched and used.

## Coverage

Fonts are merged/combined as per the regions defined in the [Unicode Standard
(pdf)](https://www.unicode.org/versions/Unicode14.0.0/UnicodeStandard-14.0.pdf). Chapter numbers
below refer to that spec.

| Regional font              | Coverage                                                                                |
|----------------------------|-----------------------------------------------------------------------------------------|
| GoNotoEuropeAmericas.ttf   | "Europe" - ch. 7, 8 and "Americas" - ch 20                                              |
| GoNotoAfricaMiddleEast.ttf | "Middle East" - ch. 9, 10, 11 and "Africa" - ch. 19                                     |
| GoNotoSouthAsia.ttf        | "South and Central Asia" - ch. 12 and 13                                                |
| GoNotoAsiaHistorical.ttf   | "South and Central Asia" - ch. 14 and 15                                                |
| GoNotoSouthEastAsia.ttf    | "Southeast Asia" - ch. 16 and "Indonesia and Ocenia" - ch 17                            |
| GoNotoCJKCore2005.ttf      | [Unihan IICore][1] subset of CJK (~10K ideographs). Use [Noto CJK][2] for full coverage |
| GoNotoEastAsia.ttf         | "East Asia" - ch 18. everything other than Han (CJK)                                    |

Each of the above fonts includes LGC (Latin-Greek-Cyrillic) as default, same coverage as `Noto Sans
Regular`. Each one also includes Noto Sans Math, Noto Sans Symbols and Noto Sans Symbols 2 to give
you bonus coverage of beautiful notations, symbols and emoji :)

### Go Noto South Asia

Following are included: Devanagari (Hindi, Marathi, Nepali, etc), Bengali, Punjabi (Gurmukhi),
Gujarati, Oriya, Tamil, Telugu, Kannada, Malayalam, Thaana, Sinhala, Newa, Tibetan, Limbu, Meetei
Mayek, Mro, Warang Citi, Ol Chiki, Chakma, Lepcha, Saurashtra, Masaram Gondi, Gunjala Gondi, Wancho.

Urdu (NotoNastaliq), though not written in an Indic script and not part of "South Asia" chapters in
the Unicode spec, is included for practical reasons. Mongolian is currently not included because of
issue with vmtx (vertical metrics). Noto fonts do not exist for Toto and Tangsa.

### Go Noto Asia Historical

Following are included: Brahmi, Kharoshthi, Bhaiksuki, Phags-Pa, Marchen, Zanabazar Square, Soyombo,
Old Turkic, Old Sogdian, Sogdian, Old Uyghur, Syloti Nagri, Kaithi, Sharada, Takri, Siddham,
Mahajani, Khojki, Khudawadi, Multani, Tirhuta, Modi, Grantha, Ahom, Sora Sompeng, Dogra.

Nandinagari is currently not included. Noto fonts do not exist for Dives Akuru. An older version of
NotoSansDogra is included.

### Go Noto South East Asia

Following are included: Thai, Lao, Myanmar, Khmer, Tai Le, New Tai Lue, Tai Tham, Tai Viet, Kayah
Li, Cham, Pahawh Hmong, Pau Cin Hau, Hanifi Rohingya, Tagalog, Hanunoo, Buhid, Tagbanwa, Buginese,
Balinese, Javanese, Sundanese, Rejang, Batak.

Noto fonts do not exist for Makasar and Nyiakeng Puache Hmong.

### Go Noto Europe Americas

Everything covered by NotoSans (Latin-Greek-Cyrillic etc.) plus Armenian, Coptic, Cypriot, Georgian,
Deseret, Glagolitic, Osage, Old Italic, Runic, Anatolian Hieroglyphics, Carian, Canadian Aboriginal,
Cherokee, Old Hungarian, Gothic, Elbasan, Caucasian Albanian, Vithkuqi, Ogham, Old Permic, Shavian,
Linear A and Linear B.

### Go Noto Africa Middle East

The following are included: Arabic (Naskh-style), Adlam, Avestan, Bamum, Bassa Vah, Cuneiform,
Hebrew, Syriac, Samaritan, Mandaic, Yezidi, Old North Arabian, Old South Arabian, Phoenician,
Imperial Aramaic, Manichaean, Inscriptional Parthian, Inscriptional Pahlavi, Psalter Pahlavi,
Elymaic, Nabataean, Palmyrene, Hatran, Ugaritic, Old Persian, Egyptian, Meroitic, Anatolian
Hieroglyphics.

Noto fonts do not exist for Chorasmian.

### Go Noto East Asia

Tibetan, Lisu, Marchen, Miao, Yi, etc. excluding Han/CJK (Chinese-Japanese-Korean).

Mongolian, Nüshu and Tangut could not be included.

### Go Noto CJK Core 2005

[Unihan IICore][1] is a minimal, region-agnostic subset of Han/CJK specified in 2005 for
memory-constrained systems. It standardizes about 9800 codepoints, covering basic use cases of
Chinese (Traditional, Simplified), Japanese and Korean. Recently [Unihan Core
2020](https://unicode.org/charts/unihan.html) superseded and expanded the minimal subset to about
20000 codepoints.

The GoNotoCJKCore2005 includes "locl" features, so it can display Japanese or Korean glyphs just by
switching the language in your editor/word processor/web browser etc.

The generated font does _not_ contain Noto Sans Math, Noto Sans Symbols, Noto Sans Symbols 2 because
[fonttools does not support](https://fonttools.readthedocs.io/en/latest/merge.html) merging fonts
with CFF outlines (which is the case for .otf). Converting .otf to .ttf still doesn't solve the
problem because CJK fonts have "vmtx" table, which is absent in other fonts, thus preventing
`pyftmerge`.


## Font Statistics

Statistics below correspond to release v2.1.

| Regional font              | Code blocks | Codepoints | Glyphs |
|----------------------------|-------------|------------|--------|
| GoNotoEuropeAmericas.ttf   | 111         | 11896      | 14780  |
| GoNotoAfricaMiddleEast.ttf | 125         | 15506      | 19750  |
| GoNotoSouthAsia.ttf        | 114         | 10922      | 20879  |
| GoNotoAsiaHistorical.ttf   | 114         | 10261      | 16767  |
| GoNotoSouthEastAsia.ttf    | 107         | 10168      | 14358  |
| GoNotoEastAsia.ttf         | 96          | 10522      | 15081  |
| GoNotoCJKCore2005.ttf      | 20          | 10338      | 20099  |

Note that each of the above (except CJKCore2005) include statistics of:

| Upstream font       | Code blocks | Codepoints      | Glyphs      |
|---------------------|-------------|-----------------|-------------|
| Noto Sans           | 37 blocks   | 2840 codepoints | 3317 glyphs |
| Noto Sans Math      | 22 blocks   | 2472 codepoints | 2655 glyphs |
| Noto Sans Symbols   | 15 blocks   | 840 codepoints  | 1218 glyphs |
| Noto Sans Symbols 2 | 37 blocks   | 2655 codepoints | 2674 glyphs |
| Total               | 111 blocks  | 8807 codepoints | 9864 glyphs |

## Caveats

1. You might have to increase line spacing or line margins in your application to avoid some
   characters appearing "clipped". This is because many Asian scripts stack letters vertically
   (e.g. Indic scripts, Thai, Balinese etc.) but the line metrics of the merged font are
   optimized for LGC.
2. Tibetan has limited glyphs, otherwise GSUB table gets "overflow"ed. Only the most frequently
   occuring "subjoined consonants" are included. Those characters are displayed ok, but just that
   the glyphs appear to be "pushed up" compared to their neighbours.
3. Certain fonts just refuse to cooperate, e.g. Mongolian, Nushu.

## License

In the spirit of _loka-saṃgraha_, the scripts distributed in this git repository (the "Software")
are dedicated to the public domain as per "The Unlicense". See UNLICENSE.txt.

However, the fonts generated by using the the Software are licensed under the SIL Open Font License,
Version 1.1, as required by the upstream Noto Fonts Project.

### Others

FontTools package comes with nice utilities `ttx` (ttf to xml and back), `pyftsubset` (create font
with subset of given font) and `pyftmerge` (merging fonts, basically same as this repo).

`otfinfo` gives useful info about glyphs, codepoints, scripts and more.

<!--
1891 glyphs -> GSUB LookupIndex 1293 fails
1575 glyphs -> GSUB LookupIndex 646 fails. Max Lookuptable size = 1651
(NoSubjoined) 168 code points, 688 glpyhs -> GSUB LookupCount 1680

../venv_fonty/bin/pyftsubset  NotoSerifTibetan-Regular.ttf \
    --unicodes=U+0F00-0F8C,U+0F90,U+0F94,U+0F95,U+0F97,U+0F9F,U+0FA1,U+0FA3,U+0FA4,\
    U+0FA6,U+0FA9,U+0FAB,U+0FAD,U+0FAF,U+0FB1-0FB3,U+0FB06-0FB8,U+0FBE-0FDA
=> gives 181 codepoints, 1380 glyphs, 401KB size, GSUB LookupCount 915

In comparison, Devanagari has GSUB LookupCount = 120 just!

--unicodes=U+0F00-0F68,U+0F6B-0F87,U+0F90,U+0F94,U+0F95,U+0F97,U+0F
9F,U+0FA1,U+0FA3,U+0FA4,U+0FA6,U+0FA9,U+0FAB,U+0FAD,U+0FAF,U+0FB1-0FB3,U+0FB06-0FB8,U+0FBE-0FDA

=> gives 174 codepoints, 1322 glyphs, 385KB size, GSUB LookupCount 892

-ka, -ga, -ja, -ta, -da, -na, -pa, -ba, -ma, -ya, -ra, -la, -wa, -tsa, -ha

Bhutanese/Tibetan only:

 --unicodes=U+0F00-0F8F,U+0F90,U+0F92,U+0F97,U+0F9F,u+0FA1,U+0FA3,U+0FA4,U+0FA6,U+0FA8,U+0FA9,U+0FAD,U+0FB1-0FB3,U+0FB7

155 codepoints, 1435 glyphs, 426 KB,

 --unicodes=U+0F00-0F8C,U+0F90,U+0F92,U+0F97,U+0F9F,u+0FA1,U+0FA3,U+0FA4,U+0FA6,U+0FA8,U+0FA9,U+0FAD,U+0FB1-0FB3,U+0FB8,U+0FBE-0FDA

180 codepoints, 1456 glyphs, 431KB, GSUB 988 lookup ==> Not working

 --unicodes=U+0F00-0F8C,U+0F90,U+0F92,U+0F94,U+0FF99,U+0FAD,U+0FB1-0FB3,U+0FBA-0FDA

175 codepoints, 1023 glyphs, 285KB, GSUB 646 lookup ==> WORKS WITH EastAsia.ttf and SouthAsia.ttf!

  --unicodes=U+0F00-0F8C,U+0F90,U+0F92,U+0F94,U+0F9F,U+0FF99,U+0FAD,U+0FB1-0FB3,U+0FBA-0FDA
(added TA) 176 codepoints, 1096 glyphs, 309KB, GSUB 703

 --unicodes=U+0F00-0F8C,U+0F90,U+0F92,U+0F94,U+0F99,U+0F9F,U+0FA4,U+0FAD,U+0FB1-0FB3,U+0FBA-0FDA
(added TA, PA) 178 codepoints, 1170 glyphs, 330KB, GSUB 749

 --unicodes=U+0F00-0F8C,U+0F90,U+0F92,U+0F94,U+0F99,U+0F9F,U+0FA4,U+0FA9,U+0FAD,U+0FB1-0FB3,U+0FBA-0FDA
(added TA, PA, TSA) 179 codepoints, 1204 glyphs, 343KB, GSUB 771 ==> WORKS with both South Asia!

  --unicodes=U+0F00-0F8C,U+0F90,U+0F92,U+0F94,U+0F99,U+0F9F,U+0FA1,U+0FA4,U+0FA9,U+0FAD,U+0FB1-0FB3,U+0FBA-0FDA
(added TA, PA, TSA, DA) 180 codepoints, 1297 glyphs, 374KB, GSUB 845

  --unicodes=U+0F00-0F8C,U+0F90,U+0F92,U+0F94,U+0F99,U+0F9F,U+0FA1,U+0FA4,U+0FA6,U+0FA9,U+0FAD,U+0FB1-0FB3,U+0FBA-0FDA
(added TA, PA, TSA, DA, BA) 181 codepoints, 1381 glyphs, 402KB, GSUB 912

DA > BA > TA > PA > TSA

--unicodes=U+0F00-0F8C,U+0FAD,U+0FB1,U+0FB2,U+0FBE-0FDA
Basic minimal set 168 codepoints, 839 glyphs, 234KB, 541 GSUB
-->

[1]: https://en.wikipedia.org/wiki/International_Ideographs_Core
[2]: https://github.com/googlefonts/noto-cjk/
