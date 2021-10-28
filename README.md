# About Conglomeration
[conglomeration (noun)](https://www.merriam-webster.com/dictionary/conglomeration)<br/>
con·​glom·​er·​a·​tion | \ kən-ˌglä-mə-ˈrā-shən, ˌkän- <br/>
something conglomerated : a mixed mass or collection

## What is Conglomeration?
Conglomeration (the project, not the word) is a simple data-notation method semi-similar to JSON.<br/>
It's meant to be easy to parse (decode) and stringify (encode), and allow saving and loading several "normal"/"common" datatypes, such as Numbers (ints, floats, doubles, etc...), Strings, other tables, aswell as less-common datatypes such as [`Vector3`](https://developer.roblox.com/en-us/api-reference/datatype/Vector3)s, [`Vector2`](https://developer.roblox.com/en-us/api-reference/datatype/Vector2)s, [`UDim2`](https://developer.roblox.com/en-us/api-reference/datatype/UDim2)s, [`UDim`](https://developer.roblox.com/en-us/api-reference/datatype/UDim)s, and lots more, without needing to re-implement them 20 times on 20 different platforms.<br/>
Additionally, Conglomeration allows you to check the (raw text) Size of individual fields of data before fully parsing it, as to let servers reject things with more than `x` bytes of Data.\*<br/><br/>
\* Our "official" parsers may not support this, although that depends on the parser. For this use-case, we encourage you to implement your own parser based on [the standard](/standard/)<br/><br/>

## Roadmap
(Current Version: `0.1.0` | Roadmap is for the standard, not the individual parser libraries)
### >=1.0.0
- Add String Compression
### >=1.1.0
- Add AES256 Encryption
