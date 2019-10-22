---
title: What is BEM?!
subtitle: And why you should start using it!
date: 2019-10-21
category: CSS
layout: post
tags: CSS Tools HTML BEM
permalink: "/tools/what-is-bem.html"
---

`BEM` stands for Block-Element-Modifier and it's basicaly a [naming convention][nc], or set of rules you can use when creating your HTML elements to give them classes, no installation needed no prerequisites, you can simply start using it.

Simple as it sounds, **it's a fantastic tool**. You can use and _modify_ it to your needs. And if used right, you will get **clean, readable, reusable and easy to maintain** code. Both for your HTML and your CSS.

Well. At least for me.

**So, let's see what `BEM` can do for us.**

Let's say we want to make a `navbar` and we have our general layout looking like this:

**HTML:**

{% highlight html %}

<div class="container">
  <img src="" alt="logo" />
  <ul>
    <li>item</li>
    <li>item</li>
    <li>item</li>
    <li>item</li>
  </ul>
  <button><p>Sign in</p></button>
  <button><p>Action</p></button>
</div>
{% endhighlight %}

**CSS:**

{% highlight css %}
.container {
display: flex;
width: 100vw;
height: 50px;
background-color: lightgray;
margin: 0;
padding: 0;
justify-content: flex-end;
align-items: center;
}

.container img {
max-height: 40px;
margin-right: auto;
}

.container img:hover {
cursor: pointer;
}

ul {
display: flex;
}

li {
font-style: italic;
font-size: 16px;
}

button{
background-color: red;
border-radius: 2px;
}

button p{
font-family: sans-serif;
}
{% endhighlight %}

As you can see, this example is kind of an exageration, _(I hope)_, you can see the code is neither readable nor easy to maintain, any change requiered, as simple as just changing the font to a single element, will requiere you to know by memory what is what.

Another problem is, every single `ul`, `li` and `button` in our `HTML` will take the same style, and with time, our CSS will be full of lost classes in a sea of repeated rules.

Now, the HTML can look clean, but it's [readability][rd] could be improuved and in fact I think it needs to be. It's obvious we need to do something. _(just imagine a classless html of 1000 lines)_

**Now let's compare our code after applying Block-Element-Modifier to it.**

**HTML:**

{% highlight html %}
<div class="navBar">
  <img class="navBar__logo "src="" alt="logo" />
  <ul class="navBar__Menu">
    <li class="navBar__menuItem">item</li>
    <li class="navBar__menuItem navBar__menuItem--red">item</li>
    <li class="navBar__menuItem">item</li>
    <li class="navBar__menuItem">item</li>
  </ul>
  <button class="navBar__button"><p class="navBar__text">Sign in</p></button>
  <button class="navBar__button navBar__button--action"><p class="navBar__text navBar__text--blue">Action</p></button>
</div>
{% endhighlight %}

**CSS:**

{% highlight css %}
.navBar {
  display: flex;
  width: 100vw;
  height: 50px;
  background-color: lightgray;
  margin: 0;
  padding: 0;
  justify-content: flex-end;
  align-items: center;
}

.navBar__logo {
  max-height: 40px;
  margin-right: auto;
}

.navBar__logo:hover {
  cursor: pointer;
}

.navBar__Menu {
  display: flex;
}

.navBar__menuItem {
  font-style: italic;
  font-size: 16px;
}

.navBar__menuItem--red {
  color: red;
}

.navBar__button {
  background-color: red;
  border-radius: 2px;
}

.navBar__text {
  font-family: sans-serif;
}

.navBar__text--red {
  color: red;
}
{% endhighlight %}

I don't know guys, for me both the `HTML` and `CSS` look a lot more readable, and our `CSS` is now not only readable, the **code is reusable, modifications to single elements are easy to do**, and thus maintaining it is a piece of cake.

In conclusion, I see no reason that stops me from implementing BEM standars to my future projects.

Of course there are other methodologyes to keep your code clean like [SMACSS][smacss] or [Atomic][atm], however, `BEM` is super simple and easier to implement.

My recommendation is that you read the [BEM docs][bem] and try it right now, of course your code can be even better if you apply the [best paractices][bp], and, will became a thing of beauty if you add [SASS][sass] to it. However just a small change on how you work with your styles and names and implementing `BEM` in your projects will save you alot of time.

Just remember, [never use ID's for styling][nv]!


[nv]: https://css-tricks.com/almanac/selectors/i/id/
[sass]: https://sass-lang.com/
[bp]: https://csswizardry.com/2012/11/code-smells-in-css/
[rd]: https://en.wikipedia.org/wiki/Readability
[bem]: http://getbem.com/
[atm]: https://github.com/nemophrost/atomic-css/
[smacss]: http://smacss.com/
[nc]: https://en.wikipedia.org/wiki/Naming_convention/
