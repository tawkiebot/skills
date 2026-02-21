---
name: motion
description: Use Motion (formerly Framer Motion) for React animations. Use when adding animations, transitions, gestures, or scroll effects to React components.
---

# Motion Animation Library

Motion (formerly Framer Motion) is a React animation library for building smooth, production-grade UI animations. It delivers 120fps animations by combining native browser APIs with JavaScript flexibility.

## When to Use

Activate this skill when the user asks to:
- "Add animations"
- "Add transitions"
- "Add hover effects"
- "Add scroll animations"
- "Add drag gestures"
- "Animate on mount"
- "Add page transitions"
- "Use Motion"
- "Animate with Framer Motion"

## Installation

```bash
npm install motion
```

Import from:
```typescript
import { motion } from "motion/react"
```

## Core Concepts

### 1. Motion Components

Wrap any HTML/SVG element with `motion.`:
```tsx
<motion.div animate={{ rotate: 360 }} />
<motion.button whileHover={{ scale: 1.1 }} whileTap={{ scale: 0.95 }} />
<motion.path animate={{ pathLength: 1 }} />
```

### 2. Animation Props

| Prop | Purpose |
|------|---------|
| `initial` | Starting values |
| `animate` | Target values |
| `transition` | Animation timing |
| `whileHover` | Hover state |
| `whileTap` | Tap/click state |
| `whileInView` | Scroll into view |
| `whileDrag` | Dragging state |
| `exit` | Exit animation (needs AnimatePresence) |

### 3. Transition Types

```tsx
// Basic
transition={{ duration: 0.5 }}

// Spring
transition={{ type: "spring", stiffness: 300, damping: 20 }}

// Stagger children
transition={{ staggerChildren: 0.1 }}

// Custom easing
transition={{ ease: [0.6, 0.01, -0.05, 0.9] }}
```

### 4. Variants

Orchestrate multiple elements:

```tsx
const container = {
  hidden: { opacity: 0 },
  show: { 
    opacity: 1,
    transition: { staggerChildren: 0.1 }
  }
}

const item = {
  hidden: { opacity: 0, y: 20 },
  show: { opacity: 1, y: 0 }
}

return (
  <motion.ul variants={container} initial="hidden" animate="show">
    <motion.li variants={item} />
    <motion.li variants={item} />
  </motion.ul>
)
```

## Motion Values

For complex animations without re-renders:

### useMotionValue
```tsx
import { motion, useMotionValue } from "motion/react"

const x = useMotionValue(0)
return <motion.div style={{ x }} />
```

### useSpring
```tsx
const x = useSpring(0, { stiffness: 300, damping: 20 })
```

### useTransform
```tsx
const x = useMotionValue(100)
const opacity = useTransform(x, [0, 100], [1, 0])
```

### useScroll
```tsx
const { scrollYProgress } = useScroll()
return <motion.div style={{ scaleX: scrollYProgress }} />
```

## Gestures

### Hover
```tsx
<motion.button whileHover={{ scale: 1.1 }} />
```

### Tap
```tsx
<motion.button whileTap={{ scale: 0.95 }} />
```

### Drag
```tsx
<motion.div drag dragConstraints={{ left: 0, right: 100 }} />
```

### Pan
```tsx
<motion.div 
  onPan={(e, info) => console.log(info.point)} 
/>
```

## Scroll Animations

### Trigger on scroll into view
```tsx
<motion.div
  initial={{ opacity: 0, y: 50 }}
  whileInView={{ opacity: 1, y: 0 }}
  viewport={{ once: true }}
/>
```

### Link to scroll position
```tsx
const { scrollYProgress } = useScroll()

return (
  <motion.div style={{ scaleX: scrollYProgress }} />
)
```

## Layout Animations

### Auto layout transitions
```tsx
<motion.div layout />
```

### Shared element transitions
```tsx
<motion.div layoutId="box" />
<motion.div layoutId="box" />  // Both animate together
```

## Exit Animations

Requires AnimatePresence:

```tsx
import { AnimatePresence } from "motion/react"

<AnimatePresence>
  {show && (
    <motion.div 
      initial={{ opacity: 0 }} 
      animate={{ opacity: 1 }}
      exit={{ opacity: 0 }}
    />
  )}
</AnimatePresence>
```

## Page Transitions

```tsx
// Wrap children in layout.tsx
<AnimatePresence mode="wait">
  {children}
</AnimatePresence>

// In page component
<motion.div
  initial={{ opacity: 0, y: 20 }}
  animate={{ opacity: 1, y: 0 }}
  exit={{ opacity: 0, y: -20 }}
  transition={{ duration: 0.3 }}
/>
```

## Common Patterns

### Fade in on mount
```tsx
<motion.div
  initial={{ opacity: 0 }}
  animate={{ opacity: 1 }}
  transition={{ duration: 05 }}
/>
```

### Scale up on hover
```tsx
<motion.div
  whileHover={{ scale: 1.05 }}
  transition={{ type: "spring", stiffness: 400 }}
/>
```

### Slide in from right
```tsx
<motion.div
  initial={{ x: 100, opacity: 0 }}
  animate={{ x: 0, opacity: 1 }}
  transition={{ type: "spring", damping: 25 }}
/>
```

### Staggered list
```tsx
const variants = {
  hidden: { opacity: 0 },
  show: { opacity: 1, transition: { staggerChildren: 0.1 } }
}

const item = {
  hidden: { opacity: 0, y: 10 },
  show: { opacity: 1, y: 0 }
}

<motion.ul variants={variants} initial="hidden" animate="show">
  {items.map(item => (
    <motion.li variants={item} key={item.id} />
  ))}
</motion.ul>
```

### Loading spinner
```tsx
<motion.div
  animate={{ rotate: 360 }}
  transition={{ repeat: Infinity, duration: 1, ease: "linear" }}
/>
```

### Progress bar
```tsx
<motion.div
  style={{ scaleX: scrollYProgress }}
  className="h-1 bg-emerald-500 origin-left"
/>
```

## Key Differences from Framer Motion

- Package name: `motion` (not `framer-motion`)
- Import: `from "motion/react"` (not `from "framer-motion"`)
- Some props may have changed - check docs if needed

## Best Practices

1. Use `layout` prop for smooth layout changes
2. Use `spring` transitions for natural feel
3. Use `useMotionValue` for performance-critical animations
4. Use `AnimatePresence` for exit animations
5. Set `viewport={{ once: true }}` for scroll animations that shouldn't replay
6. Use `layoutId` for shared element transitions

## Resources

- Docs: https://motion.dev/docs/react
- Examples: https://motion.dev/examples
- GitHub: https://github.com/motiondivision/motion
