# Performance Optimizations

This document outlines key performance optimizations for this Hugo site, focusing on Google Page Speed Insights scores and build times.

## Largest Contentful Paint (LCP) Optimization

The Largest Contentful Paint (LCP) metric measures the render time of the largest image or text block visible within the viewport. To optimize LCP, especially for hero images or the first significant image on a page, ensure you use the `optimised_image` shortcode with the following attributes:

*   `loading="eager"`: This tells the browser to load the image immediately, without waiting for other resources.
*   `fetchpriority="high"`: This hints to the browser that this image is critical and should be fetched with high priority.

**Example Usage for LCP Image:**

```html
{{< optimised_image src="your-lcp-image.jpg" alt="Description of LCP image" loading="eager" fetchpriority="high" >}}
```

For all other images that are not immediately visible (i.e., below the fold), continue to use `loading="lazy"` (which is the default if `loading` is not specified) to defer their loading and improve initial page load performance.

## Image Generation and Build Speed

The `optimised_image` shortcode now generates a more optimized set of image widths (640px, 1280px, 1920px) for AVIF, WebP, and fallback formats. This significantly reduces the number of image variations Hugo needs to process, leading to faster build times.


