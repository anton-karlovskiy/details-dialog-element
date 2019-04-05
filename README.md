# &lt;details-dialog&gt; element

A modal dialog that's opened with a &lt;details> button.

## Installation

```
$ npm install --save details-dialog-element
```

## Usage

```js
import 'details-dialog-element'
```

```html
<details>
  <summary>Open dialog</summary>
  <details-dialog>
    Modal content
    <button type="button" data-close-dialog>Close</button>
  </details-dialog>
</details>
```

## Deferred loading

Dialog content can be loaded from a server by embedding an [`<include-fragment>`][fragment] element.

```html
<details>
  <summary>Robots</summary>
  <details-dialog src="/robots" preload>
    <include-fragment>Loading…</include-fragment>
  </details-dialog>
</details>
```

The `src` attribute value is copied to the `<include-fragment>` the first time the `<details>` button is toggled open, which starts the server fetch.

If the `preload` attribute is present, hovering over the `<details>` element will trigger the server fetch.

## Events

### `details-dialog:will-close`

A `details-dialog:will-close` event is fired when a request to close the dialog
is made either by pressing escape, clicking a `data-close-dialog` element,
clicking on the `<summary>` element, or when `.toggle(false)` is called on an
open dialog.

This event can be cancelled to keep the dialog open.

```js
document.addEventListener('details-dialog:will-close', function(event) {
  if (!confirm('Are you sure?')) {
    event.preventDefault()
  }
})
```

## Browser support

Browsers without native [custom element support][support] require a [polyfill][].

- Chrome
- Firefox
- Safari
- Microsoft Edge

## Development

```
npm install
npm test
```

## License

Distributed under the MIT license. See LICENSE for details.

[fragment]: https://github.com/github/include-fragment-element/
[support]: https://caniuse.com/#feat=custom-elementsv1
[polyfill]: https://github.com/webcomponents/custom-elements
