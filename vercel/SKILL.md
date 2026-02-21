---
name: vercel
description: Use Vercel skills for React, Next.js, web design, and React Native development. This is a meta-skill that delegates to specific Vercel skills based on the task.
---

# Vercel Skills

This is a meta-skill that routes to specific Vercel agent-skills based on the task.

## When to Use

Activate this skill when working with:
- React or Next.js development
- Web performance optimization
- UI/UX design and accessibility
- React Native mobile development
- Component architecture patterns

## Delegated Skills

### react-best-practices

**Use when:**
- Writing new React components or Next.js pages
- Implementing data fetching (client or server-side)
- Reviewing code for performance issues
- Optimizing bundle size or load times

**Covers:**
- Eliminating waterfalls (Critical)
- Bundle size optimization (Critical)
- Server-side performance (High)
- Client-side data fetching (Medium-High)
- Re-render optimization (Medium)
- Rendering performance (Medium)
- JavaScript micro-optimizations (Low-Medium)

### web-design-guidelines

**Use when:**
- "Review my UI"
- "Check accessibility"
- "Audit design"
- "Review UX"
- "Check my site against best practices"

**Covers:**
- Accessibility (aria-labels, semantic HTML, keyboard handlers)
- Focus States (visible focus, focus-visible patterns)
- Forms (autocomplete, validation, error handling)
- Animation (prefers-reduced-motion, compositor-friendly transforms)
- Typography (curly quotes, ellipsis, tabular-nums)
- Images (dimensions, lazy loading, alt text)
- Performance (virtualization, layout thrashing, preconnect)
- Navigation & State (URL reflects state, deep-linking)
- Dark Mode & Theming (color-scheme, theme-color meta)
- Touch & Interaction (touch-action, tap-highlight)
- Locale & i18n (Intl.DateTimeFormat, Intl.NumberFormat)

### react-native-skills

**Use when:**
- Building React Native or Expo apps
- Optimizing mobile performance
- Implementing animations or gestures
- Working with native modules or platform APIs

**Covers:**
- Performance (Critical) - FlashList, memoization, heavy computation
- Layout (High) - flex patterns, safe areas, keyboard handling
- Animation (High) - Reanimated, gesture handling
- Images (Medium) - expo-image, caching, lazy loading
- State Management (Medium) - Zustand patterns, React Compiler
- Architecture (Medium) - monorepo structure, imports
- Platform (Medium) - iOS/Android specific patterns

### composition-patterns

**Use when:**
- Refactoring components with many boolean props
- Building reusable component libraries
- Designing flexible APIs
- Reviewing component architecture

**Covers:**
- Extracting compound components
- Lifting state to reduce props
- Composing internals for flexibility
- Avoiding prop drilling

## Installation (for reference)

```bash
npx skills add vercel-labs/agent-skills
```

## Resources

- Vercel agent-skills: https://github.com/vercel-labs/agent-skills
- Skills.sh registry: https://skills.sh/vercel-labs/agent-skills
