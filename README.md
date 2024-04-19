# SCSS

https://www.youtube.com/watch?v=cRpmo58EE8A

SCSS is a CSS preprocessor

## 0. How to install SASS preprocessor

To install the sass preprocessor please run the following command:

```
npm install -g sass
```

To verify the sass installation run this command:

```
sass --version
```

## 1. Project folders and files structure

**Before compiling** the SCSS file

![image](https://github.com/luiscoco/SCSS_Sample1/assets/32194879/cdddcf8a-ce66-4a02-bc83-c853994bac34)

**After compiling** the SCSS file

![image](https://github.com/luiscoco/SCSS_Sample1/assets/32194879/fa2f2c1c-484e-40f5-b3dc-9f5c9c247089)

## 2. HTML source code

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Title</title>
        <link rel="stylesheet" href="style.css">
    </head>
    <body>
        <p>Hello World Luis!</p>
        <div>
            <h1>This is my label</h1>
        </div>
        <button>Accept</button>
        <div class="container">
            <h1>My Head 1</h1>
            <p>My text is also called as my first name</p>
        </div>
        <div class="inheritance">
            <p>Inheritance text</p>
        </div>
    </body>
</html>
```

## 3. SCSS source code

```scss
@use "sass:math";

@import 'variables';

@function px-to-rem($pixels, $root-font-size: 16px) {
  @return #{math.div($pixels, $root-font-size)}rem;
}

body {
  font-size: px-to-rem(18px); // Converts 18px to rem
}

//How to use my variable
body{
    background-color: $primary-color;
}

p{
    color: $font-color;
}
div{
    h1{
        color:$text-color;
    }

    p{
        color:$other-color;
    }
}

@mixin borderstyle($radius){
    border-radius:$radius;
}

.container{
    display:flex;
    align-items:center;
    justify-content:center;
    flex-direction:column;
    background-color: $label-color;
    @include borderstyle(20px);
}

button{
    @include borderstyle(10px);
    margin-bottom:15px;
}

//Operations

$high: 16px;

p{
    font-size: $high * 2.0;
}

//Inheritance

%general{
    border:2px solid black;
    border-radius: 10px;
}

.inheritance{
    @extend %general;
    background-color: cyan;
}

//Conditions
body{
    @if $label-color == green{
        background-color: magenta;
    }
    @else{
        background-color: brown;
    }
}

@mixin theme-colors($theme) {
  @if $theme == 'dark' {
    color: white;
    background-color: greenyellow;
  } @else if $theme == 'light' {
    color: black;
    background-color: white;
  } @else {
    color: gray;
    background-color: lightgray;
  }
}

body {
  @include theme-colors('dark'); // Applies dark theme colors
}

@for $i from 1 through 5 {
  .text-size-#{$i} {
    font-size: px-to-rem($i * 2 + 12px); // Generates font sizes from 14px to 22px in rem
  }
}

// Define the colors map with quoted keys
$colors: ("red": #e3342f, "green": #38c172, "blue": #3490dc);

// Iterate over the colors map
@each $name, $color in $colors {
  .text-#{$name} {
    color: $color;
  }
}

@mixin responsive-text($size-desktop, $size-mobile) {
  font-size: px-to-rem($size-desktop);

  @media (max-width: 768px) {
    font-size: px-to-rem($size-mobile);
  }
}

h1 {
  @include responsive-text(24px, 18px); // 24px on desktops, 18px on mobile devices
}
```

## 4. How to compile the SCSS file

To compile the style.scss file to generate the style.css file we execute this command:

```
sass style.scss style.css
```

For continously compiling the scss file we run this command:

```
sass --watch style.scss style.css
```

