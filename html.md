# HTML CHEATSHEET


<a href="mailto:email">email me</a>
`<a href="mailto:email">email me</a>`

<nav>
  <a href="/html/">Home</a> |
  <a href="/css/">About</a> |
  <a href="/js/">Shop</a> |
  <a href="/python/">Contact</a>
</nav>

```
<nav>
  <a href="/html/">Home</a> |
  <a href="/css/">About</a> |
  <a href="/js/">Shop</a> |
  <a href="/python/">Contact</a>
</nav>
```

```html
  <form>
    <label for="person1Input">A name</label>
    <input id="person1Input" type="text" name="person1Input">
    <label for="person2Input">Another name</label>
    <input id="person2Input" type="text" name="person2Input">
    <label for="animalInput">An animal</label>
    <input id="animalInput" type="text" name="animalInput">
    <label for="exclamationInput">An exclamation</label>
    <input id="exclamationInput" type="text" name="exclamationInput">
    <label for="verbInput">A past tense verb</label>
    <input id="verbInput" type="text" name="verbInput">
    <label for="nounInput">A noun</label>
    <input id="nounInput" type="text" name="nounInput">
    <button type="submit">Show me the story!</button>
  </form>
  ```

## Forms
### form input types
| name         | declaration                                                                                                        |                                                                        |     |     |
| ------------ | ------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------- | --- | --- |
| select box   | `<select id="foo">`<br>  `<option value="foo"></option>`   <br> `  <option value="foo"></option>` <br> `</select>` |                                                                        |     |     |
| radio button | `<input type="radio" name="foo" value="foo" checked>`                                                              | read value selected `querySelector("inpu[name='foo']:checked).value;"` |     |     |
| check boxes  |                                                                                                                    |                                                                        |     |     |
| date         | `<input id="foo" type="date">`                                                                                     |                                                                        |     |     |
| color        | `<input id="foo" type="color">`                                                                                    |                                                                        |     |     |
|              |                                                                                                                    |                                                                        |     |     |
### button types
| type    | description                            | a                                | b   | c   |
| ------- | -------------------------------------- | -------------------------------- | --- | --- |
| submit  | used for form, causes submission event | default submission is to refresh |     |     |
| button  | no default behavior                    |                                  |     |     |
| no type | default type is submit                 |                                  |     |     |
|         |                                        |                                  |     |     |
