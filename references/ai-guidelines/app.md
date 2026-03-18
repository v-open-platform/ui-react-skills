# App Framework Guidelines

Critical guidelines for AI assistants when working with App Framework features (routing, navigation, theming) in V-MiniApp projects.

---

## Routing Guidelines

**CRITICAL:** Routing in V-MiniApp only supports **single-level paths** (`/pathname`). Nested routes or custom paths are not supported.

### Routing Limitations

1. **Single-level paths only:**

   - Supported: `/home`, `/settings`, `/profile`, `/products`
   - Not supported: `/products/detail`, `/users/:id`, `/category/:slug`

2. **For detail pages or dynamic content:**

   - Use **search params** (query parameters) instead of nested routes
   - Example: `/products?id=123` instead of `/products/123`
   - Example: `/users?id=456&tab=profile` instead of `/users/456/profile`

3. **Navigation with params:**

   ```tsx
   import { useNavigate } from '@v-miniapp/ui-react'

   const navigate = useNavigate()

   // Correct: Use search params for detail pages
   navigate('/products', { params: { id: '123' } })
   // Results in: /products?id=123

   // Incorrect: Don't use nested paths
   navigate('/products/123') // This won't work properly
   ```

4. **Reading params:**

   ```tsx
   import { useLocation } from '@v-miniapp/ui-react'

   const location = useLocation()
   const productId = location?.params?.id // Get from search params
   ```

**Remember:** Always use search params (`?key=value`) for detail pages, filters, or any dynamic content. The routing system only supports top-level pathnames.

---

## Design & Theme Guidelines

**CRITICAL:** When creating new V-MiniApp projects, use the standard brand color token as the default theme color.

### Default Brand Color

1. **Brand color token:**

   - Use `--color-alias-background-brand` as the default brand color for new projects
   - This token is part of the design system and ensures consistency across all V-MiniApp projects

2. **Usage in components:**

   ```tsx
   import { Button } from '@v-miniapp/ui-react'

   // Use brand color token
   ;<Button color="alias-background-brand">Click me</Button>
   ```

3. **Usage in CSS:**

   ```css
   .my-brand-element {
     background-color: var(--color-alias-background-brand);
   }
   ```

4. **Usage with Tailwind:**
   ```tsx
   // When using Tailwind integration
   <div className="bg-alias-background-brand">Brand colored content</div>
   ```

**Remember:** Always use `--color-alias-background-brand` (or `alias-background-brand` token) as the default brand color when creating new projects. This ensures visual consistency with the V-MiniApp design system.
