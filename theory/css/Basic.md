## What is CSS selector specificity and how does it work?
CSS selector specificity determines which CSS rules are applied to an element when multiple rules could apply

```html
<div id="header" style="color: pink;">
  <p class="text">Hello</p>
</div>

<style>
  #header {
    color: blue; /* Specificity: 0,1,0,0 */
  }

  .text {
    color: green; /* Specificity: 0,0,1,0 */
  }
</style>
```

#### Specificity Calculation Formula

1. Count the number of ID selectors in the rule.
2. Count the number of class selectors, attribute selectors, and pseudo-classes in the rule.
3. Count the number of element selectors and pseudo-elements in the rule.
4. Inline styles are given the highest specificity, and the default specificity for inline styles is `1,0,0,0`.

#### Specificity Hierarchy Summary

- **Inline styles**: `1,0,0,0`
- **IDs**: `0,1,0,0`
- **Classes, attributes, pseudo-classes**: `0,0,1,0`
- **Elements, pseudo-elements**: `0,0,0,1`

!important has highest specificity, avoid overusing

## What is the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?

Resetting CSS involves removing or "resetting" all default browser styles to create a clean slate

Normalizing CSS involves making the default styles of elements consistent across different browsers, rather than removing them entirely. This approach aims to preserve useful default styles while ensuring consistency in how elements are rendered

#### Which to Choose and Why?

Choosing between resetting and normalizing CSS depends on your project’s needs:

**Use Resetting CSS if**:
You want a completely uniform starting point and are comfortable with reapplying basic styling yourself.
You need to ensure that no browser-specific styles interfere with your custom styles.
You are working on a project where you require precise control over every aspect of styling from scratch.

**Use Normalizing CSS if**:
You prefer to keep some useful default styles while standardizing inconsistencies.
You want to avoid the extra work of reapplying basic styles that resets might strip out.
You are aiming for a balance between consistency and preserving useful browser defaults.

## Block Formatting Context (BFC)

Block Formatting Context (BFC) is a layout mechanism that affects how block-level elements are formatted and interact within a container.
Creating BFC: Elements create a BFC with certain properties like position, overflow, display, or float.

Effects:
Prevents margin collapsing with neighboring BFCs.
Contains floating elements within the BFC.
Defines a new stacking context for elements within it.

## What are the various clearing techniques and which is appropriate for what context

Clearfix: Best used when you need to clear floats within a container and ensure the container encompasses its floated children. It’s a traditional and widely compatible method.

Overflow Property: Useful for creating a new block formatting context and clearing floats. It also handles overflow issues within the container. Ideal when you want to manage both floating elements and overflow.

Clear Property: Suitable for clearing floats for specific elements rather than entire containers. It’s useful for individual elements that need to be placed below floating elements.

Flexbox: Best for modern, flexible layouts where you want to avoid using floats altogether. It handles layout issues cleanly and is ideal for responsive designs.

Grid Layout: Appropriate for complex, multi-dimensional layouts where you need a robust and flexible solution for placing elements. It provides a powerful alternative to floats and flexbox
