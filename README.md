_Yes, this includes animating the closing of the element too!_

**[Check the final result live on CodePen](https://codepen.io/jgustavoas/pen/zYLNKbN)**

Animating the `<details>` HTML element using only pure CSS can be a challenging task, as many articles, posts, and tutorials either rely on JavaScript or offer incomplete solutions that are unable to animate the closing of the element or produce a smooth animation.

However, with a bit of creativity, it is possible to create a fully-animated `<details>` element using pure CSS.

This solution reproduces the example from [Chris Coyier's CSS Tricks post](https://css-tricks.com/how-to-animate-the-details-element/), but achieves the same smooth animation without using any JavaScript – only CSS – for both opening and closing the element.

The key is to start the page with the `details` element in its open state (`<details open>`), then change its `max-height` value by toggling a checkbox, and use a transition effect to animate that change.
```
details {
   max-height: 4rem; /* Set a max-height value just enough to show the summary */
   overflow: hidden; /* Hide the rest of the content */
   transition: max-height 400ms ease-out; /* Animate the change */
}
```

To control the change of the element's `max-height` value, you will need a checkbox and associate it with the `<details>` element. You can choose from two approaches to do this, and both work great:

1. Using the `+` adjacent sibling combinator
2. Using the `:has()` pseudo-class
```
input:checked + details,
details:has(input:checked) {
    max-height: 576px; /* Set a max-height value enough to show all the content */
}
```
In the CSS, the selector `input:checked + details` selects a `<details>` element that immediately follows a checked input element. On the other hand, the selector `details:has(input:checked)` selects a `<details>` element that has a checked input element as a descendant.

The difference between the two approaches is that the checkbox input must come immediately before the `<details>` element in the first approach, and the checkbox must be a descendant of the `<details>` element in the second approach.

Inside the `<summary>` tag of the `<details>` element , place a `<label>` that toggles the checkbox:

```
<!-- approach #1 (checkbox comes immediately before the details element) -->
<input type="checkbox" name="detail-plus" id="detail-plus" />
<details open>
  <summary>
    <label for="detail-plus">This one uses the adjacent sibling combinator (+) approach</label>
  </summary>

  <div class="rest-of-the-content">...</div>
</details>

<!-- approach #2 (checkbox is a descendant of the details element -->
<details open>
  <summary>
    <input type="checkbox" name="detail-has" id="detail-has" />
    <label for="detail-has">This one uses :has() pseudo-class approach</label>
  </summary>

  <div class="rest-of-the-content">...</div>
</details>
```

One caveat to consider when using the `:has()` approach is that in Firefox the user must explicitly enable this feature (see [caniuse.com](https://caniuse.com/css-has) and [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/CSS/:has#browser_compatibility)).

