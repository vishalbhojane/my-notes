Question: What is CSS selector specificity and how does it work?
Answer: CSS specificity is a weight given to CSS selectors, determining which styles are applied when multiple rules target the same element. It's calculated as: (Inline styles, IDs, Classes/attributes/pseudo-classes, Elements/pseudo-elements). More specific selectors override less specific ones.

Question: What is the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?
Answer: Resetting removes all built-in browser styling, while normalizing preserves useful defaults and corrects common bugs. Normalizing is generally preferred as it maintains consistency across browsers without removing all default styles.

Question: Describe Floats and how they work.
Answer: Floats remove elements from the normal document flow, pushing them to the left or right of their container. Other content flows around floated elements. They're often used for creating multi-column layouts.

Question: Describe z-index and how stacking context is formed.
Answer: Z-index controls the vertical stacking order of elements that overlap. A stacking context is formed by elements with a z-index value other than auto and a position value other than static. Child elements' z-indexes are only compared within their parent's stacking context.

Question: Describe BFC (Block Formatting Context) and how it works.
Answer: BFC is a part of the visual CSS rendering that contains floats, handles margin collapsing, and prevents element overflow. It's created by elements like floats, absolutely positioned elements, and flex containers.

Question: What are the various clearing techniques and which is appropriate for what context?
Answer: Clearing techniques include:
1. clear: both; - for elements after floats
2. overflow: hidden; - creates a new BFC
3. Clearfix hack - a class with :after pseudo-element
4. display: flow-root; - modern way to create a BFC
Choose based on specific layout needs and browser support requirements.

Question: How would you approach fixing browser-specific styling issues?
Answer: Use feature detection, CSS prefixes, normalize.css, and polyfills. Test across browsers, use browser-specific hacks sparingly, and consider using a CSS preprocessor for managing vendor prefixes.

Question: How do you serve your pages for feature-constrained browsers? What techniques/processes do you use?
Answer: Use progressive enhancement, feature detection (Modernizr), and provide fallbacks. Serve separate stylesheets for older browsers, use polyfills, and consider using a tool like Autoprefixer for vendor prefixes.

Question: What are the different ways to visually hide content (and make it available only for screen readers)?
Answer: 
1. position: absolute; left: -9999px;
2. width: 1px; height: 1px; overflow: hidden;
3. clip: rect(0, 0, 0, 0); clip-path: inset(50%);
4. visibility: hidden; (with aria-hidden="false")

Question: Have you ever used a grid system, and if so, what do you prefer?
Answer: Yes, I've used CSS Grid, Flexbox, and Bootstrap's grid system. I prefer CSS Grid for complex layouts due to its two-dimensional nature, and Flexbox for simpler, one-dimensional layouts.

Question: Have you used or implemented media queries or mobile specific layouts/CSS?
Answer: Yes, media queries are essential for responsive design. Example:

```css
@media (max-width: 600px) {
  .container {
    width: 100%;
  }
}
```

Question: Are you familiar with styling SVG?
Answer: Yes, SVGs can be styled with CSS. You can target SVG elements like paths and change properties such as fill, stroke, and stroke-width.

Question: Can you give an example of an @media property other than screen?
Answer: @media print { ... } - This targets print stylesheets for when a page is printed.

Question: What are some of the "gotchas" for writing efficient CSS?
Answer: Avoid overly specific selectors, minimize use of expensive properties (e.g., box-shadow), use shorthand properties, and be cautious with wildcard selectors (*). Also, consider CSS specificity to prevent unnecessary overrides.

Question: What are the advantages/disadvantages of using CSS preprocessors?
Answer: 
Advantages: Variables, nesting, mixins, functions, and better organization.
Disadvantages: Additional compilation step, potential for overly complex CSS, and debugging can be more difficult.

Question: Describe what you like and dislike about the CSS preprocessors you have used.
Answer: I like the ability to use variables and mixins in Sass, which improves maintainability. However, the potential for overly nested selectors can lead to specificity issues if not carefully managed.

Question: How would you implement a web design comp that uses non-standard fonts?
Answer: Use @font-face to include custom fonts, considering web-safe fallbacks. Example:

```css
@font-face {
  font-family: 'CustomFont';
  src: url('path/to/font.woff2') format('woff2');
}
```

Question: Explain how a browser determines what elements match a CSS selector.
Answer: Browsers match selectors from right to left. They first find elements matching the rightmost selector (key selector) and then traverse up the DOM tree to check if the element's ancestors match the rest of the selector.

