---
title: My desktop setting Part 1
subtitle: Let's make everything look prettier
date: 2019-11-05
category: Tools
layout: postwip
tags: CSS Tools HTML Javascript
imgLink: /blog/img/nov-2019/setup1.jpg
comments: true
permalink: "/tools/setup-env-pt1.html"
identifier: envsetup01
imgcard: https://mariodena.github.io/blog/img/nov-2019/setup1.jpg
---

I've read a lot about the importance of having a comfortable, cool and organized development environment, and we all love to customize our desktop or laptop to be ours and match our personality. _(if you don't you should)_ So, let's do just that shall we?

## Visuals matter.

Like my favorite youtuber said. **You need to have a comfortable work-environment**, because you will be sitting in front of your computer for hours and hours a day and if your desktop is a mess, your keyboard is dirty, your computer takes 3 hours to boot or you simply have unorganized files everywhere on your OS. Chances are, you don't want to be there. So let's work on that. _(there is nothing I can do about your phisical desktop and your dirty keyboard)_

This is my desktop:

At least for me, when I boot up my computer, I get a nice feeling just because it looks _(In my opinion)_ as the working machine of some kind of hacker or at least someone that knows what hes doing _(even though I don't **I feel** like I do)_ So, in order to get that I need a lot of things but first of all, I need a sable OS.

I've tried the most popular linux distros like Ubuntu, Linux Mint, Manjaro, Kubuntu, KDE Neon, Elementary and so on. But above all of them I choose MX Linux, the reason is simple. It's really stable, easy to use _(Debian based)_, fast _(xfce desktop)_ and have the best set of tools for customization I've encounter so far.

I get questions from my peers about the "Thing" I have on the right side of my desktop, so That's what I want to share with you today. It's a system monitor with some data about my prossesor usage, memory, internet etc... It's called conky. 



`BEM` stands for **Block-Element-Modifier** and it's basically a [naming convention][nc]{:target="_blank"} or set of rules you can use to name your `HTML elements` _(with classes)_. Since it's not a framework or a piece of software, you can simply start using it now.

You can watch [this video][ytv]{:target="_blank"} for a quick run-down.



Simple as it sounds, **it's a fantastic tool**. You can use and _modify*_ it to your needs. And if used right, you will get **clean, readable, reusable and easy to maintain** code, both for your `HTML` and your `CSS`.

## So, what BEM can do for you?

Let's say we want to make a `navbar` and we have our general layout looking like this:

{% highlight html %}
<div class="container">
  <ul>
    <li>item</li>
    <li>item</li>
    <li>item</li>
    <li>item</li>
  </ul>
  <button><p>Sign in</p></button>
  <button><p>Action</p></button>
  <img src="" alt="logo" />
</div>
{% endhighlight %}

We can always try to be specific with our [selectors][sl]{:target="_blank"}, and style doing something similar to this:

{% highlight css %}
.container > ul {
  display: flex;
}
{% endhighlight %}

However as the files grow bigger _(both HTML and CSS)_ you'll have to remember what is what the whole time, and **that will be a problem in the long run.** As a student, I learned we should use classes for styling, [never use IDs for styling][nv]{:target="_blank"} and some general [best practices][bp]{:target="_blank"}.

For example:

{% highlight html %}
<div class="container">
  <ul class="menuList">
    <li>item</li>
    ......
{% endhighlight %}

There _seems_ to be nothing wrong with the code above, but, what if you have more than one `menuList` on your website? What if we want _them_ to look different?

Then we have to be more specific, and use less generic but equally descriptive names. And here is where `BEM` will help us out.

{% highlight html %}
<div class="mainNavBar">
  <ul class="mainNavBar__menuList">
    <li>item</li>
    ...
{% endhighlight %}

{% highlight css %}
.mainNavBar {
  display: flex;
  width: 100vw;
  height: 45px; 
}

.mainNavBar__menuList{
  display: flex;
}
{% endhighlight %}

So we name our `block` with a descriptive name, and use double underscores for our elements `__element`. 

The code is clean and easy to maintain, even if I come back to it a month or a year after writing it, **I would know just by reading the names what every part of my code represents.**

## Naming hierarchy is a bit different.

Ok! Now let's get into something *really* interesting about `BEM`. What would you do with our `li` elements? Well, you might be inclined to do something like this:

{% highlight html %}
<div class="mainNavBar">
  <ul class="mainNavBar__menuList">
    <li class="mainNavBar__menuList__menuItem">item</li>
    ...
{% endhighlight %}

While the code above would work, we have to remember, **in BEM the [hierarchy][hc]{:target="_blank"} is defined by our naming standard** and not by our HTML _(at least not as much)_. So we can either leave it as a `li` element or we could do, this:

{% highlight html %}
<div class="mainNavBar">
  <ul class="mainNavBar__menuList">
    <li class="mainNavBar__menuItem">item</li>
    ...
{% endhighlight %}

{% highlight css %}
.mainNavBar {
  display: flex;
  width: 100vw;
  height: 45px; 
}

.mainNavBar__menuList{
  display: flex;
}

.mainNavBar__menuItem{
  font-size: 16px;
}
{% endhighlight %}

What I love about this approach is we can get **single class elements** for styling, while keeping everything organized. However, as our site grows _(or if we want to go crazy with styling)_ we will find ourselves in need of something even more specific, and here is where modifiers come in handy.

## Using modifiers and modding BEM!

Imagine we want only one element in our list to be in _italics_. The `BEM` way to do it is with something like this:

{% highlight html %}
<div class="mainNavBar">
  <ul class="mainNavBar__menuList">
    <li class="mainNavBar__menuItem">item</li>
    <li class="mainNavBar__menuItem mainNavBar__menuItem--italics">item</li>
    ...
{% endhighlight %}

{% highlight css %}
.mainNavBar {
  display: flex;
  width: 100vw;
  height: 45px; 
}

.mainNavBar__menuList{
  display: flex;
}

.mainNavBar__menuItem{
  font-size: 16px;
}

.mainNavBar__menuItem--italics{
  font-style: italic;
}

{% endhighlight %}

So, now we have our `block` our `__element` and following the double dash standard our `--modifier`.

What's so cool about this, and what I love the most, is that we can _bend_ the rules a little bit. **This is entirely a personal preference** and my way to _(sometimes)_ deal with my modifiers. 

So, if my modifier is so simple _(making changes to the font style)_, I then add it to my CSS along with all my helper classes like this:

{% highlight css %}
.--italics{
  font-style: italic;
}

.--bold{
  font-weight: bold;
}
{% endhighlight %}

Now we are not following the `BEM` standards, but **we made our own modification,** _(for more complicated styles I do follow BEM)_ and our `HTML` is clean and has great [readability][rd]{:target="_blank"}:

{% highlight html %}
<div class="mainNavBar">
  <ul class="mainNavBar__menuList">
    <li class="mainNavBar__menuItem">item</li>
    <li class="mainNavBar__menuItem --italics">item</li>
    ...
{% endhighlight %}

## In conclusion...

**I find it amazing that it's so easy and it offers so much.** Our code is readable, easy to maintain and we have a lot of [reusable code][ruc]{:target="_blank"}.

Of course, there are other methodologies to keep your code clean like [SMACSS][smacss]{:target="_blank"} or [Atomic][atm]{:target="_blank"}, however, `BEM` is a super simple, easy and powerful tool anyone can start using from day one. And if you add [SASS][sass]{:target="_blank"} to it... Well, that's just **a thing of beauty.**

So, if you are learning CSS and HTML, or if you have some intermediate knowledge but struggle with organizing your code, **I recommend you to go and read the [BEM docs][bem]{:target="_blank"} and start implementing it.**

Remember you can do small modifications to the rules as you see fit, however you should stick to the standard until you master BEM.

Cheers!

![meme][img1]{:class="postImageGeneral"}


[ytv]: https://www.youtube.com/watch?v=1fW8v4ErK10
[img1]: /blog/img/oct-2019/memeBEM.jpg
[ruc]: https://en.wikiversity.org/wiki/Visual_Basic_.NET/Reusable_Code
[hc]: http://webreference.com/html/rendering/index-2.html
[nv]: https://css-tricks.com/almanac/selectors/i/id/
[sass]: https://sass-lang.com/
[bp]: https://csswizardry.com/2012/11/code-smells-in-css/
[rd]: https://en.wikipedia.org/wiki/Readability
[bem]: http://getbem.com/
[atm]: https://github.com/nemophrost/atomic-css/
[smacss]: http://smacss.com/
[nc]: https://en.wikipedia.org/wiki/Naming_convention/
[sl]: https://www.sitepoint.com/css-selectors/