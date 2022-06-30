# flexbox
Flexbox - simple guide for myself

## 1. Flex-direction 
```flex-direction:row``` main-axis => x  | cross-axis => y
with ```flex-wrap``` and setting width to `.box` we can create 3 col layout 

```css
.container {
  display:flex;
  border:10px solid goldenrod;
  min-height:100vh;
  flex-wrap:wrap;
}
.box {
  width:33.3333333%;
}
```

## 2. Flex order
we set order to individual items

```css
.box {
  flex:1;
}

.box3 {
  order:1;
}

.box5 {
  order:2;
}
```
## 3. Flexbox Alignment and centering
### 3.1 justify-content

> alignment along the main axis 

- flex-start / center / flex-end - move whole bunch to those 3 positions
- space-between - move item to each side and give equal space to the rest 
- space-around - each has some space

if we change flex-direction to column and then add center -> it will be positioned at center of website:
```css
.container {
  display:flex;
  border:10px solid mistyrose;
  min-height:100vh;
  flex-direction: column;
  justify-content: center;
}
```
### 3.2 Align-items
 concerned with cross axis 
=> container must have some height 
by default is set to stretch

```css
.container {
  display:flex;
  border:10px solid mistyrose;
  height:100vh;
  align-items: center;
}
```

### 3.3 Align-content
```css
  
  .container {
      display:flex;
      flex-wrap: wrap;
      border:10px solid red;
      height:100vh;
      align-content: flex-start;
  }
  .box {
      width:33.333%;
  }
```

### 3.4 align-self
position in cross-axis every single elemtent
```css
  .container {
      display:flex;
      border:10px solid red;
      height:100vh;
      align-items:flex-start;
  }

  
  .box2 {
      align-self: flex-end;
  }
  .box3 {
      align-self: center;
  }
  .box4 {
    align-self:stretch;
   }
  ```
## 4. Flexbox Sizing 

- what to do with extra space 

 twice size (double amount that rest have )

```css
.box {
    flex:1;
}
.box2 {
    flex:2;
}
.box4 {
    flex:3;
}
```

### 4.1 grow / shrink / basis

`flex-grow` by default is 0 

below example : box1 will consume rest of space 

if we set `flex-grow:10` it will consume 10 of  extra space 

`flex-shrink` by deafault evenly divide 

`flex-shrink:10` - how much of myself give up in relation to other element 

```css
.box1 {
    flex-basis:400px;
    flex-grow:1;
}
.box2 {
    flex-basis:400px;
}
```



```css
flex:10 5 400px /* grow, shrink, basis */
```

### 4.2 Flex basis and wraping 

if we want to set size of each element and total width is beyond the width of screen 

we need to set `flex-wrap` for parent container and to deal with extra space `flex-grow` for individual element 

```css
  .container {
      display:flex;
     flex-wrap: wrap;
    }

.box {
    flex-basis: 500px;
    flex-grow: 1;
}
```

if we set grow bigger for particual element  - it will effect only row with element 

```css
.box3 {
    background:azure;
    flex-grow: 12;
}
```

if we want to work with column - flex direction and min-height (vh) and flex-grow to individual element

```css
  .container {
      display:flex;
     flex-wrap: wrap;
     flex-direction: column;
     min-height: 100vh;
    }

.box {
    flex-grow: 1;
}
```

assuming - individual element has `flex-basis` param 

if we set `height` instead of `min-height` we will get 2 columns instead of 1

```css
  .container {
     height: 100vh;
    }

.box {
    flex-basis: 200px;
    flex-grow: 1;
}

```

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


