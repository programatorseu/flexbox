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



