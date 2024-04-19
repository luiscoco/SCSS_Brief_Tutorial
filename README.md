# SCSS

https://www.youtube.com/watch?v=cRpmo58EE8A

SCSS is a CSS preprocessor

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

## 3. CSS source code

```css
//My first comment
/* My second comment with more lines */
@import 'variables';

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

