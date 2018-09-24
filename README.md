# Textifier ![](http://img.badgesize.io/TemplarVolk/textifier/master/dist/textifier.min.js.svg?style=flat)

>*Textifier is a javascript library that lets you convert images to any text of your choosing, in your browser*

| Colored | Grayscale | Monochrome | Console |
| --- | --- | --- | --- |
| ![Colored](images/rendered_piggies.png "Colored") | ![Grayscale](images/grayscale_piggies.png "Grayscale") | ![Monochrome](images/monochrome_piggies.png "Monochrome") | ![Console](images/console_piggies.png "Console") |

Textifier can print as HTML an image or it can even print it in you browser's console.

## Instalation

  ```bash
  $ npm install textifier
  # OR
  $ bower install textifier
  ```

  Or just [download](https://github.com/TemplarVolk/textifier/master/dist/textifier.min.js) the minified script and add it in your HTML:

  ```html
  <script src="textifier.min.js"></script>
  ```

## Usage

  Here is the mandatory one-liner to show how simple it can be.
  ```js
  new Textifier().draw(target, 'images/piggies.png');
  ```

  Of course you are probably going to want use some options. Textifier takes 3 optional arguments: maxWidth, maxHeight and options.

### :warning: NOTES :warning:

  Textifier needs CORS access to the source images.

  Dimensions are measured in characters and not pixels. So setting something like 500 will be something huge. Also a character is not a square, meaning that the height and width are not the same proportions. The default `monospace` font has a height/width ratio of around 1.8. Which means that a number in maxHeight means almost twice as much as the one in maxWidth.
  Measurements in pixels will be added somewhere in the future.

### maxWidth
  `type: int`

  maxWidth is an should be a positive number. This sets maximum width of the rendered image. If it is not set or set with something other than a positive number, it will take as much space as it can.

### maxHeight
  `type: int`

  Same as maxWidth except that if it is not set the maximum height will be the the same as the height of the original image but in characters instead of pixels.

### options
  `type: object`

Every other option will be in the option object.

  | Names | Defaults | Types | Info
  | --- | --- | --- | ---
  | characters | `"01"` | `string`  | The character list to write the image with.
  | background | `#00000000` | `string`   | Color of the background. This color will also be rendered in text.
  | ordered | `false` | `boolean`  | If true the characters will show up in order of the `characters` string
  | color | `int` | `number` | If the image should be colored, in grayscale or monochrome<br>`0 = colored`<br>`1 = grayscale`<br>`2 = monochrome`<br>Textifier comes with some [constants](#constants) so you don't have to memorize this

  Since all arguments are optional the options argument can be placed anywhere by omitting any of the other 2.

  ```js
  new Textifier(100, 50, options);
  ```

  ```js
  new Textifier(100, options);
  ```

  ```js
  new Textifier(options);
  ```
  **↿These are all valid↾**

## Functions
  There are 3 main functions in Textifier, write, draw and log. There a few other mainly used internally but available anyways since they might come in handy.
### write, draw
  `arguments: (url, element, append)`

  The `write` and `draw` functions work exactly the same way. The only difference is that `write` will print html in a \<pre> tag and the `draw` will print an actual image on a canvas.
#### url
  `type: string`

  The url of the image to be used.
#### element
  `type: DOM Element`

  The element in which the rendered image will be added to.
#### append
  `type: boolean`

  If the rendered image should be appended or replace the contents of the target `element`.

##### **Example**

  ```js
  new Textifier(100, {characters: 'piggy', ordered: true}).draw('images/piggies.png', target);
  ```
##### Output
  ![Rendered image](images/rendered_piggies.png "Rendered image")


### log
  `arguments: (url)`

  The `log` function will print the image in the dev console of your browser.
#### url
  `type: string`

  The url of the image to be used.

##### **Example**

  ```js
  new Textifier(100, {characters: 'piggy', ordered: true}).log('images/piggies.png');
  ```
##### Output
  ![Rendered image](images/console_piggies.png "Rendered image")

## Constants
  Textifier comes with some "constants" so you don't have to remember arguments that are numbers and to make your code more readable.

  ```js
  Textifier.COLORED = 0;
  Textifier.GRAYSCALE = 1;
  Textifier.MONOCHROME = 2;

  Textifier.HTML = 0;
  Textifier.CANVAS = 1;
  Textifier.CONSOLE = 2;
  ```

## License
   [MIT License](LICENSE.md)