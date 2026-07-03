# Image Generation Skill

## Purpose
Generate production-ready images for UI assets, hero images, icons, and content using OpenAI's image generation models.

## Models
- `gpt-image-1` — Latest, highest quality, best instruction following
- `dall-e-3` — High quality, good for illustrations
- `dall-e-2` — Faster, lower cost, good for variations

## Prompt Patterns

### UI Hero Images
```
A clean, modern hero image for a SaaS dashboard product.
Style: flat illustration, minimal, professional.
Colors: blue and white palette.
No text. 1792x1024.
```

### App Icons
```
A simple app icon for a productivity app.
Style: rounded square, gradient background (purple to blue),
white minimalist symbol of a checkmark inside a circle.
Clean, modern, iOS-style. 1024x1024.
```

### Social Media / OG Images
```
Open Graph image for a developer tool blog post titled "Building with AI".
Style: dark background, code aesthetic, subtle grid pattern.
Accent color: green. No text overlay needed. 1200x630.
```

### Placeholder / Content Images
```
A professional photo-realistic image of a team collaborating
around a laptop in a modern office. Natural lighting.
Diverse team. No faces clearly visible. 1024x1024.
```

## Size Reference

| Use Case | Size |
|----------|------|
| Square asset / icon | 1024x1024 |
| Landscape / hero | 1792x1024 |
| Portrait / mobile | 1024x1792 |
| OG / social (dall-e-3) | 1792x1024 |

## Quality Settings
- `high` — Best quality, slower, higher cost (gpt-image-1)
- `medium` — Balanced
- `low` — Fast prototyping

## Output
Generated images are saved to `assets/generated/` with descriptive filenames.

## Best Practices
- Be specific about style, colors, and mood — vague prompts give vague results
- Specify "no text" if you don't want text rendered in the image
- For brand consistency, always specify your color palette
- Generate multiple variations and pick the best
- Use `gpt-image-1` for final production assets, `dall-e-2` for quick drafts
