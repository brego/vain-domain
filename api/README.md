# Description of the vain-domain internal API

This API's barely worth the name. It's a filter and cache-layer between 2
external endpoints:

 - [Big Huge Thesaurus API][]
 - [IANA's list of TLDs][]

## Methods

### `/tlds/`

Will return a JSON array of currently existing TLDs. This should obviously be
cached in the client.

The TLDs will be lowercased, and sorted alphabetically. The `xn--` TLDs (using
non-latin glyphs) will not be returned.

### `/thesaurus/[word]`

Will return a JSON object with synonyms, antonyms, related and similar terms.
Not all of those relationship types will be available for all words.

Example output for `/thesaurus/love` (truncated):

```json
{
  "synonyms": [
    "passion",
    "beloved",
    "dear"
  ],
  "antonyms": [
    "hate"
  ]
}
```

[Big Huge Thesaurus API]: http://words.bighugelabs.com/api.php
[IANA's list of TLDs]: https://www.icann.org/resources/pages/tlds-2012-02-25-en
