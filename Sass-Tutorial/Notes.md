# SASS Tutorial for Beginners - FreeCodeCamp

<https://www.youtube.com/watch?v=_a5j7KoflTs>

Sass is an extension of CSS that include a variety of other capabilities beyond those found in regular css.

Must compile Sass into css for it to work on the web.

Can use a variety of paths to compile SASS, including nmp gulp and vs code live sass compiler.

Live Sass compiler is easiest.

+ Make sure to change any settings such as minifying or changing output directory to a distribution folder.

## Maps

Maps in Sass are variables with lists of key:value pairs. They use regular parentheses instead of curly braces. Helps you change things in one spot (the map) versus changing it everywhere you use it in the file.

Example:

```scss
$font-weights: (
    "regular": 400,
    "medium": 500,
    "bold": 700,
)

.main {
    font-weight: map-get($font-weights, bold)
}
```

## Nesting

Be careful with too much nesting. It is one of the most powerful features of Sass, but it is better to use classes that can be reused over and over compared to nesting and repeating things constantly.

+ Use an ampersand (&) to refer to include parent class.
+ Must use interpolation to include everything before it. Do this by wrapping the & in `#{&}`

Example:

```scss
.main {
    width: 80%;
    margin: 0 auto;

    #{&}__paragraph {
        font-weight: map-get($font-weights, bold);

        &:hover {
            color: pink;
        }
    }
}
```

## Partials

Live Sass compiler will look for any .scss to create into a css file, but you can create partial files by including an underscore in the beginning of the name, such as `_variables.scss`. You the use the `@import '_variables.scss'` at the top of your main scss file to include them.

By separating them, it helps you locate things easier as your stylesheet grows. It also helps teams in large projects to break up the work.

## Functions

Sass supports creating functions by using the `@function FUNCTION_NAME($VARIABLES)` verbiage.

Example:

```scss
@function weight($weight-name) {
    @return map-get($font-weights, $weight-name)
}

.main {
    font-weight: weight(bold);
}
```
