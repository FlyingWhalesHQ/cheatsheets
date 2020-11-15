---
layout: default
title: Stimulus
parent: JavaScript
---

# Stimulus Cheatsheet

---

__References__

- Homepage: [https://stimulusjs.org/](https://stimulusjs.org/)
- Github: [https://github.com/stimulusjs/stimulus](https://github.com/stimulusjs/stimulus)

__Sample controller__

```js
import { Controller } from 'stimulus'

export default class extends Controller {
  static targets = [ 'foo', 'bar' ]

  initialize () {}

  connect () {}

  disconnect () {}
}
```

__Lifecycle callbacks__

- `initialize`: once, when the controller is first instantiated
- `connect`: anytime the controller is connected to the DOM
- `disconnect`: anytime the controller is disconnected from the DOM

__Actions__

An action could be invoked by using `data-action="event->controller#method"`

An element could have multiple actions from same or different controllers, separated by space.\
e.g. `data-action="product#addToCart card#updateItems"`

List of tags with default action:

```js
a -> click
button -> click
input[type=submit] -> click

form -> submit

input -> change
select -> change
textarea -> change
```
