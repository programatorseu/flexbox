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


