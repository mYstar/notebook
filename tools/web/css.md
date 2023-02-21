# naming convention BEM
- block = standalone entity --> `list`
- element = part of an entity --> `list__item`
    - deeper nested elements are only refering to their block --> `list__subitem` instead of `list__item__subitem`
- modifier = flag to change style/behaviour --> `list__item--bold`