An early mockup of Support kit T3.3

Run a linter/validator:
CSS: https://jigsaw.w3.org/css-validator/ or stylelint
JSON: https://jsonlint.com/
Vamilla JS: 
(HTML: https://validator.w3.org/)

### index.json is the basis for the full content. 
encoding can be html, plain or markdown in the json text field, but only markdown is used at this point in time.

### editor.html can be used to suggest changes (by one way or the other "submitting" the newly produced file you have exported)
The whole index.json will be loaded and exportet - always (roundtrips without changing anything should always work for verification) 

### Note on filtering, sorting and order:

"Track" (or if you like: learning path) is the top level filtering. Tags are next level for filtering, then search. 

A search will have hits in module titles, tags, module descriptions, as well as module content (the last shown as a "preview" area. 

### 1. Default Mode (When the search field is EMPTY)

When you haven't typed anything into the search field, the order is guided by a structured, logical learning path (alphabetical, numbered etc.) 

Sorting happens in two stages: First by Track (Category): The code groups the articles alphabetically by the track they belong to (e.g., managers, researchers, trainers).

Then by order (Sequence): Within each group, the modules are sorted according to your numerical order field (e.g., 1, 2, 3).Why does it do this?This ensures that the course material and modules are arranged in a pedagogical sequence (e.g., Introduction to Step 1 to Step 2). 

This logic is also what allows your code to automatically find the "Next Module" by looking for an article in the same track with an order + 1 value.


### 2. Search Mode (When you TYPE in the search field).

As soon as you type a word into the search field, the default mode turns off completely. The learning path and the order numbers are entirely ignored. Instead, results are sorted by relevance (how well the search term matches the title):

Your code assigns points (scoring) based on where your search term appears:3 points (Highest relevance): If the article title matches the exact word you searched for.2 points (Medium relevance): If the article title starts with the word you searched for.1 point (Lowest relevance): If the word is found anywhere inside the title text, inside the abstract (summary), or among the tags.In case of a tie (Equal score):If two articles get the exact same score (for example, if both contain the search term right in the middle of their abstracts), the code falls back on sorting the titles alphabetically (titleA.localeCompare(titleB)) to determine which one comes first.




### Searching
The words in a title and abstract and tags (defined in the file index.json) are the basis for the search function and the "front page". 
markdown-it is the basis for parsing markdown into html, used together also with the styling from the css file and javascript code in the app.js file. 
This solution will run on any web server.

## The use of Markdown-it is in this solution based on the original MIT License for the markdown-it javascript:

https://github.com/markdown-it/markdown-it?tab=MIT-1-ov-file 

"Copyright (c) 2014 Vitaly Puzrin, Alex Kocharin.

Permission is hereby granted, free of charge, to any person
obtaining a copy of this software and associated documentation
files (the "Software"), to deal in the Software without
restriction, including without limitation the rights to use,
copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following
conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE."


