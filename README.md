## Flexbox

1-dimenional content

- taking bunch of items of different sizes / return the besat layout for those items

```html
    <div class="wrapper">
      <main class="content">
        <article>
          <p>
            This is an article of content that sits inline with a sidebar. There’s not
            enough room in the viewport at the moment so it’s all very squished.
          </p>
        </article>
      </main>
      <aside class="sidebar">
        <p>This is a sidebar that is squished.</p>
      </aside>
    </div>
```

```css
html {
  box-sizing:border-box;
  font-family:'Roboto', 'Lato';
  font-size:15px;
}
*, *:after, *:before {
  box-sizing:inherit;
}

body {
  max-width:50rem;
  padding:2rem;
  border:1px solid #d2d2d2;
  background:#d6d3ef;
  margin:1rem auto;
}
.wrapper {
  display:flex;
  flex-wrap:wrap;
} 
.wrapper > * {
  padding:1rem;
}
.wrapper {
  background:white;
  border:1px solid #c2c2c2;
}
.sidebar {
  background:#e8f0fe;
  flex-grow:1;
  flex-basis:12rem;
}
.content {
  flex-basis:0;
  flex-grow:2;
  min-width:70%;
}
```



**main axis and cross axis**

=> if `flex-direction` set to row 

> main-axis - row | cross-axis - column



**flex container**

```html
<div class="container" id="container">
  <div>One</div>
  <div>Item two</div>
  <div>The item we will refer to as three</div>
</div>
```

```css
.container {
  display: flex;
}
```

give you a block-level box, with flex item children

- `row`: the items lay out as a row.
- `row-reverse:` the items lay out as a row from the end of the flex container.
- `column`: the items lay out as a column.
- `column-reverse` : the items lay out as a column from the end of the flex container.

**wrapping flex items**

The initial value of the `flex-wrap` property is `nowrap`. This means that if there is not enough space in the container the items will overflow.



when flex container wraps: 

- creates multiple flex lines 

```css
.container {
  display: flex;
  flex-wrap: wrap;
}
```

with flex-flow we can control direction and wrapping

```css
.container {
  display: flex;
  flex-flow: column wrap;
}
```



**controlling space inside flex items**

- our container can have more space than is needed to display items

> items line up at the start do not grow to fill space 

*initial value of* `flex-` is : 

- `flex-grow: 0`: items do not grow.

- `flex-shrink: 1`: items can shrink smaller than their `flex-basis`.

- `flex-basis: auto`: items have a base size of `auto`.

  

  if we set `flex:auto`:



`flex-grow: 1`: items can grow larger than their `flex-basis`.

`flex-shrink: 1`: items can shrink smaller than their `flex-basis`.

`flex-basis: auto`: items have a base size of `auto`.



if we set `flex:1`

- `flex-grow: 1`: items can grow larger than their `flex-basis`.
- `flex-shrink: 1`: items can shrink smaller than their `flex-basis`.
- `flex-basis: 0`: items have a base size of `0`.





```css
.item1 {
  flex: 1 1 auto;
}

.item2 {
  flex: 2 1 auto;
}
```

`flex-basis` of `auto` is to allow the browser to figure out space distribution.



**flexbox alignment**

basically : working on main axis we use `justify-` / cross axis : `align-`

- **properties for space distribution**

​	`justify-content`: space distribution on the main axis.

​	`align-content`: space distribution on the cross axis.

​	`place-content`: a shorthand for setting both of the above properties.

**alignment **

- `align-self`: aligns a single item on the cross axis
- `align-items`: aligns all of the items as a group on the cross axis



### Distribute space on main axis 

initial value of `justify-content` is `flex-start`

If your items fill the axis then there is no space to share out so the property won't do anything.

```css
.container {
  display: flex;
  justify-content: flex-end;
}
```

**options we have **

- flex-start / flex-end
- space-around / space-evenly / space-between 

- center



if we change to `flex-direction` to `column`

- we need to give our container height 

```css
.container {  
display: flex;
  max-width: 30rem;
  height: 25rem;
  flex-direction: column;
  gap: 1rem;
}
```

**distribute space between flex lines**

- `align-content` by deafult is set to stretch 

we need to remeber about : 

`flex-wrap`

`heigh` or `min-height` for container 

**place-content**

 set both `justify-content` and `align-content`

if you specify both the first is used for `align-content` and the second for `justify-content`.





### 4.3 Cross browser - flexbox auto-prefixer 

Many options: 

autoprefixer.github.io -> 1 option 

codekit or other app

#### Create Own Observer or Watcher 

**requirements**

1) npm 
2) gulp 

**steps**

1. Curl Command-Line Tool ; 

```bash
sudo apt install curl
```

-  nodejs  - follow instructions 

https://github.com/nodesource/distributions/blob/master/README.md#debinstall

```bash
# Using Ubuntu
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs

# Using Debian, as root
curl -fsSL https://deb.nodesource.com/setup_18.x | bash -
apt-get install -y nodejs
```

in our folder  - create package.json 

install gulp globally / local version

```bash
npm init
npm install gulp -g
npm install gulp --save-dev
npm install gulp-autoprefixer
touch gulpfile.js
```

 

```js
var gulp = require('gulp');
const autoprefixer = require('gulp-autoprefixer');
gulp.task('prefix', () =>
    gulp.src('style.css')
        .pipe(autoprefixer({
            cascade: false
    }))
    .pipe(gulp.dest('style'))
);
```
## 5. Menu

```html
<div class="container">
  <nav class="flex-nav">
  <ul>
    <li><a href="#">item 01</a></li>
    ..
    <li class="social"><a href=""><i class="fab fa-twitter"></i></a></li>
  </ul>
</nav>
</div>
```

```css
.container{
  max-width:1000px;
  margin:0 auto;
  padding: 50px;
}
.flex-nav ul {
   
  list-style: none;
  margin: 0;
  padding: 0;
  display:flex;
 
}
.flex-nav li {
  flex:3;
}
.flex-nav .social {
  flex:1;
}

@media all and (max-width:1000px) {
  .flex-nav ul {
   flex-wrap:wrap;
  }
  .flex-nav li {
    flex: 1 1 50%;
  }
  .flex-nav .social {
    flex:1 1 25%;
  }
}
@media all and(max-width:500px) {
  .flex-nav li {
    flex-basis:100%;
  }
}
```
## 5. Equal columns height trick

simple html: 
```html
.wrapper>.item*16
```

css: 
```css
.wrapper {
  display: flex;
  flex-wrap: wrap;
}
.item {
  margin:10px;
  padding:20px;
  font-size: 30px;
  flex:1 1 calc(33.33% - 20px);
}
```


