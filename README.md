[README.md](https://github.com/user-attachments/files/26459626/README.md)
# 🗺️ Image Polygon Coordinate Generator

A browser-based tool to draw polygons on images and export coordinates — fully compatible with SVG `viewBox` hotspot systems (e.g. `viewBox="0 0 114 63.8"`).

---

## ✨ Features

- 📁 **Upload any image** — via click or drag & drop
- 🖱️ **Click to place points** — draw a polygon directly on the image
- ✋ **Drag points** — fine-tune each vertex after placing
- 🔄 **Move entire polygon** — click inside a closed polygon and drag it
- 👁️ **Preview selected region** — see the clipped area in a modal
- 📋 **Copy coordinates** — in three formats:
  - **Custom ViewBox** *(default — for test.html)*
  - **Natural Pixels**
  - **Percentage**
- ↩️ **Undo / Clear** — step back or start fresh
- ⌨️ **Keyboard shortcuts** — for faster workflow

---

## 🚀 Getting Started

1. Open `index.html` in any modern browser (no server required).
2. Click the upload area or drag an image onto it.
3. Click on the image to place polygon points.
4. Close the polygon by:
   - Clicking near the **first point** (green), or
   - Pressing **Enter**, or
   - Clicking the **⬡ Close** button.
5. Copy the generated coordinates from the output box.

---

## 🎯 ViewBox Configuration (For test.html)

The tool is pre-configured for `viewBox="0 0 114 63.8"`.

| Setting | Default Value |
|--------|---------------|
| ViewBox Width | `114` |
| ViewBox Height | `63.8` |

You can change these values using the **ViewBox** input fields in the toolbar. Coordinates in the **Custom ViewBox** tab will update instantly.

> ✅ Use the **Custom ViewBox** tab output to paste coordinates directly into your `test.html` `<polygon points="...">` attribute.

---

## ⌨️ Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Enter` | Close polygon (requires 3+ points) |
| `Ctrl + Z` | Undo last point |
| `Escape` | Clear all / Close preview modal |

---

## 📤 Output Formats

### 1. Custom ViewBox *(Recommended for test.html)*
Coordinates scaled to your configured viewBox dimensions.
```
points="12.5,8.2 45.0,10.1 60.3,35.6 20.1,40.0"
```

### 2. Natural Pixels
Raw pixel coordinates based on the image's actual resolution.
```
points="220,145 790,178 1060,628 354,705"
```

### 3. Percentage
Coordinates as percentages of image width/height.
```
points="12.28%,8.21% 44.97%,10.08% 59.84%,35.59%"
```

---

## 🖱️ Interaction Guide

| Action | How To |
|--------|--------|
| Add point | Click on image |
| Move a point | Drag any numbered circle |
| Move whole polygon | Click inside closed polygon and drag |
| Close polygon | Click near point #1 / press Enter |
| Undo last point | Click ↩ Undo or Ctrl+Z |
| Preview selection | Click 👁 View Selected (polygon must be closed) |
| Copy output | Click 📋 Copy |

---

## 🛠️ How Coordinates Are Calculated

```
viewBox_x = (natural_pixel_x / image_natural_width)  × viewBox_width
viewBox_y = (natural_pixel_y / image_natural_height) × viewBox_height
```

The stats panel shows:
- **Points** — number of vertices placed
- **Image Size** — natural pixel dimensions of the loaded image
- **ViewBox** — currently configured viewBox dimensions
- **Scale Factor** — ratio of viewBox width to image pixel width

---

## 🌐 Browser Compatibility

| Browser | Support |
|---------|---------|
| Chrome | ✅ Full |
| Firefox | ✅ Full |
| Edge | ✅ Full |
| Safari | ✅ Full |

> No dependencies, no install, no server needed — just open the HTML file.

---

## 📁 File Structure

```
project/
├── index.html      # The complete tool (single file, no dependencies)
└── README.md       # This documentation
```

---

## 📝 License

Free to use and modify for personal and commercial projects.