Question: Describe pseudo-elements and discuss what they are used for.
Answer: Pseudo-elements allow you to style specific parts of an element. Common uses include adding content before or after an element (::before, ::after), styling the first letter or line of text (::first-letter, ::first-line), or creating custom list markers (::marker).

Question: Explain your understanding of the box model and how you would tell the browser in CSS to render your layout in different box models.
Answer: The box model describes how elements are rendered with content, padding, border, and margin. You can switch between the standard and alternative box model using the box-sizing property:

```css
/* Standard box model */
box-sizing: content-box;

/* Alternative box model */
box-sizing: border-box;
```

Question: What does * { box-sizing: border-box; } do? What are its advantages?
Answer: This sets all elements to use the alternative box model, where padding and border are included in the element's total width and height. Advantages include easier sizing calculations and more intuitive layout behavior.

Question: What is the CSS display property and can you give a few examples of its use?
Answer: The display property determines how an element is rendered. Examples:
- display: block; (full width, new line)
- display: inline; (inline with text)
- display: flex; (flexible box layout)
- display: grid; (grid layout)
- display: none; (removes from layout)

Question: What is the difference between inline and inline-block?
Answer: Inline elements flow with text and don't accept width/height. Inline-block elements flow with text but accept width, height, and vertical margins/paddings.

Question: What is the difference between the "nth-of-type()" and "nth-child()" selectors?
Answer: nth-of-type() selects elements of a specific type, while nth-child() selects elements based on their position among all siblings, regardless of type.

Question: What is the difference between a relative, fixed, absolute and statically positioned element?
Answer: 
- Static: Default flow
- Relative: Positioned relative to its normal position
- Absolute: Positioned relative to nearest positioned ancestor
- Fixed: Positioned relative to the viewport

Question: What existing CSS frameworks have you used locally, or in production? How would you change/improve them?
Answer: I've used Bootstrap and Tailwind CSS. To improve, I'd focus on reducing unused CSS, improving customization options, and enhancing accessibility features.

Question: Have you used CSS Grid?
Answer: Yes, CSS Grid is excellent for creating complex, two-dimensional layouts. It's particularly useful for responsive designs and can simplify layout code significantly.

Question: Can you explain the difference between coding a web site to be responsive versus using a mobile-first strategy?
Answer: Responsive design adapts to different screen sizes, while mobile-first starts with a mobile design and progressively enhances for larger screens. Mobile-first often results in leaner code and faster mobile load times.

Question: Have you ever worked with retina graphics? If so, when and what techniques did you use?
Answer: Yes, for retina displays, I've used techniques like serving higher resolution images with media queries, using SVGs, and utilizing the srcset attribute for responsive images.

Question: Is there any reason you'd want to use translate() instead of absolute positioning, or vice-versa? And why?
Answer: translate() is often preferred for animations as it's handled by the compositor thread, leading to better performance. Absolute positioning is better for static layouts or when you need to remove an element from the document flow.

Question: How is clearfix css property useful?
Answer: Clearfix is not a CSS property, but a technique used to clear floated elements. It's useful for containing floats within a parent element, preventing layout issues. A common implementation:

```css
.clearfix::after {
  content: "";
  display: table;
  clear: both;
}
```

Question: Can you explain the difference between px, em and rem as they relate to font sizing?
Answer: 
- px: Fixed size, doesn't scale with user preferences
- em: Relative to the parent element's font size
- rem: Relative to the root element's font size (usually the `<html>` tag)

Question: Can you give an example of a pseudo class? Can you provide an example use case for a pseudo class?
Answer: :hover is a pseudo-class. Use case:

```css
a:hover {
  color: red;
  text-decoration: underline;
}
```

This changes the link color and adds underline when hovering over it.

Question: What is the difference between a block level element and an inline element? Can you provide examples of each type of element?
Answer: 
Block elements: Start on a new line and take full width. Examples: `<div>, <p>, <h1>`
Inline elements: Flow with text and only take necessary width. Examples: `<span>, <a>, <strong>`

Question: What is the difference between CSS Grid and Flexbox? When would you use one over the other?
Answer: CSS Grid is for two-dimensional layouts (rows and columns), while Flexbox is for one-dimensional layouts (row or column). Use Grid for overall page structure and Flexbox for components within that structure.

Question: What is the difference between fixed, fluid and responsive layouts?
Answer: 
- Fixed: Set widths in pixels, doesn't adapt to screen size
- Fluid: Uses percentages, adapts to screen size but doesn't change layout
- Responsive: Uses media queries to change layout and styling based on screen size