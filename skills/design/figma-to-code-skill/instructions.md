# Figma to Code Skill

## Purpose
Convert Figma designs to production-ready, pixel-perfect code with responsive design and accessibility.

## Prerequisites
- Figma API access token
- Figma file URL or ID
- Target framework (React, Vue, etc.)

## Conversion Process

### 1. Fetch Design Data
- Connect to Figma API
- Fetch design file
- Extract components and styles
- Download assets (images, icons)

### 2. Analyze Design
- Identify component hierarchy
- Extract design tokens (colors, spacing, typography)
- Detect responsive breakpoints
- Identify interactive elements

### 3. Generate Code
- Create component structure
- Generate styles (CSS/Tailwind/styled-components)
- Implement responsive design
- Add accessibility attributes
- Optimize images

### 4. Validation
- Verify pixel-perfect implementation
- Test responsive behavior
- Check accessibility compliance
- Validate semantic HTML

## Instructions

### Step 1: Fetch Figma Design
```
User: Convert this Figma design to React: [Figma URL]

Codex: Fetching design from Figma...
✓ Design file loaded
✓ 12 components identified
✓ Assets downloaded
```

### Step 2: Extract Design Tokens
```
Design Tokens Extracted:
Colors:
- Primary: #3B82F6
- Secondary: #10B981
- Background: #F9FAFB
- Text: #111827

Typography:
- Heading: Inter, 32px, 700
- Body: Inter, 16px, 400
- Caption: Inter, 14px, 400

Spacing:
- xs: 4px
- sm: 8px
- md: 16px
- lg: 24px
- xl: 32px
```

### Step 3: Generate Components
```javascript
// Button.tsx
import React from 'react';

interface ButtonProps {
  variant?: 'primary' | 'secondary';
  size?: 'sm' | 'md' | 'lg';
  children: React.ReactNode;
  onClick?: () => void;
}

export const Button: React.FC<ButtonProps> = ({
  variant = 'primary',
  size = 'md',
  children,
  onClick
}) => {
  const baseStyles = 'rounded-lg font-medium transition-colors';
  
  const variantStyles = {
    primary: 'bg-blue-500 hover:bg-blue-600 text-white',
    secondary: 'bg-green-500 hover:bg-green-600 text-white'
  };
  
  const sizeStyles = {
    sm: 'px-3 py-1.5 text-sm',
    md: 'px-4 py-2 text-base',
    lg: 'px-6 py-3 text-lg'
  };
  
  return (
    <button
      className={`${baseStyles} ${variantStyles[variant]} ${sizeStyles[size]}`}
      onClick={onClick}
      aria-label={typeof children === 'string' ? children : undefined}
    >
      {children}
    </button>
  );
};
```

### Step 4: Implement Responsive Design
```javascript
// Hero.tsx
export const Hero: React.FC = () => {
  return (
    <section className="relative">
      {/* Mobile: Stack vertically */}
      <div className="flex flex-col md:flex-row items-center gap-8 p-4 md:p-8 lg:p-12">
        <div className="w-full md:w-1/2">
          <h1 className="text-3xl md:text-4xl lg:text-5xl font-bold">
            Welcome to Our Platform
          </h1>
          <p className="mt-4 text-base md:text-lg text-gray-600">
            Build amazing products with our tools
          </p>
        </div>
        <div className="w-full md:w-1/2">
          <img 
            src="/hero-image.png" 
            alt="Platform preview"
            className="w-full h-auto"
          />
        </div>
      </div>
    </section>
  );
};
```

## Example Workflow

```
User: Convert this Figma landing page to Next.js with Tailwind

Codex: [Activates figma-to-code-skill]

Step 1: Fetching Figma Design
✓ Design file loaded
✓ 8 sections identified
✓ 24 components found
✓ Assets downloaded (12 images, 8 icons)

Step 2: Extracting Design Tokens
✓ Color palette extracted
✓ Typography system defined
✓ Spacing scale created
✓ Breakpoints identified

Step 3: Generating Components
✓ Hero component created
✓ Features section created
✓ Testimonials component created
✓ CTA section created
✓ Footer component created

Step 4: Implementing Responsive Design
✓ Mobile layout (< 768px)
✓ Tablet layout (768px - 1024px)
✓ Desktop layout (> 1024px)

Step 5: Adding Accessibility
✓ Semantic HTML
✓ ARIA labels
✓ Keyboard navigation
✓ Focus indicators
✓ Alt text for images

Step 6: Optimization
✓ Images optimized (Next.js Image)
✓ Lazy loading implemented
✓ CSS purged (unused styles removed)

Conversion complete! ✓

Files created:
- components/Hero.tsx
- components/Features.tsx
- components/Testimonials.tsx
- components/CTA.tsx
- components/Footer.tsx
- styles/design-tokens.css
- public/assets/* (optimized images)

Preview: http://localhost:3000
```

## Best Practices

### Component Structure
- Create reusable components
- Use TypeScript for type safety
- Follow framework conventions
- Implement proper prop validation

### Styling
- Use design tokens for consistency
- Implement responsive design
- Follow mobile-first approach
- Use CSS-in-JS or utility classes

### Accessibility
- Use semantic HTML
- Add ARIA labels
- Ensure keyboard navigation
- Maintain color contrast ratios
- Provide alt text for images

### Performance
- Optimize images
- Lazy load components
- Minimize bundle size
- Use code splitting

## Supported Frameworks
- React / Next.js
- Vue / Nuxt
- Svelte / SvelteKit
- Angular
- HTML/CSS

## Supported Styling
- Tailwind CSS
- styled-components
- CSS Modules
- Sass/SCSS
- Vanilla CSS
