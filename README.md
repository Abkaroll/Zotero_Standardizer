# Zotero_Standardizer
Standardizing entries in Zotero, mostly for Journal Titles
ZOTERO STANDARDIZER SCRIPT — README

WHAT THIS SCRIPT DOES:
-----------------------
This script helps clean up your Zotero library by standardizing values like journal titles. For example, if the same journal is entered as “PloS One” or “PLoS ONE,” the script will find all those entries and change them to the correct version: “PLOS One”.

HOW TO USE THE SCRIPT:
-----------------------
1. Open Zotero.
2. Go to `Tools > Developer > Run JavaScript`.
3. Paste the full script into the window.
4. Press "Run".

5. The script will list your Zotero folders.
6. Type the number of the folder you want to fix (example: `2`) and press OK.
7. You will get a message telling you how many entries were updated.

HOW TO CUSTOMIZE THE SCRIPT:
-----------------------------

1. TO CHANGE WHAT YOU'RE FIXING (JOURNAL TITLES, BOOK TITLES, AUTHORS, ETC.)
-------------------------------------------------
Find this part near the top of the script:

```javascript
const correctionsMap = new Map([
    ["PLoS ONE", "PLOS One"],
    ["PloS One", "PLOS One"],
    ["PLOS ONE", "PLOS One"]
]);
```

➤ To fix other fields (like book titles, authors, etc.), change the left side to the “wrong” version and the right side to the correct version.

Examples:

```javascript
["Nature journal", "Nature"]
["Douglas Adams", "Adams, Douglas"]
["march 5, 2020", "2020-03-05"]
```

You can add as many as you want. Just copy the format:  
`["wrong version", "correct version"],`

2. TO CHANGE WHICH FIELD YOU ARE FIXING
------------------------------------------
Right below the corrections, you’ll see:

```javascript
const fieldName = "publicationTitle";
```

This is where you tell the script which field to fix. Here are some options:

- `"title"` — fixes the main title (used for books, articles, etc.)
- `"publicationTitle"` — fixes journal names
- `"creators"` — for authors/editors (⚠ advanced use)
- `"date"` — for fixing dates (e.g. format to YYYY-MM-DD)

To fix book titles, just change it to:

```javascript
const fieldName = "title";
```

3. TO FIX DATES
------------------
Zotero expects dates in `YYYY-MM-DD` format (or just `YYYY-MM`).  

If you want to correct dates like this:

```javascript
const correctionsMap = new Map([
    ["March 5, 2020", "2020-03-05"],
    ["5 Mar 2020", "2020-03-05"]
]);
const fieldName = "date";
```

Note: Make sure all entries you want to fix are spelled *exactly* as shown in Zotero, or the script won’t find them.

TIPS:
-----
✔ Always test on a small folder first.
✔ You can undo changes manually in Zotero if needed.
✔ The script will never delete or remove items — it only updates field values.
