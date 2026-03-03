# Adding Images to Your Landing Page

## Instructions to Add the Promotional Images

The landing page is now set up to use your Matasree Super promotional images. Follow these steps:

### Step 1: Save the Images

You have two images to add to the `assets/` folder:

1. **Poster Image** (Launch campaign poster with spices)
   - Save as: `assets/matasree-poster.jpg`
   - Location: `d:\Matasree_Store\matasree-landing\assets\matasree-poster.jpg`
   - Used in: Hero section (top of page)

2. **Excellence Image** (Yellow card "18+ Years of Excellence")
   - Save as: `assets/matasree-excellence.jpg`
   - Location: `d:\Matasree_Store\matasree-landing\assets\matasree-excellence.jpg`
   - Used in: About section (middle of page)

### Step 2: Copy Image Files

Directly copy/paste the image files you provided into the `matasree-landing/assets/` folder:

```
matasree-landing/
├── assets/
│   ├── matasree-poster.jpg        ← Add poster image here
│   ├── matasree-excellence.jpg    ← Add excellence image here
│   ├── styles.css
│   ├── script.js
│   └── logo.svg
├── index.html
├── README.md
└── package.json
```

### Step 3: View the Landing Page

Once the images are added:

1. Open the folder in VS Code
2. Right-click `index.html` → "Open with Live Server"
3. The page will display with your actual promotional images!

## Image Requirements

- **Format**: JPG or PNG
- **Poster Size**: Recommended 1200x800px (landscape)
- **Excellence Card**: Recommended 600x400px (landscape)
- **Quality**: High resolution for sharp display

## Alternative: Quick Test

If you want to test the page layout without images:
- The page will still load and display correctly
- Images will just show as broken if files aren't present
- Add them later and refresh the page

## File Paths in HTML

The HTML now references:
- `assets/matasree-poster.jpg` - Main hero poster
- `assets/matasree-excellence.jpg` - About section image

Both are configured to be responsive and mobile-friendly!
