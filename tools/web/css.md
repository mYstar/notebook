- `content:url("image.jpg")`: change image

# naming convention BEM
- block = standalone entity --> `list`
- element = part of an entity --> `list__item`
    - deeper nested elements are only refering to their block --> `list__subitem` instead of `list__item__subitem`
- modifier = flag to change style/behaviour --> `list__item--bold`

# square trick
- the padding is relative to width and not height
```
.square {
  position: relative;
  width: 50%; // adjust to needs
}

.square:after {
  content: "";
  display: block;
  padding-bottom: 100%; // relative to width
}

.content {
  position: absolute;
  width: 100%;
  height: 100%;
}
```