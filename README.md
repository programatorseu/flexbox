## Flexbox

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


