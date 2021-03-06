# About Conglomeration
[conglomeration (noun)](https://www.merriam-webster.com/dictionary/conglomeration)<br/>
con·​glom·​er·​a·​tion | \ kən-ˌglä-mə-ˈrā-shən, ˌkän- <br/>
something conglomerated : a mixed mass or collection

## What is Conglomeration?
Conglomeration (the project, not the word) is a simple data-notation method semi-similar to JSON.<br/>
It's meant to be easy to parse (decode) and stringify (encode), and allow saving and loading several "normal"/"common" datatypes, such as Numbers (ints, floats, doubles, etc...), Strings, other tables, aswell as less-common datatypes such as [`Vector3`](https://developer.roblox.com/en-us/api-reference/datatype/Vector3)s, [`Vector2`](https://developer.roblox.com/en-us/api-reference/datatype/Vector2)s, [`UDim2`](https://developer.roblox.com/en-us/api-reference/datatype/UDim2)s, [`UDim`](https://developer.roblox.com/en-us/api-reference/datatype/UDim)s, and lots more, without needing to re-implement their encoders/parsers 20 times on 20 different platforms, as the end-user of the library.<br/>
Additionally, Conglomeration allows you to check the (raw text) Size of individual fields of data before fully parsing it, as to let servers reject things with more than `x` bytes of Data.\*<br/><br/>
\* Our "official" parsers may not support this, although that depends on the parser. For this use-case, we encourage you to implement your own parser based on [the standard](/Standard/)<br/><br/>

## Roadmap
See [Standard/Roadmap.md](/Standard/Roadmap.md)

## Versioning
Minor and Patch versions may differ from library to library, but for versions >=1.0.0, the Major version of all Libraries indicates the same, or compatible, standard version.

For <1.0.0, the public API is unstable, aswell as the actual parsing/encoding/etc... of the implementation.

## License
See [LICENSE](/LICENSE/)
