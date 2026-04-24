# PESOnize

PESOnize is a small browser-based image tool for creating a framed profile-style image. Users upload an image, crop it to a square, apply the `Pesonized.png` overlay, and download the result as a PNG.

## Features

- Upload any local image supported by the browser.
- Crop the image with a fixed 1:1 aspect ratio.
- Apply the bundled `Pesonized.png` frame overlay.
- Preview the processed image at 300 x 300 pixels.
- Download the final image at 800 x 800 pixels.

## Project Files

```text
.
|-- index.php          # Main PESOnize page and client-side app logic
|-- cropper.min.css    # Cropper.js styles
|-- cropper.min.js     # Cropper.js library
|-- Pesonized.png      # Frame overlay image
`-- PESOnize.md          # Project documentation
```

## Requirements

- XAMPP, Apache, or another local web server that can serve PHP files.
- A modern browser with JavaScript enabled.

The app runs entirely in the browser after the page loads. It does not require a database or server-side image processing.

## Running Locally With XAMPP

1. Place this folder inside your XAMPP `htdocs` directory.
2. Start Apache from the XAMPP Control Panel.
3. Open the app in your browser:

```text
http://localhost/pesonize/
```

If your folder name is different, replace `pesonize` in the URL with the actual folder name.

## How To Use

1. Click the file input and choose an image.
2. Adjust the crop area in the preview.
3. Click **PESOnize!** to apply the frame.
4. Click **Download** to save the processed PNG.

## Customizing The Overlay

The current overlay is loaded from:

```javascript
overlayBlue.src = 'Pesonized.png';
```

To use a different frame, replace `Pesonized.png` with another transparent PNG of the same style. The app treats the transparent center of the overlay as the image opening and keeps the frame visible on top.

## Notes

- The preview output is rendered at 300 x 300 pixels.
- The downloaded output is rendered at 800 x 800 pixels.
- Cropper.js is bundled locally, so the page does not depend on a CDN.
