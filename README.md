# p5js-to-svg

Use p5.js-svg library to convert the p5js element to svg. Add this in the `<head></head>` tag of your index.html

```html
<script src="https://unpkg.com/p5.js-svg@1.3.1"></script>
```

Create a button to save the svg file.
```html
<button type="button" id="saveSvgbtn" onclick="downloadSvg()">Save SVG</button>
```

In your sketch.js file, add this function.
```js
function downloadSvg() {
  noLoop();
  
  let svgElement = document.getElementsByTagName('svg')[0];
  let svg = svgElement.outerHTML;
  let file = new Blob([svg], { type: 'plain/text' });
  let a = document.createElement("a"), url = URL.createObjectURL(file);

  a.href = url;
  a.download = 'exported.svg';    
  document.body.appendChild(a);
  a.click();

  setTimeout(function() 
  {
      document.body.removeChild(a);
      window.URL.revokeObjectURL(url);  
  }, 0); 
}
```

In the `createCanvas()` function, add the `SVG` parameter.
```js
createCanvas(1080, 1080, SVG);
```
