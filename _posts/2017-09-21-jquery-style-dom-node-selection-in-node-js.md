---
layout: post
title:  "Jquery style DOM Node selection in NodeJS"
author: "Shalitha Suranga"
---

If you worked with some frontend developments you know how useful JQuery's selectors. Suppose you need to select some internal text of some html portion using NodeJs. Then it is called web scraping. When you search npm registery you will find out many modules for web scraping.

I used [https://github.com/cheeriojs/cheerio](cheerio) to build an awesome w3c and link validator (You can find [here](https://github.com/99xt/w3c-link-validator)) and Basically I wanted to check existance of some tags, attributes of specific tag and get anchor contents.

Special thing is that cheeriojs offers very similar working environment as same as JQuery. Then you can use css selectors to select HTML elements as you wish.

#### Install Cheerio

```bash
npm install cheerio --save
```

#### Simple Example of cheerio

```Javascript
const cheerio = require('cheerio')
const $ = cheerio.load('<h2 class="title">Hello world</h2>')

$('h2.title').text('Hello there!')
$('h2').addClass('welcome')

$.html()
//=> <h2 class="title welcome">Hello there!</h2>
```
