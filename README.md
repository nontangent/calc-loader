# Calc Loader
This is a webpack Loader for making functions available in CSS calc() function by interpolation.

## Installation
```
$ npm i -D calc-loader
```

## Usage

```sample.scss
@function pow($n, $k) {
  $res: 1;
  @for $_ from 1 through $k {
    $res: $res * $n;
  }
  @return $res;
}

div {
  width: calc(pow(2, 2) * 2); // => width: calc(#{pow(2, 2))} * 2);
}
```

```webpack.config.js
module.exports = {
  // ......, 
  module: {
    rules: [
      {
        test: /\.scss$/,
        use: [
        // ..., 
        // Add ''calc-loader' under the SCSS Loaders 
          { 
            loader: 'calc-loader',
            options: {
              functions: ['pow']
            },
          }
        ],
      }
    ],
  },
}
```


## LICENSE
MIT
