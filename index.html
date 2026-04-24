<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>PESOnize</title>
  <link href="cropper.min.css" rel="stylesheet">
  <style>
    html, body {
      margin: 0;
      padding: 0;
      height: 100%;
    }

    body {
      font-family: Arial, sans-serif;
      background-color: white;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    #container {
      text-align: center;
    }

    #upload {
      margin-bottom: 20px;
    }

    #preview-container {
      width: 300px;
      height: 300px;
      margin: 0 auto 20px;
      border: 2px solid #ccc;
      background-color: white;
      overflow: hidden;
    }

    #preview {
      width: 100%;
      height: 100%;
    }

    canvas {
      display: block;
      margin: 0 auto;
    }

    button {
      margin: 5px;
      padding: 10px 20px;
      font-size: 14px;
      cursor: pointer;
    }
  </style>
</head>
<body>

<div id="container">
  <h1>PESOnize</h1>
  <input type="file" id="upload" accept="image/*">
    <br>
 <h2>Preview</h2> 
  <div id="preview-container">
    <div id="preview"></div>
  </div>

  <button onclick="pesonize()" style="background: linear-gradient(to right, #f6a5a5, #a5d8f6);">PESOnize!</button>
  <!-- <button onclick="pesonizeBlue()" style="background-color:rgb(125, 221, 245);">PESOnize Blue!</button> -->
  <!-- <button onclick="pesonizePink()" style="background-color:rgb(255, 174, 255);">PESOnize Pink!</button> -->
  <button onclick="downloadImage()"style="background-color:rgb(204, 255, 219);">Download</button>
</div>

<script src="cropper.min.js"></script>
<script>
  let cropper;
  const overlayBlue = new Image();
  overlayBlue.src = 'Pesonized.png';

  // const overlayPink = new Image();
  // overlayPink.src = 'pink1.png';

  let currentOverlay = overlayBlue;

  function initCropper(image) {
    const preview = document.getElementById('preview');
    preview.innerHTML = '';

    const img = new Image();
    img.src = image;
    img.id = 'cropper-image';
    img.style.maxWidth = '100%';
    preview.appendChild(img);

    cropper = new Cropper(img, {
      aspectRatio: 1,
      viewMode: 1,
      autoCropArea: 1,
      background: false,
      movable: false,
      zoomable: false,
      rotatable: false,
      scalable: false,
    });
  }

  // function pesonizeBlue() {
  //   applyOverlay(overlayBlue);
  // }

  function pesonize() {
    applyOverlay(overlayBlue);
  }

  // function pesonizePink() {
  //   applyOverlay(overlayPink);
  // }

  function applyOverlay(overlayImage) {
    if (!cropper) return alert('Please upload and crop an image first.');

    currentOverlay = overlayImage;

    const canvas = cropper.getCroppedCanvas({
      width: 300,
      height: 300,
    });

    composeFramedCanvas(canvas, overlayImage);

    const preview = document.getElementById('preview');
    preview.innerHTML = '';
    preview.appendChild(canvas);
  }

  function composeFramedCanvas(canvas, overlayImage) {
    const width = canvas.width;
    const height = canvas.height;
    const sourceCtx = canvas.getContext('2d');
    const sourceImage = sourceCtx.getImageData(0, 0, width, height);

    const overlayCanvas = document.createElement('canvas');
    overlayCanvas.width = width;
    overlayCanvas.height = height;

    const overlayCtx = overlayCanvas.getContext('2d');
    overlayCtx.drawImage(overlayImage, 0, 0, width, height);

    const overlayData = overlayCtx.getImageData(0, 0, width, height);
    const pixelCount = width * height;
    const outside = new Uint8Array(pixelCount);
    const queue = new Uint32Array(pixelCount);
    const alphaThreshold = 10;
    let head = 0;
    let tail = 0;

    function tryQueue(x, y) {
      const index = y * width + x;
      if (outside[index]) return;
      if (overlayData.data[index * 4 + 3] >= alphaThreshold) return;
      outside[index] = 1;
      queue[tail++] = index;
    }

    for (let x = 0; x < width; x++) {
      tryQueue(x, 0);
      tryQueue(x, height - 1);
    }

    for (let y = 1; y < height - 1; y++) {
      tryQueue(0, y);
      tryQueue(width - 1, y);
    }

    while (head < tail) {
      const index = queue[head++];
      const x = index % width;
      const y = Math.floor(index / width);

      if (x > 0) tryQueue(x - 1, y);
      if (x < width - 1) tryQueue(x + 1, y);
      if (y > 0) tryQueue(x, y - 1);
      if (y < height - 1) tryQueue(x, y + 1);
    }

    const maskedCanvas = document.createElement('canvas');
    maskedCanvas.width = width;
    maskedCanvas.height = height;

    const maskedCtx = maskedCanvas.getContext('2d');
    const maskedImage = maskedCtx.createImageData(width, height);

    for (let i = 0; i < pixelCount; i++) {
      const offset = i * 4;
      const isTransparent = overlayData.data[offset + 3] < alphaThreshold;
      const isFrameOpening = isTransparent && !outside[i];

      if (isFrameOpening) {
        maskedImage.data[offset] = sourceImage.data[offset];
        maskedImage.data[offset + 1] = sourceImage.data[offset + 1];
        maskedImage.data[offset + 2] = sourceImage.data[offset + 2];
        maskedImage.data[offset + 3] = sourceImage.data[offset + 3];
      }
    }

    sourceCtx.clearRect(0, 0, width, height);
    sourceCtx.fillStyle = 'white';
    sourceCtx.fillRect(0, 0, width, height);
    maskedCtx.putImageData(maskedImage, 0, 0);
    sourceCtx.drawImage(maskedCanvas, 0, 0);
    sourceCtx.drawImage(overlayCanvas, 0, 0);
  }

  function downloadImage() {
  if (!cropper || !currentOverlay) return alert("Please upload and process an image first.");

  // Adjusted canvas size for download
  const canvas = cropper.getCroppedCanvas({
    width: 800,
    height: 800,
  });

  composeFramedCanvas(canvas, currentOverlay);

  const link = document.createElement('a');
  link.download = 'PESOnized.png';
  link.href = canvas.toDataURL('image/png');
  link.click();
}

  document.getElementById('upload').addEventListener('change', function () {
    const file = this.files[0];
    if (!file) return;

    const reader = new FileReader();
    reader.onload = function (e) {
      initCropper(e.target.result);
    };
    reader.readAsDataURL(file);
  });
</script>

</body>
</html>
