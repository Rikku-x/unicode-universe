- [Unicode universe](#unicode-universe)
- [The codespace](#the-codespace)
- [Unicode internal representation](#unicode-internal-representation)
- [Dynamic composition in Unicode](#dynamic-composition-in-unicode)
- [Why not ASCII?](#why-not-ascii)
- [Types of encoding](#types-of-encoding)
- [UTF-8 vs UTF-16?](#utf-8-vs-utf-16)
- [UTF-8](#utf-8)

## Unicode universe

What do we know about Unicode? According to the [official website](https://home.unicode.org/), Unicode is "the universal character encoding, maintained by the Unicode Consortium. This encoding standard provides the basis for processing, storage, and interchange of text data in any language in all modern software and information technology protocols."

Not long ago was the time when emails with headings like "?????? ????????" were commonplace whereas nowadays there is no such problem. What has changed? To start, you need to realise the immense number of languages and dialects that exist (or existed) in the world. People can make use of it and communicate with each other, but the computer itself is not so smart.

With the rise of the Internet, it became necessary to teach computers to understand and distinguish languages. That is when character encoding instructions started to appear. It made possible to display information according to the desired language. Some time later, a Unicode Consortium created a standard of character encoding called Unicode. Unicode Consortium is a non-profit organization founded in 1991. To date, the current version of Unicode is [13.0.0](http://www.unicode.org/versions/Unicode13.0.0/) from March 2020. It contains 143,859 characters and 154 scripts. In Unicode, a collection of letters or written signs is called a script.

Two main goals of Unicode are:

- to provide easily accessible and understandable software developing process
- to allow people in any country to use computers in any language

The strict Unicode structure does not seek simplification but encompasses many complex scenarios. This applies, for example, to texts in which several languages are used at once.

Unicode operates with characters, which are commonly called code points. The code points are written as follows: prefix "U +" and a number in hexadecimal format. For example, code point `U+0043` corresponds to [LATIN CAPITAL LETTER C](https://unicode.org/cldr/utility/character.jsp?%D1%81=%D0%A1). Moreover, each code point has a specific set of properties that can be found on the official website.

## The codespace

Speaking of Unicode, it is important to mention the codespace. The codespace is a set of all possible code points. In total, there are more than 1,114,100 code points in the codespace, of which just under 130,000 (about 12%) are assigned. It is worth noting that Unicode allocated a number of code points for personal use, which is not subject to the standard purpose and can be used by certain applications for their specific purposes.

For a better understanding of the structure of the codespace, 256 (16 × 16) boxes placed in one large plane can be imagined. In one plane there are 65,536 boxes. There are 17 such planes.

The zero plane is called the "Basic Multilingual Plane" or [BMP](<https://en.wikipedia.org/wiki/Plane_(Unicode)#Basic_Multilingual_Plane>). It contains most of the characters that can be used today, including Latin, Cyrillic, Hebrew, Greek, Japanese, Han (Chinese), Korean, Arabic, and many others. In the first plane there are historical scripts (for example, Egyptian hieroglyphs) and emoji. Rarely used and historical Han characters belong to the second plane. 14th plane stores some non-typical formatting characters and 15–16 planes contain characters for private use. The remaining planes are free.

Many code points in the codespace are adapted or borrowed from earlier encodings, which gives advantages over compatibility issues. For example, preventing losses when converting text from other encodings to Unicode.

To summarize given information, below is a list of key advantages of Unicode:

- Unicode is a single encoding scheme for all characters and languages
- Unicode data is available in various systems (Windows, Mac OS, Linux)
- Unicode provides an ability to conduct software development for various platforms, countries, and languages within one system
- Unicode is the unifying core of character encoding schemes
- Conversion to Unicode from another encoding scheme and vice versa is available

## Unicode internal representation

When working with text it is important to think about the internal representation. Speaking of Unicode, the internal representation is an array of 16 or 32-bit integer unsigned numbers. The internal representation can work with different encoding types (we will talk about it later), such as UTF-8, UTF-16, and UTF-32, where UTF stands for Unicode Transformation Unit. A developer should think of encoding when reading text data and printing it out.

## Dynamic composition in Unicode

Unicode supports many diacritic signs and every sign can be applied to only one letter or several. Some sophisticated situations may arise with, for example, characters "é", "ö", "ż" and others. Do they consist of one character or two – the letter itself and the diacritical mark? What happens if this symbol to be reversed, will the diacritical mark remain in the right place? How to use text search functions with such characters if a keyboard does not have it?

In Unicode there is a system of characters that are dynamically composed, this system allows to combine codepoints and create desired characters. When a text editor has a similar sequence in a line, a composed character is created automatically.

It is important to emphasize that all this has already been implemented and the developer can find solutions for the issues he faces by familiarizing himself with [ICU-project website](http://site.icu-project.org/home) and selecting the desired library. Also, it is recommended to check the documentation of the applicable programming language.

## Why not ASCII?

At one time, [ASCII](https://en.wikipedia.org/wiki/ASCII) was indispensable, but keep in mind that Unicode is a lot more. It includes more characters and has an expanded structure.

ASCII and Unicode are two different encoding approaches. Their main task is to operate (i.e. store, record, etc.) symbols in binary format. The key difference between ASCII and Unicode is the encoding approach and the number of bits allocated per character.

Today, ASCII uses 8 bits per character, while Unicode allows choosing between 32, 16 and 8-bit encoding types thanks to the variable bit encoding program. Why do we need more bits? With more bits, it’s possible to use more characters that results in larger files. Extra space can be saved by using fewer bits.

In Unicode, all code points are standardized, whereas ASCII offers many non-standard programs. For example, a developer may face some problems displaying characters unless he or she doesn’t use the common pages that Microsoft uses.

The advantage of Unicode is that it stores a large number of characters. Even though Unicode covers most written languages, there is still enough free space to add new ones. That is why Unicode supposed to be relevant in the near future.

Given the widespread popularity of ASCII, Unicode was developed with support for ASCII compatibility. More precisely, the first 8 bits of Unicode correspond to the bits of the most popular ASCII code page. A code page is a coding scheme that maps a certain combination of bits to a character representation. Thus, opening a file in ASCII encoding with Unicode, a developer still get the correct characters.

According to the above information, it can be concluded that the advantages of Unicode over ASCII are:

- Unicode provides different encoding types (32, 16 and 8 bit)
- code points in Unicode are standardized
- Unicode stores a large number of characters and still have space for new ones
- Unicode is ASCII compatible

## Types of encoding

Why do we need encoding? For different types of data to be used within different systems, data must be correctly encoded. Encoding data is not about hiding it, it is about processing it for the later use. For encoding no secret keys are needed but a generally recognized scheme according to which everything works. Decoding of formats is carried out due to a special algorithm.

Today, Unicode uses several types of encoding, most common of them are UTF-8, UTF-16, and UTF-32.

Nowadays, an informal decision has been made to use UTF-8 encoding. There is a manifest [UTF-8 Everywhere](http://utf8everywhere.org/), an informative source of information written by developers and explaining the benefits of UTF-8, and answering the most common questions.

All valid code points of Unicode can be encoded with UTF-16. This encoding type is mostly used by Microsoft Windows.

UTF-32 allocates 4 bytes per code point. When working with UTF-32, it is necessary to provide additional memory space, especially in cases with large texts. Today, UTF-32 is used very rarely.

## UTF-8 vs UTF-16

UTF-8 and UTF-16 are used much more often. UTF-8 uses 8 bits (1 byte) for encoding, this scenario is applicable for English characters, in cases of encoding other characters certain sequences of bytes are applicable. UTF-16 uses 16 bits (2 bytes) to encode most characters. In complex cases, symbols can be represented by a pair of 16-bit numbers.

The main difference between UTF-8 and UTF-16 is the number of bytes used to encode a single character. Both standards are of [variable width encoding](https://en.wikipedia.org/wiki/Variable-width_encoding) type, which means that they use up to 4 bytes to encode data, but their minimum is 8 bits for UTF-8 and 16 bits for UTF-16. The number of bytes used noticeably affects the final size of the files.

The main advantage of UTF-8 is compatibility with ASCII, the character set of which uses 1 byte. When encoding a file that contains only ASCII characters with UTF-8, the size of the final file will be comparable to the size of the file encoded with ASCII. This situation is not possible in the case of encoding UTF-16, because each character is 2 bytes long.

When errors occur, UTF-16 can recover corrupted fragments, however, some bytes can be lost permanently. UTF-8 recovers from errors better, as it can decode uncorrupted bytes.

Why choose UTF-8 instead of UTF-16? The reasons are the following:

- UTF-8 uses 1 byte for encoding, UTF-16 uses 2 bytes
- UTF-8 encoded file requires less space than UTF-16 encoded file
- UTF-8 is compatible with ASCII, while UTF-16 isn’t
- UTF-8 is used by Linux and Mac OS, whereas Windows uses a mix of UTF-16 and ASCII
- UTF-8 recovers from errors better than UTF-16

## UTF-8

As it is said above, UTF-8 uses 8 bits for encoding, it is ASCII compatible and has several other advantages. And yet, there is a couple of features that are worth being highlighted separately.

UTF-8 encoding adds markers to each byte. For the first byte of the multibyte character, the 7th and 6th bits are set, and in the subsequent bytes only 7 bits are set. For example:

|         | 1st byte   | 2nd byte | 3rd byte | 4th byte | 5th byte | 6th byte |
| ------- | ---------- | -------- | -------- | -------- | -------- | -------- |
| 1 byte  | 0xxxxxxx   |
| 2 bytes | 110xxxxx   | 10xxxxxx |
| 3 bytes | 1110xxxx   | 10xxxxxx | 10xxxxxx |
| 4 bytes | 11110xxx   | 10xxxxxx | 10xxxxxx | 10xxxxxx |
| 5 bytes | 111110xxx  | 10xxxxxx | 10xxxxxx | 10xxxxxx | 10xxxxxx |
| 6 bytes | 1111110xxx | 10xxxxxx | 10xxxxxx | 10xxxxxx | 10xxxxxx | 10xxxxxx |

An important feature of UTF-8 is that this encoding does not have endianness or byte order, which makes possible to read it in big or little endian order. It is also worth noting that almost all [C byte functions](https://en.wikipedia.org/wiki/C_string_handling) are compatible with UTF-8 encoding strings, for example, `printf`. This does not apply to UTF-16 and UTF-32 encodings. For UTF-16 there are UTF-16LE and UTF-16BE encodings exist.

Why not let every developer use encoding? It is a complex question from a technical standpoint. Using different encodings may lead to errors and plenty of time spent on fixing these errors. Almost 95% of all webpages use UTF-8 making it a dominant encoding type.
