# Firefly Sources

## Fragments
 
Sources can be given in *'fragments'*, i. e., in more folders and files. 

- The name of a file fragment must have the `.firefly.html` *ending*.
- A folder's *main source* is in the `!.firefly.html`; other files and subfolders are 
placed into its outer (last) heading's content in lexicographic order.
- Firefly combines the fragments into a single source
- Every fragment can have its own heading numbering; Firefly will renumber the headings. 
<br>E. g., every fragments can start with an `<h1>`

### Example

The `!.firefly.html`:

```
<h1>Main Title</h1>

<p>Description
```

The `1_Part.firefly.html`:

```
<h1>Part 2</h1>

<p>Description
```

'Part 2' will be put at the end of the content of the 'Main Title'.

## Simplified HTML format

Firefly provides to create testable descriptions of applications. Descriptions and 
test steps can be given in simplified HTML format, that uses the following tags:

- **`<section>`** - optionally can be used around headings and their contents

- **`<h1>` - `<h6>`** - **Headings**
  - Firefly builds the structure of headings and their contents. 
    - The heading's content has the descriptions, codes, optional sections and subheadings. For example, if there's an `<h2>` and later an `<h3>` (without a `<section>` tag), the `<h3>` will be in the content of the `<h2>`. 
  - `<section>` tags can be used to specify the structure, thus in the structure of `<section>` tags the same heading number can be used.
  - headings closes open `<p>` and `<pre>` tags

- **`<div>`** ... **Description**, that may contain subdescriptions and codes
  - `<div>` closes open `<p>` and `<pre>` tags

- **`<p>`** ... - **Simple description**
  - `<p>` closes open `<p>` and `<pre>` tags
  - the following `<pre>` tags are handled as codes of the description 

- **`<pre>`** ... - **Code**
  - `<pre>` closes open `<pre>` tag

- Descriptions can have other HTML tags, e.g., `<b>`, `<i>`, `<img ...>`.

## Img

If a description contains an `<img data-ff src="`...`"`... part, then the result of the *first inner code* is put into the `src` attribute.

E.g., 
```
<div><img data-ff src="?">
  <pre>page.image();
  <pre>page.click('Done');
  <p><img data-ff src="?">
  <pre>page.image();
</div>  
```

## Code

Steps of test execution can be given in `<pre>` tags in JavaScript.

- The JavaScript code can have more *parts*, separated by `;;` characters. Every code part will be executed separately.

- A code part can have an **assertion**, that is a testable condition
  - `??` and `^??` note **optional assertions**
    - if an optional assertion is not fulfilled, it means an **error**, but the execution continues
  - `???` and `^???` note **mandatory assertions**
    - if a mandatory assertion is not fulfilled, it means a **failure**, and the execution does not continue

- **Condition assertions** ('Check' assertions)
  - `EXPR1 ?? ;;` and `EXPR1 ??? ;;` - test if the value of the `EXPR1` is **true-ish** 
    - 'true-ish' means that the value is not undefined, not null, not 0, not "", not an empty array and not an empty object 
    - e. g., `<pre> page.get('')`
  - `EXPR1 ^?? ;;` and `EXPR1 ^??? ;;` - test if the value of the `EXPR1` is **false-ish**, i. e., not true-ish 

- **Value assertions** ('Match' assertions)
  - `EXPR1 ?? EXPR2;;` and `EXPR1 ??? EXPR2 ;;` - compare if the values are **matched**
    - generally it checks if the value of the `EXPR1` **equals** to the asserted value of `EXPR2` 
    - if the `EXPR2` asserted value is an **Array**
      - if the `EXPR1` is a **String**, it checks if `EXPR1` contains each `EXPR2` element as String 
      - if the `EXPR1` is an **Array**, it checks if `EXPR1` contains each `EXPR2` element  
      - otherwise it fails
    - if the `EXPR2` asserted value is an **Object**
      - it checks if `EXPR1` contains each `EXPR2` fields with the same value 
      - otherwise it fails
  - `EXPR1 ^?? EXPR2;;` and `EXPR1 ^??? EXPR2 ;;` - compare if the values are **not matched**


