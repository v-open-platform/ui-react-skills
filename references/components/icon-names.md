# Icon Names

Complete list of available icon names in `@v-miniapp/ui-react`. Icons are available in two variants: `-outline` and `-fill`.

**Usage:** Use icon name without suffix (e.g., `'home'`) or with suffix (e.g., `'home-outline'`, `'home-fill'`).

---

## Icon Names List

### A

- `add-magic` (outline, fill)
- `arrow-door-out` (outline, fill)
- `arrow-left-from-line` (outline, fill)
- `arrow-right` (outline, fill)
- `arrow-right-from-line` (outline, fill)
- `arrow-rotate-anticlockwise` (outline, fill)
- `arrow-rotate-clockwise` (outline, fill)
- `arrow-trend-down` (outline, fill)
- `arrow-trend-up` (outline, fill)
- `arrows-expand` (outline, fill)
- `atm-machine` (outline, fill)

### B

- `badge-check` (outline, fill)
- `ballot-circle` (outline, fill)
- `battery-alert` (outline, fill)
- `battery-charging` (outline, fill)
- `bell` (outline, fill)
- `bell-slash` (outline, fill)
- `bolt` (outline, fill)
- `bolt-slash` (outline, fill)
- `book-open` (outline, fill)
- `bookmark` (outline, fill)
- `bug-slash` (outline, fill)

### C

- `calendar` (outline, fill)
- `camera` (outline, fill)
- `car-electric` (outline, fill)
- `car-side` (outline, fill)
- `charging-station` (outline, fill)
- `chart-column-trend-up` (outline, fill)
- `chart-donut` (outline, fill)
- `check` (outline, fill)
- `check-double` (outline, fill)
- `chevron-down` (outline, fill)
- `chevron-left` (outline, fill)
- `chevron-right` (outline, fill)
- `chevron-up` (outline, fill)
- `circle-check` (outline, fill)
- `circle-info` (outline, fill)
- `circle-question` (outline, fill)
- `circle-xmark` (outline, fill)
- `clipboard-list` (outline, fill)
- `clock` (outline, fill)
- `clone` (outline, fill)
- `credit-card` (outline, fill)
- `credit-card-plus` (outline, fill)
- `crown` (outline, fill)

### D

- `discount-code` (outline, fill)
- `dots` (outline, fill)
- `double-chevron-left` (outline, fill)
- `double-chevron-right` (outline, fill)
- `download` (outline, fill)

### E

- `envelope` (outline, fill)
- `eye` (outline, fill)
- `eye-slash` (outline, fill)

### F

- `facial-recognition` (outline, fill)
- `file-content` (outline, fill)
- `filter` (outline, fill)
- `fingerprint` (outline, fill)
- `flag` (outline, fill)
- `folder` (outline, fill)
- `folder-open` (outline, fill)

### G

- `gear` (outline, fill)
- `gift` (outline, fill)
- `graduation-cap` (outline, fill)
- `grid` (outline, fill)
- `grid-plus` (outline, fill)

### H

- `hashtag` (outline, fill)
- `headset` (outline, fill)
- `heart` (outline, fill)
- `history` (outline, fill)
- `house` (outline, fill)

### I

- `image` (outline, fill)
- `input-password` (outline, fill)

### L

- `language` (outline, fill)
- `lightbulb` (outline, fill)
- `link` (outline, fill)
- `link-slash` (outline, fill)
- `loader` (outline, fill)
- `lock` (outline, fill)

### M

- `magnifier` (outline, fill)
- `media-next` (outline, fill)
- `media-pause` (outline, fill)
- `media-play` (outline, fill)
- `media-previous` (outline, fill)
- `media-stop` (outline, fill)
- `menu` (outline, fill)
- `message-content` (outline, fill)
- `microphone` (outline, fill)
- `minus` (outline, fill)
- `money-bill-coin` (outline, fill)
- `msg` (outline, fill)

### N

- `newspaper` (outline, fill)
- `nodes` (outline, fill)

### O

- `office` (outline, fill)

### P

- `paper-plane` (outline, fill)
- `pen` (outline, fill)
- `phone` (outline, fill)
- `pin` (outline, fill)
- `pin-tack` (outline, fill)
- `plane` (outline, fill)
- `placeholder` (outline, fill)
- `plus` (outline, fill)

### Q

- `qrcode` (outline, fill)

### R

- `receipt` (outline, fill)

### S

- `scan` (outline, fill)
- `scooter-front` (outline, fill)
- `share-right` (outline, fill)
- `shield-check` (outline, fill)
- `stack-x-plus` (outline, fill)
- `star` (outline, fill)

### T

- `text-prompt` (outline, fill)
- `text-size` (outline, fill)
- `thumbs-down` (outline, fill)
- `thumbs-up` (outline, fill)
- `trash` (outline, fill)
- `triangle-warning` (outline, fill)

### U

- `user` (outline, fill)
- `user-bubble-check` (outline, fill)
- `user-shield` (outline, fill)
- `user-xmark` (outline, fill)
- `users-plus` (outline, fill)

### W

- `wallet` (outline, fill)
- `waveform-lines` (outline, fill)

### X

- `xmark` (outline, fill)

---

## Usage Examples

```tsx
// Use without suffix (defaults to outline)
<Icon name="home" />
<Icon name="user" />
<Icon name="arrow-right" />

// Use with suffix for specific variant
<Icon name="home-fill" />
<Icon name="home-outline" />
<Icon name="bell-fill" />
<Icon name="bell-outline" />
```

---

## Icon Name Format

- **Base name:** Icon name without suffix (e.g., `'home'`, `'user'`, `'arrow-right'`)
- **With suffix:** Add `-outline` or `-fill` for specific variant (e.g., `'home-outline'`, `'home-fill'`)
- **TypeScript:** Icon names are type-safe. Use `iconNames` export to get all available names programmatically.

---

## Notes

- All icons have both `-outline` and `-fill` variants
- Icon names use kebab-case (lowercase with hyphens)
- Use base name (without suffix) for default outline variant
- Special icons: `loader` and `placeholder` use SVG components instead of font icons
