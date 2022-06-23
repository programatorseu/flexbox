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
