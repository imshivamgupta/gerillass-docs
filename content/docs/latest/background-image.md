---
title: "Background Image"
---

# Background Image

{{< mixin type="Mixin" name="background-image" >}}
**Background Image** Sass mixin allows you to apply background images to the selected element(s). Provides an easy to use one-line method.
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="Use `null` if you want to skip an argument. For more see [the examples](#examples).">}}
    {{< arguments/row name="$image-url" type="string" description="The URL link of the background image." >}}
    {{< arguments/row name="filter-color" type="color | list" description="The color or the list of colors you may want to apply as a filter over the background image. **Multiple color values must be seperated by space.**" >}}
    {{< arguments/row name="$filter-direction" type="string" description="The angle of gradient's direction. **It can be activated only when you pass multiple color values for `$filter-color` argument**. Accpets `top`, `top-right`, `right`, `bottom-right`, `bottom`, `bottom-left`, `left`, `top-left` values. The default value is set `to top`." >}}
{{< /arguments/table >}}


## Examples

{{< highlightwrap class="example">}}
Simply call the mixin in selector and pass the URL of the background image.
{{< highlight scss >}}
.element{
    @include gls-background-image("https://i.picsum.photos/id/1018/3914/2935.jpg");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    position: relative;
    background-image: url("https://i.picsum.photos/id/1018/3914/2935.jpg");
    background-position: center center;
    background-repeat: no-repeat;
    background-size: cover;
}
{{< /highlight >}}
{{< sandbox class="xlarge" >}}
position: relative;background-image: url("https://i.picsum.photos/id/1018/3914/2935.jpg");background-position: center center;background-repeat: no-repeat;background-size: cover;
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's apply a color filter to it by passing a value for $filter-color argument.
{{< highlight scss >}}
.element{
    @include gls-background-image("https://i.picsum.photos/id/1018/3914/2935.jpg", rgba(teal, 0.3));
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    position: relative;
    background-image: url("https://i.picsum.photos/id/1018/3914/2935.jpg");
    background-position: center center;
    background-repeat: no-repeat;
    background-size: cover;
}
.element::after {
    content: "";
    display: block;
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 128, 128, 0.3);
}
.element > * {
    position: relative;
    z-index: 1;
}
{{< /highlight >}}

<style>
.element.example02 {
    position: relative;
    background-image: url("https://i.picsum.photos/id/1018/3914/2935.jpg");
    background-position: center center;
    background-repeat: no-repeat;
    background-size: cover;
    overflow: hidden;
}
.element.example02::after {
    content: "";
    display: block;
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 128, 128, 0.3);
}
.element.example02 > * {
    position: relative;
    z-index: 1;
}
</style>
<div class="element sandbox xxlarge example02"></div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's pass multiple color values for `$filter-color` to make background image look even more interesting. **Multiple color values must be seperated by space**.
{{< hint info >}}
**Tip:** When you pass multiple color values, **Gerillass' Linear Gradient mixin** works in the background to generate a beautiful gradient color filter.
{{< /hint >}}
{{< highlight scss >}}
.element{
    @include gls-background-image("https://i.picsum.photos/id/1018/3914/2935.jpg", rgba(teal, 0.3) rgba(black, 0.8));
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    position: relative;
    background-image: url("https://i.picsum.photos/id/1018/3914/2935.jpg");
    background-position: center center;
    background-repeat: no-repeat;
    background-size: cover;
}
.element::after {
    content: "";
    display: block;
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(to top, rgba(0, 128, 128, 0.3), rgba(0, 0, 0, 0.6));
}
.element > * {
    position: relative;
    z-index: 1;
}
{{< /highlight >}}

<style>
.element.example03 {
  position: relative;
  background-image: url("https://i.picsum.photos/id/1018/3914/2935.jpg");
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
  overflow: hidden;
}
.element.example03::after {
  content: "";
  display: block;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: -webkit-gradient(linear, left bottom, left top, from(rgba(0, 128, 128, 0.3)), to(rgba(0, 0, 0, 0.6)));
  background: linear-gradient(to top, rgba(0, 128, 128, 0.3), rgba(0, 0, 0, 0.6));
}
.element.example03 > * {
  position: relative;
  z-index: 1;
}
</style>
<div class="element sandbox xxlarge example03"></div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's try `$filter-direction` option, and while trying it, let's use sharper color transitions to see the effect clearly.
{{< highlight scss >}}
.element{
    @include gls-background-image("https://i.picsum.photos/id/1018/3914/2935.jpg", rgba(teal, 0.7) rgba(pink, 0.8), right);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    position: relative;
    background-image: url("https://i.picsum.photos/id/1018/3914/2935.jpg");
    background-position: center center;
    background-repeat: no-repeat;
    background-size: cover;
}
.element::after {
    content: "";
    display: block;
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(to right, rgba(0, 128, 128, 0.7), rgba(255, 192, 203, 0.8));
}
.element > * {
    position: relative;
    z-index: 1;
}
{{< /highlight >}}

