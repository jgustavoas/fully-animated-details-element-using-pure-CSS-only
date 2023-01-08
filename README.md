# Fully animated `<details>` element using pure CSS only

This solution reproduces the example from [Chris Coyier's CSS Tricks article](https://css-tricks.com/how-to-animate-the-details-element/), but achieves the same smooth animation without using JavaScript, only with pure CSS for both opening and closing the `<details>` element.

It presents two possible approaches:

1. Using `+` adjacent sibling combinator that requires an extra div as container.
2. Using `:has()` pseudo-class that doesn't require an extra div, but in order for it to work in Firefox, the user must explicitly enable that feature behind the `layout.css.has-selector.enabled` flag (see [caniuse.com](https://developer.mozilla.org/en-US/docs/Web/CSS/:has#browser_compatibility) and [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/CSS/:has#browser_compatibility)).
