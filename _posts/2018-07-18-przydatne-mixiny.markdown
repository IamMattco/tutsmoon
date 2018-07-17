---
layout: post
title:  "Przydatne mixiny do Sassa"
date:   2018-07-18 16:12:09 +0100
categories: sass frontend
thumbnail: "/images/pic01.jpg"
---

Witaj, chciałbym Ci zaprezentować kilka przydatnych mixinów do Sassa, które przyspieszą i z automatyzują twoją pracę.

## Placeholder

Mixin ten pomaga nam ostylować placeholder w inpucie.

```sass
@mixin placeholder {
   &.placeholder { @content; }
   &:-moz-placeholder { @content; }
   &::-moz-placeholder { @content; }
   &::-webkit-input-placeholder { @content; }
}
```
Przydład użycia:

```sass
input {
   @include placeholder {
      color: #ccc;
      font-style: italic;
   }
}
```

## Font smothing

Wygładzona czcionka wygląda lepiej, to fakt z którym nikt nie dyskutuje, tak więc jeśli chcesz wygładzić czcionki na swojej stronie, użyj w swoim projekcie poniższy mixin.

```sass
@mixin smooth {
   -webkit-font-smoothing: antialiased;
   -moz-osx-font-smoothing: grayscale;
}
```

Przykład użycia

```sass
p {
   @include smooth();
}
```

## Gradient

Mixin generujący gradient, wystarczy że podamy kolor początkowy, kolor końcowy oraz kierunek gradientu.

```sass
@mixin gradient($start-color, $end-color, $orientation) {
background: $start-color;
@if $orientation == 'vertical' {
background: -webkit-linear-gradient(top, $start-color, $end-color);
background: linear-gradient(to bottom, $start-color, $end-color);
} @else if $orientation == 'horizontal' {
background: -webkit-linear-gradient(left, $start-color, $end-color);
background: linear-gradient(to right, $start-color, $end-color);
} @else {
background: -webkit-radial-gradient(center, ellipse cover, $start-color, $end-color);
background: radial-gradient(ellipse at center, $start-color, $end-color);
}
}
``` 

Przykład użycia

```sass
.button {
   @include gradient(#fff, #000, vertical);
}
```

## Podsumowując

Sass znacząco przyspiesza tworzenie styli dla strony internetowej, uważam, że jest bardzo wygodny i łatwy w nauczeniu. Wszystko robi się intuicyjnie, a powyższe mixiny dodatkowo przyspieszają ten proces.

Zawszę wychodzę z założenia, że trzeba ułatwiać sobie pracę a nie ją komplikować.
