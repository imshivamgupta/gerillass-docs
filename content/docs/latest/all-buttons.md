---
title: "All Buttons"
---

# All Buttons

{{< featured type="Mixin" name="all-buttons" >}}
**All Buttons** Sass mixin helps you to target all the HTML button elements in the DOM so you can easily apply your style rules to them.
{{< /featured >}}

## Arguments

{{< arguments/table footnote="You can call the mixin either at the root level of your style sheet to target all the HTML button elements in the DOM or call it in a parent selector to target its children.">}}
    {{< arguments/row name="$pseudo" type="string" description="Help you to select pseudo class selector of the selected button elements. Accepts `hover`, `focus`, `active`, `disabled`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin at the root level of your style sheet **to target all the HTML button elements**.
{{< highlight scss >}}
@include gls-all-buttons {
    background-color: teal;
    color: white;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
button,
[type="button"],
[type="reset"],
[type="submit"] {
    background-color: teal;
    color: white;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's style the **hover state** of the buttons.
{{< highlight scss >}}
@include gls-all-buttons(hover) {
    background-color: crimson;
    color: white;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
button:hover, [type='button']:hover, [type='reset']:hover, [type='submit']:hover {
    background-color: crimson;
    color: white;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, let's try to style all the states of the buttons elements and see how the generated code is looking.
{{< highlight scss >}}
@include gls-all-buttons {
    background-color: teal;
    color: white;
}
@include gls-all-buttons(hover) {
    background-color: teal;
    color: white;
}
@include gls-all-buttons(focus) {
    background-color: purple;
    color: white;
}
@include gls-all-buttons(active) {
    background-color: blue;
    color: white;
}
@include gls-all-buttons(disabled) {
    background-color: gray;
    color: black;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
button,
[type="button"],
[type="reset"],
[type="submit"] {
    background-color: teal;
    color: white;
}
button:hover, [type='button']:hover, [type='reset']:hover, [type='submit']:hover {
    background-color: teal;
    color: white;
}
button:focus, [type='button']:focus, [type='reset']:focus, [type='submit']:focus {
    background-color: purple;
    color: white;
}
button:active, [type='button']:active, [type='reset']:active, [type='submit']:active {
    background-color: blue;
    color: white;
}
button:disabled, [type='button']:disabled, [type='reset']:disabled, [type='submit']:disabled {
    background-color: gray;
    color: black;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Call the mixin in a selector to target only those button elements inside that selector.
{{< highlight scss >}}
.containing-element {
    @include gls-all-buttons {
        background-color: teal;
        color: white;
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.containing-element button, .containing-element [type='button'], .containing-element [type='reset'], .containing-element [type='submit'] {
    background-color: teal;
    color: white;
}
{{< /highlight >}}
{{< /highlightwrap >}}