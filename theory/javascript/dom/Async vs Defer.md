### Regular script tag

```html
<script>
```

The HTML file will be parsed until the script file is hit,
at that point parsing will stop and a request will be made to fetch the file (if it’s external).
The script will then be executed before parsing is resumed.

### `async`

```html
<script async>
```

`async` downloads the file during HTML parsing
it will pause the HTML parser to execute it when it has finished downloading.
we don't know when the script will download. it depends on network speed so generally it is not used

### `defer`

```html
<script defer>
```
defer downloads the file during HTML parsing and will only execute it after the parser has completed.
defer scripts are also guaranteed to execute in the order that they appear in the document.

---
## Uses

If the script is modular and does not rely on any scripts then use async.
If the script relies upon or is relied upon by another script then use defer.
If the script is small and is relied upon by an async script then use an inline script with no attributes placed above the async scripts.