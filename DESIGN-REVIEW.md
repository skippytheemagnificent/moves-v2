# MOVES App Design Review
## Form Before Features — Visual Polish Assessment

**Review Date:** February 13, 2026  
**Target User:** Jonte (screenwriter, nonprofit founder) — NOT a power user  
**Design Goal:** "Million dollar project manager" — Premium but SIMPLE  
**References:** Linear, Notion, Anthropic's design language

---

## Executive Summary

The MOVES app has solid functionality but currently reads as "hobby project" rather than "premium professional tool." The good news: with focused visual polish (not feature additions), it can absolutely achieve the "million dollar" aesthetic. The key is **reduction** — removing visual noise, refining the color system, and establishing consistent spacing/typography hierarchies.

### Current Impression
> "A feature-rich task manager with enthusiastic but unfocused styling"

### Target Impression  
> "A refined, calm workspace that makes me feel like a CEO"

---

## What Premium Apps Do (The Secret Sauce)

### Linear's Approach
- **Ultra-reduced palette**: Mostly grays, one accent color used sparingly
- **Typography as hierarchy**: Font weight and size do the work, not colors
- **Generous whitespace**: Elements breathe; never feels cramped
- **Subtle depth**: Soft shadows, not glows or heavy borders
- **Consistent 8px grid**: Every spacing decision feels intentional
- **Border subtlety**: 1px borders at 5-10% opacity, never decorative

### Notion's Approach
- **Editorial calm**: Content is the star, chrome recedes
- **Warm neutrals**: Not stark black/white — subtle warmth in grays
- **Block-based clarity**: Clear visual separation between content types
- **Restrained color**: Color is semantic (labels, statuses), not decorative

### Anthropic's Approach
- **Sophisticated warmth**: Deep charcoal instead of pure black; cream instead of pure white
- **Typography pairing**: Sans-serif for UI, serif for editorial moments
- **Breathing room**: Wide margins, tall line-heights
- **Soft edges**: Rounded corners (8-12px), never sharp
- **Layered depth**: Subtle background variations create hierarchy

---

## Current Design Assessment

### What Works

1. **The 3-tab structure is right** — Tasks, Calendar, Journal is a clean mental model
2. **Dark mode foundation** — Appropriate for a "focused work" tool
3. **Card-based layout** — Good structural foundation
4. **The "Today's Focus" section** — Smart prioritization, good UX pattern
5. **Progress indicators** — Visual feedback on completion

### What Doesn't Work

#### 1. Color Palette: "Night Club" Energy
**Current:**
- Background: `#1a1a2e` (deep blue-purple)
- Accent: `#e94560` (hot pink/coral)
- Success: `#4ecca3` (bright teal)
- Gold accents: `#C9A227` (in affirmation banner)

**Problem:** The hot pink + teal + gold combination feels like a gaming app or nightclub flyer. Too many competing accent colors. The blue-purple background has a "cheap dark mode" feel.

#### 2. Typography: No Hierarchy System
**Current:**
- Single font family (system default)
- Sizes range randomly from 0.7rem to 1.4rem
- No consistent type scale
- Italic Georgia for "premium" moments feels mismatched

**Problem:** Visual hierarchy is unclear. User's eye doesn't know where to go.

#### 3. Visual Noise: Too Many "Cool Effects"
**Current:**
- Shimmer animation on affirmation banner
- Pulse animations on hot streaks
- Float animations on icons
- Glow effects on text
- Multiple gradient backgrounds
- Decorative sparkles

**Problem:** Each effect alone is fine; together they create visual chaos. Premium = confident restraint.

#### 4. Inconsistent Spacing
- Padding ranges from 4px to 24px arbitrarily
- No consistent grid system

#### 5. Border Overload
- Many elements have full borders
- Border colors vary wildly
- Creates "caged" feeling

---

## Prioritized Recommendations

### Phase 1: Maximum Impact (Do These First)

#### 1. COLOR SYSTEM OVERHAUL

