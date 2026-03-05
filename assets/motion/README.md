# Motion Assets

Animated SVG variants of the Orqa Studio logo for use in loading states, splash screens, and transitions.

---

## logo-pulse.svg

![logo-pulse](logo-pulse.svg)

A looping sonar pulse animation. The three concentric rings illuminate sequentially from inner to outer, creating a ripple-out effect. The fin remains static as an anchor point.

| Property | Value |
|---|---|
| Cycle duration | 2.4s |
| Easing | ease-in-out |
| Loop | infinite |
| Technique | CSS `@keyframes` (no JS required) |

### Timing

| Element | Delay | Effect |
|---|---|---|
| Inner ring | 0s | Pulses first |
| Middle ring | 0.4s | Follows inner |
| Outer ring | 0.8s | Follows middle |

Each ring animates from 15% opacity to full and back, creating a calm outward ripple.

### Usage

**Inline in HTML:**

```html
<img src="/assets/motion/logo-pulse.svg" alt="Loading..." width="64" height="64">
```

**As a React component:**

```tsx
function LoadingSpinner({ size = 64 }: { size?: number }) {
  return (
    <img
      src="/assets/motion/logo-pulse.svg"
      alt="Loading..."
      width={size}
      height={size}
    />
  );
}
```

**In CSS as a background:**

```css
.loading {
  width: 64px;
  height: 64px;
  background: url('/assets/motion/logo-pulse.svg') no-repeat center;
  background-size: contain;
}
```

**Inline SVG (for full CSS control):**

If you need to override timing or colours, embed the SVG directly in your markup. The animation classes are:

- `.ring-inner` — first pulse
- `.ring-middle` — second pulse
- `.ring-outer` — third pulse

You can override the animation duration or delay with your own CSS:

```css
.ring {
  animation-duration: 3s; /* slower pulse */
}
```

### Recommended sizes

| Context | Size |
|---|---|
| Inline loading spinner | 32–64px |
| Page-level loading state | 96–128px |
| Splash screen | 256px+ |

### Browser support

Uses CSS animations inside SVG, supported in all modern browsers. When loaded via `<img>`, the animation runs automatically with no JavaScript. For older browsers that don't support SVG CSS animations, the logo renders static at full opacity as a graceful fallback.
