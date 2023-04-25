# emoji-json
JSON data for handling emojis. Compatible with v15.0.

It is convenient to have a JSON data that provides information about emoji keywords, orders, and other details when creating an emoji picker or autocomplete for emoji input.  
I have prepared JSON data that supports v15, and would like to share it with you.  
If the response is positive, we will continue to support future versions, so please give us a star. Please also write your requests in the ISSUE section!

## Features
- Support for emoji v15
- order
- subcategories
- the relationship between base emoji and skin tone variants

## install
```
npm install @arayutw/emoji-json
```

## property
### `emoji.json`
An object with the emoji ID as the key.
```json
{
  "2049": {
    "category": "Symbols",  // category name string | null
    "code": "U+2049", // code point string
    "id": "2049", // unique id string
    "keywords": [ // keywords Array string | null
      "!",
      "!?",
      "?",
      "exclamation",
      "interrobang",
      "mark",
      "punctuation",
      "question"
    ],
    "name": "exclamation question mark",  // short name string
    "order": 1496,  // order int | null
    "parent": null, // base emoji id string
    "skin": [], // The skin tone included in this emoji. ("1f3fb" | "1f3fc" | "1f3fd" | "1f3fe" | "1f3ff")[]
    "subcategory": "punctuation", // sub category name string
    "text": "⁉" // emoji string
  },
  "...": {
    // ...
  },
}
```

### `category.json`
An object with the category name as the key.
```json
{
  "Flags": {
    "name": "Flags",
    "order": 10,
    "subcategory": {
      "flag": {
        "name": "flag",
        "order": 1
      },
      "country-flag": {
        "name": "country-flag",
        "order": 2
      },
      "subdivision-flag": {
        "name": "subdivision-flag",
        "order": 3
      }
    }
  }
}
```

## Skin tone
Skin tone emojis have the parent emoji ID in the parent property.  
category, subcategory, order, and keywords are null since they are the same as the parent emoji.  
In the following example, "1f44b-1f3fb" is a skin tone emoji for "1f44b".
```json
{
  "1f44b": {
    "category": "People & Body",
    "code": "U+1F44B",
    "id": "1f44b",
    "keywords": [
      "hand",
      "wave",
      "waving"
    ],
    "name": "waving hand",
    "order": 167,
    "parent": null,
    "skin": [],
    "subcategory": "hand-fingers-open",
    "text": "👋"
  },
  "1f44b-1f3fb": {
    "category": null,
    "code": "U+1F44B U+1F3FB",
    "id": "1f44b-1f3fb",
    "keywords": null,
    "name": "waving hand: light skin tone",
    "order": null,
    "parent": "1f44b",
    "skin": [
      "1f3fb"
    ],
    "subcategory": null,
    "text": "👋🏻"
  },
}
```