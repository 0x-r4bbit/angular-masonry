# Angular Masonry Directive [![Build Status](https://travis-ci.org/passy/angular-masonry.png)](https://travis-ci.org/passy/angular-masonry)

[Homepage](http://passy.github.io/angular-masonry)

An [AngularJS](http://angularjs.org/) directive to work with David Desandro's [Masonry](http://masonry.desandro.com/).

## Usage

1. `bower install --save angular-masonry`
2. Include dependencies in your HTML.
3. Use the `masonry` directive.

## Example

See the [homepage](http://passy.github.io/angular-masonry) for a live example.

```html
<div masonry>
    <div class="masonry-brick" ng-repeat="brick in bricks">
        <img ng-src="{{ brick.src }}" alt="A masonry brick">
    </div>
</div>
```

You have to include the `masonry` attribute on the element holding the bricks.
The bricks are registered at the directive through the `masonry-brick` CSS
classname.

## Attributes

### `item-selector`

(Default: `.masonry-brick`)

You can specify a different [item
selector](http://masonry.desandro.com/options.html#itemselector) through the
`item-selector` attribute. You still need to use `masonry-brick` either as class
name or element attribute on sub-elements in order to register it to the
directive.

*Example:*

```html
<masonry item-selector=".mybrick">
    <div masonry-brick class="mybrick">Unicorns</div>
    <div masonry-brick class="mybrick">Sparkles</div>
</masonry>
```

### `loaded`

`angular-masonry` waits for all images within the brick to be loaded and applies
a `loaded` CSS class to the element afterwards, so you can prevent ghosting
effects. You can override this behavior by providing a `loaded` attribute that
takes a callback, which gets an `$element` injected referring to the loaded
element.

*Example:*

```javascript
$scope.onLoaded = function ($element) {
    $element.show();
};
```

```html
<masonry loaded="onLoaded($element)">
    <div class="masonry-brick" style="display: none">
        <img src="hidden-until-loaded.png">
    </div>
</masonry>
```

### `column-width`

The `column-width` attribute allows you to override the [the width of a column
of a horizontal grid](http://masonry.desandro.com/options.html#columnwidth). If
not set, Masonry will use the outer width of the first element.

*Example:*

```html
<masonry column-width="200">
    <div class="masonry-brick">This will be 200px wide max.</div>
</masonry>
```

## Credits

The directive is based on
[a StackOverflow question](http://stackoverflow.com/questions/16504151/masonry-with-angularjs)
answered by James Sharp.


## Contributing

Pull requests welcome. Only change files in `src` and don't bump any versions.
Please respect the code style in place.

## License

MIT