<style>
.element.example04 {
  position: relative;
  background-image: url("https://i.picsum.photos/id/1018/3914/2935.jpg");
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
  overflow: hidden;
}
.element.example04::after {
  content: "";
  display: block;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: -webkit-gradient(linear, left top, right top, from(rgba(0, 128, 128, 0.7)), to(rgba(255, 192, 203, 0.8)));
  background: linear-gradient(to right, rgba(0, 128, 128, 0.7), rgba(255, 192, 203, 0.8));
}
.element.example04 > * {
  position: relative;
  z-index: 1;
}
</style>
<div class="element sandbox xxlarge example04"></div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
There will be times when you would like to **add a background image on an element by using style attribute** like in the example below. **In such cases just use `null` to skip `$image-url` argument**.
{{< highlight html >}}
<div class="element" style="background-image: url(https://i.picsum.photos/id/1018/3914/2935.jpg)"></div>
{{< /highlight >}}
{{< highlight scss >}}
.element{
    @include gls-background-image(null, rgba(teal, 0.7) rgba(pink, 0.8), right);
}
{{< /highlight >}}
<style>
.element.example05 {
  position: relative;
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
}
.element.example05::after {
  content: "";
  display: block;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: -webkit-gradient(linear, left top, right top, from(rgba(0, 128, 128, 0.7)), to(rgba(255, 192, 203, 0.8)));
  background: linear-gradient(to right, rgba(0, 128, 128, 0.7), rgba(255, 192, 203, 0.8));
}
.element.example05 > * {
  position: relative;
  z-index: 1;
}
</style>
<div class="element sandbox xxlarge example05" style="background-image: url(https://i.picsum.photos/id/1018/3914/2935.jpg)"></div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Probably you're asking why those `"position: relative"` and `"z-index: 1"` style rules applied to the direct children of the selected element. **These style rules are exist to prevent color filters from overlying the direct children**.

Let's try with a title text that placed inside the selected element and see it in action. 
{{< highlight html >}}
<div class="element">
    <h2 class="title">A beautiful title text standing over the color filter.</h2>
</div>
{{< /highlight >}}
{{< highlight scss >}}
.element{
    @include gls-background-image("https://i.picsum.photos/id/1018/3914/2935.jpg", rgba(teal, 0.7) rgba(pink, 0.8), right);
}
{{< /highlight >}}
{{< highlight css "linenos=table,hl_lines=19-22,linenostart=1">}}
//CSS Output
.element {
    position: relative;
    background-image: url("https://i.picsum.photos/id/1018/3914/2935.jpg");
    background-position: center center;
    background-repeat: no-repeat;
    background-size: cover;
}
.element::after {
    content: "";
    display: block;
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(to right, rgba(0, 128, 128, 0.7), rgba(255, 192, 203, 0.8));
}
.element > * {
    position: relative;
    z-index: 1;
}
{{< /highlight >}}
<style>
.element.example06 {
    border-radius: 5px;
    display: -webkit-box;
    display: flex;
    -webkit-box-pack: center;
    justify-content: center;
    -webkit-box-align: center;
    align-items: center;
    position: relative;
    background-image: url("https://i.picsum.photos/id/1018/3914/2935.jpg");
    background-position: center center;
    background-repeat: no-repeat;
    background-size: cover;
    padding: 30px;
}
.element.example06 .title {
    color: white;
    text-align: center;
    margin: 0;
}
.element.example06::after {
    content: "";
    display: block;
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background: -webkit-gradient(linear, left top, right top, from(rgba(0, 128, 128, 0.7)), to(rgba(255, 192, 203, 0.8)));
    background: linear-gradient(to right, rgba(0, 128, 128, 0.7), rgba(255, 192, 203, 0.8));
}
.element.example06 > * {
    position: relative;
    z-index: 1;
}
</style>

<div class="element sandbox large example06">
    <h2 class="title">A beautiful title text standing over the color filter.</h2>
</div>

{{< /highlightwrap >}}




