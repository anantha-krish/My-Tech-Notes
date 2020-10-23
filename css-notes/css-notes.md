---
title: "CSS Notes"
tags: ""
---

css for sliding background fill buttons/links

SCSS 

```scss
 &__link{
        &:link,&:visited
             //add inline block
            display: inline-block;
            font-size: 3rem;
            font-weight: 300;
            padding: 1rem 2rem;
            text-decoration: none;
            color: $color-white;
            text-transform: uppercase;
            background-image:linear-gradient(120deg, transparent 0%, transparent 50%, $color-white 50%) ;
            transition: all .4s;
            //moves the background to right side
            background-size:230%;
        }
        &:hover,&:active{
            //moves the background to left
            background-position: 100%;
            color: $primary;
            transform: translateX(1rem);
        }
    }
```

HTML code

```html
 <ul class="navigation__list">
          <li class="navigation__item"><a href="#" class="navigation__link">About Natros</a></li>
          <li class="navigation__item"><a href="#" class="navigation__link">Your Benefits</a></li>
          <li class="navigation__item"><a href="#" class="navigation__link">Popular topics</a></li>
          <li class="navigation__item"><a href="#" class="navigation__link">Stories</a></li>
          <li class="navigation__item"><a href="#" class="navigation__link">Book Now</a></li>
        </ul>
```

## Sibiling selector

```scss
    &__checkbox:checked ~ &__nav{
        width: 100%;
        opacity: 1;
    }
```

```html
<input type="checkbox" id="navi-toggle" class="navigation__checkbox">
<div class="navigation__background">&nbsp;</div>
```

## Tranformation Origin

Normally while doing any kind of transformation, we don't specify any origin, hence by default it is applied to center;

hence we can choose tranformation-origin:left or right, to specify the position to perform transform.
