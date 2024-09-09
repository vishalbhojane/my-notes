Question: What tools would you use to find a performance bug in your code?
Answer: 
1. Browser DevTools (Chrome, Firefox, Safari):
   - Performance tab for profiling
   - Network tab for analyzing requests
   - Memory tab for identifying memory leaks
2. Lighthouse: For overall performance audits
3. WebPageTest: For detailed performance analysis
4. JavaScript profilers (e.g., Chrome's CPU Profiler)
5. Node.js specific tools like clinic.js for server-side performance
6. Application Performance Management (APM) tools like New Relic or Datadog

Example: Using Chrome DevTools Performance tab to record and analyze runtime performance:

```javascript
// Open DevTools, go to Performance tab
// Click Record, interact with your site, then stop recording
// Analyze flame chart, summary, and bottom-up views to identify bottlenecks
```

Question: What are some ways you may improve your website's scrolling performance?
Answer:
1. Use CSS will-change property for elements that will animate
2. Implement virtual scrolling for long lists
3. Debounce or throttle scroll event listeners
4. Use requestAnimationFrame for scroll-linked animations
5. Avoid changing layout during scroll (minimize reflows)
6. Use CSS transforms instead of changing top/left properties
7. Optimize images and use lazy loading
8. Reduce DOM depth and complexity

Example of debouncing a scroll event:

```javascript
let timeout;
window.addEventListener('scroll', () => {
  clearTimeout(timeout);
  timeout = setTimeout(() => {
    // Perform expensive operation here
  }, 150);
});
```

Question: Explain the difference between layout, painting and compositing.
Answer:
1. Layout (Reflow): 
   - Calculates the positions and sizes of elements
   - Triggered by changes to element dimensions or document structure

2. Painting:
   - Fills in pixels for each element
   - Draws text, colors, images, borders, and shadows

3. Compositing:
   - Draws layers in the correct order
   - Handles overlapping elements and transparency

The process typically flows from Layout -> Paint -> Composite. Optimizing for compositing (using properties like transform and opacity) can improve performance by avoiding layout and paint operations.

Example of optimizing for compositing:

```css
/* Instead of */
.moving-element {
  left: 100px;
  top: 100px;
}

/* Use */
.moving-element {
  transform: translate(100px, 100px);
}
```

This leverages GPU acceleration and avoids triggering layout and paint operations.