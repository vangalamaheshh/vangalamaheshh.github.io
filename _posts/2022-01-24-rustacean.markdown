---
layout: post
title:  "Getting Rusty!"
date:   2022-01-24
categories: Blog Programming Languages Rust  
---

![rust-logo](/assets/images/rust-logo.png)

If you were to ask me 2 weeks ago if I have any interest in learning a new programming language, I'd have outright said 'No'. Not that I am any shy to learn new technologies or languages, but because I was too misguided in my own thinking that ```Python``` for data science and ```Java``` for resilient applications have become pretty much the status quo and that any innovation in the compute space has to be with ```compute clusters``` and ```scalable databases```.

It was not until I decided to learn blockchain and smart contracts that I happened to cross paths with ```Rust```. Actually, my first stop was at ```Solidity```, a language on which ```Ethereum``` blockchain is built. However, ```Solidity``` didn't sit well with me. The syntax felt verbose and documentation seemed scarce. Then along came ```Rust``` and I am smitten with this language ever since. 

To describe ```Rust``` in one sentence: C++ efficiency and Java's robustness, only better!! 

<img src="/assets/images/rust-vs.png" alt="rust-versus" width="40%" />
<img src="/assets/images/rust-chart.png" alt="rust-chart" width="40%" />

I have a Github repo dedicated to all things ```Rust``` learning <a href="https://github.com/vangalamaheshh/rust-esh-cean" target="_blank">here</a>. Feel free to git clone and compose up to get ```Rusty```!

Hello world ....
================

{% highlight rust %}
fn main() {
  println!("Hello world!");
}
{% endhighlight %}

Rust Resources
===============
* <a href="https://doc.rust-lang.org/stable/book/" target="_blank">The Book</a>: Rust fundamentals to advanced concepts - all in one!
* <a href="https://tokio.rs/tokio/tutorial" target="_blank">Tokio</a>: Async programming with Rust!
* <a href="https://actix.rs/" target="_blank">Actix Web</a>: Web programming with Rust!
* <a href="https://async-graphql.github.io/async-graphql/en/index.html" target="_blank">Async-Graphql</a>: Building GraphQL APIs with Rust!
* <a href="https://docs.rs/datafusion/latest/datafusion/" target="_blank">Datafusion</a>: Data science in Rust!
* <a href="https://github.com/libp2p/rust-libp2p/tree/master/examples" target="_blank">LibP2P</a>: Peer-to-Peer Applications in Rust!

I try to share some of the topics that I found intriguing in ```Rust``` especially coming from ```Java```, ```Perl``` and ```Python``` background. An FYI - I will continually update this post with more and more snippets as I go.

Variables - Immutable, Mutables & Shadowing
============================================

{% highlight rust %}
fn main() {
  let x = 1;
  println!("{}", x); // prints 1
  x = 2; // errors out since x is immutable
  println!("{}", x); 
}
{% endhighlight %}

```
Compilation error:
x = 2; // errors out since x is immutable
^^^^^ cannot assign twice to immutable variable
```

{% highlight rust %}
fn main() {
    let mut x = 1;
    println!("{}", x); // prints 1
    x = 2; // it works since x is now mutable
    println!("{}", x); // prints 2
}
{% endhighlight %}

{% highlight rust %}
fn main() {
    let x = 1;
    println!("{}", x); // prints 1
    {
        let x = 2; // shadowing 
        println!("{}", x); // prints 2
    }
    println!("{}", x); // prints 1
}
{% endhighlight %}


Constants
==========

{% highlight rust %}
fn main() {
    const MINUTES_IN_A_DAY: usize = 60 * 24; // this works
    println!("{}", MINUTES_IN_A_DAY);
    const SECONDS_IN_DAY: usize = get_seconds_in_day(); // this does not
    println!("{}", SECONDS_IN_DAY);
}

pub fn get_seconds_in_day() -> usize {
    return 60 * 60 * 24;
}
{% endhighlight %}

```
Compilation error:
const SECONDS_IN_DAY: usize = get_seconds_in_day();
calls in constants are limited to constant functions, tuple structs and tuple variants
```

Character
=========
A ```char``` is denoted by single quotes while ```String``` by double quotes. A ```char``` in ```Rust``` is 4 bytes in size and can store not just ASCII but unicode values.

Tuples
=======
A Tuple can be heterogenous. A tuple has to be fixed in size. Tuple values are accessed using either dot notation or by unpacking. A tuple can be empty - (). Tuples get stored on stack.

{% highlight rust %}
fn main() {
    let t: (i32, f32, String, char) = (10, 64.2, String::from("Hello"), '!');
    println!("{}, {}, {}, {}", t.0, t.1, t.2, t.3);
}
{% endhighlight %}