```css
/* Premium Dark Mode - Replace current palette */
--bg-primary: #0F0F10;        /* Deep charcoal, not blue */
--bg-secondary: #18181A;      /* Slightly lighter for cards */
--bg-tertiary: #232326;       /* For hover states, inputs */

/* Text */
--text-primary: #FAFAFA;
--text-secondary: #A1A1AA;
--text-tertiary: #71717A;

/* Single Accent (use sparingly) */
--accent: #E85D4E;            /* Muted coral */
--accent-subtle: rgba(232, 93, 78, 0.1);

/* Semantic Colors (muted) */
--success: #22C55E;
```

**Action:** Remove gold entirely. Desaturate pink 20%. Remove ALL glow effects.

#### 2. TYPOGRAPHY SYSTEM

```css
/* Type Scale */
--text-xs: 0.75rem;      /* 12px - labels */
--text-sm: 0.875rem;     /* 14px - secondary */
--text-base: 1rem;       /* 16px - body */
--text-lg: 1.125rem;     /* 18px - subheadings */
--text-xl: 1.25rem;      /* 20px - card titles */

/* Weights */
--font-normal: 400;
--font-medium: 500;
--font-semibold: 600;
```

**Action:** Remove Georgia/Didot fonts. Remove text shadows. Apply consistent scale.

#### 3. SIMPLIFY AFFIRMATION BANNER

**Remove:** Shimmer animation, glow, sparkles, gradient

**Replace with:**
```css
.affirmation-banner {
  background: var(--bg-secondary);
  padding: 16px 20px;
  text-align: center;
  border-bottom: 1px solid rgba(255,255,255,0.05);
}

.affirmation-text {
  font-size: 15px;
  color: var(--text-secondary);
  font-style: italic;
  line-height: 1.5;
}
```

#### 4. SIMPLIFY LOGO/HEADER

**Remove:** Gold gradients, flame streaks, "Run Your Life Like a Boss" tagline

**Replace with:** Clean text logo: "MOVES" in semibold, white

### Phase 2: Polish & Refinement

#### 5. SPACING SYSTEM

```css
--space-1: 4px;
--space-2: 8px;
--space-3: 12px;
--space-4: 16px;
--space-6: 24px;
--space-8: 32px;
```

Audit all padding/margins. Apply consistently.

#### 6. BORDER CLEANUP

- Remove most borders
- Use background color differentiation instead
- Only keep 1px borders at 5% opacity where needed

#### 7. REDUCE ANIMATIONS

**Remove entirely:**
- Shimmer animation
- Pulse animation
- Float animation
- Text glow effects

**Keep (but simplify):**
- Tab transitions
- Card hover states
- Modal open/close

#### 8. TAB BAR REFINEMENT

```css
.tab {
  font-size: 15px;
  font-weight: 500;
  color: var(--text-secondary);
  border-bottom: 2px solid transparent;
}

.tab.active {
  color: var(--text-primary);
  border-bottom-color: var(--accent);
}
```

#### 9. CARD REFINEMENT

```css
.card {
  background: var(--bg-secondary);
  border-radius: 12px;
  padding: 16px;
  /* NO border, NO shadow */
}
```

#### 10. BUTTON CLEANUP

Two styles only:
- Primary (accent background, white text)
- Ghost (transparent, muted text)

Remove `.btn.danger` red buttons.

---

## Implementation Checklist

### Day 1: Foundation (Biggest Visual Impact)
- [ ] Replace color palette with "Professional Dark" scheme
- [ ] Remove shimmer/glow/pulse animations
- [ ] Simplify affirmation banner
- [ ] Simplify logo to text-only

### Day 2: Typography & Spacing
- [ ] Implement type scale
- [ ] Remove serif fonts
- [ ] Audit all spacing to 4px grid
- [ ] Apply consistent padding

### Day 3: Component Polish
- [ ] Refine tab bar
- [ ] Clean up cards (remove borders)
- [ ] Simplify buttons
- [ ] Add subtle hover states

---

## Summary

The path from "hobby project" to "million dollar app" is through **confident restraint**:

1. **One accent color**, not three
2. **One font family**, not three
3. **Subtle depth** through backgrounds, not glows
4. **Animation for guidance**, not decoration
5. **Whitespace as a feature**, not a bug

The functionality is already there. The design just needs to get out of its own way.
