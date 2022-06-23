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