Arrays
=======
Arrays are homogenous and are fixed in size. Arrays get stored on stack. Array elements are accessed using [], for example, array[0].

{% highlight rust %}
fn main() {
    let array: [&str;2] = ["Jan", "Feb"];
    println!("{:?}", array);
    let array = [1,2,3,4,5]; // remember shadowing; otherwise compiler throws error as the variable declared as immutable
    println!("{:?}", array);
    println!("The length of array is: {}", array.len()); // prints 5
}
{% endhighlight %}

Happy Coding in ```Rust```!! :+1:

<a href="https://www.buymeacoffee.com/MaheshVangala" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee" height="41" width="174"></a>

<div id="share-bar">

    <h4 class="share-heading">Liked it? Please share the post.</h4>

    <div class="share-buttons">
        <a class="horizontal-share-buttons" target="_blank" href="https://www.facebook.com/sharer/sharer.php?u=https://vangalamaheshh.github.io{{page.url}}" 
            onclick="gtag('event', 'Facebook', {'event_category':'Post Shared','event_label':'Facebook'}); window.open(this.href, 'pop-up', 'left=20,top=20,width=500,height=500,toolbar=1,resizable=0'); return false;"
            title="Share on Facebook" >
            <span class="icon-facebook2">Facebook</span>
        </a>
        <a  class="horizontal-share-buttons" target="_blank" href="https://twitter.com/intent/tweet?text=Getting Rusty!&url=https://vangalamaheshh.github.io{{page.url}}"
            onclick="gtag('event', 'Twitter', {'event_category':'Post Shared','event_label':'Twitter'}); window.open(this.href, 'pop-up', 'left=20,top=20,width=500,height=500,toolbar=1,resizable=0'); return false;"
            title="Share on Twitter" >
            <span class="icon-twitter">Twitter</span>
        </a>
        <a  class="horizontal-share-buttons" target="_blank" href="http://www.reddit.com/submit?url=https://vangalamaheshh.github.io{{page.url}}"
          onclick="gtag('event', 'Reddit', {'event_category':'Post Shared','event_label':'Reddit'}); window.open(this.href, 'pop-up', 'left=20,top=20,width=900,height=500,toolbar=1,resizable=0'); return false;"
          title="Share on Reddit" >
          <span class="icon-reddit">Reddit</span>
        </a>
        <a  class="horizontal-share-buttons" target="_blank" href="https://www.linkedin.com/shareArticle?mini=true&url=https://vangalamaheshh.github.io{{page.url}}"
          onclick="gtag('event', 'LinkedIn', {'event_category':'Post Shared','event_label':'LinkedIn'}); window.open(this.href, 'pop-up', 'left=20,top=20,width=500,height=500,toolbar=1,resizable=0'); return false;"
          title="Share on LinkedIn" >
          <span class="icon-linkedin">LinkedIn</span>
        </a>
    </div>

</div>
<style type="text/css">
/* Share Bar */
#share-bar {
    font-size: 20px;
    border: 3px solid #7de77b;
    border-radius: 0.3em;
    padding: 0.3em;
    background: rgba(125,231,123,.21)
}

.share-heading {
    margin-top: 0px;
}

/* Title */
#share-bar h4 {
    margin-bottom: 10px;
    font-weight: 500;
}

/* All buttons */
.share-buttons {
}

.horizontal-share-buttons {
    border: 1px solid #928b8b;
    border-radius: 0.2em;
    padding: 0.2em;
    margin-right: 0.2em;
    line-height: 2em;
}

/* Each button */
.share-button {
    margin: 0px;
    margin-bottom: 10px;
    margin-right: 3px;
    border: 1px solid #D3D6D2;
    padding: 5px 10px 5px 10px;
}
.share-button:hover {
    opacity: 1;
    color: #ffffff;
}

/* Facebook button */
.icon-facebook2 {
    color: #3b5998;
}

.icon-facebook2:hover {
    background-color: #3b5998;
    color: white;
}

/* Twitter button */
.icon-twitter {
    color: #55acee;
}
.icon-twitter:hover {
    background-color: #55acee;
    color: white;
}

/* Reddit button */
.icon-reddit {
    color: #ff4500;
}
.icon-reddit:hover {
    background-color: #ff4500;
    color: white;
}

/* Hackernews button */
.icon-hackernews {
    color: #ff4500;
}

.icon-hackernews:hover {
    background-color: #ff4500;
    color: white;
}

/* LinkedIn button */
.icon-linkedin {
    color: #007bb5;
}
.icon-linkedin:hover {
    background-color: #007bb5;
    color: white;
}

</style>

