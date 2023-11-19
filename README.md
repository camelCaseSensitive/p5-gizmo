# p5-gizmo
Gizmo for 3D translation control in p5js WEBGL mode

## Installation

Add this [CDN](https://cdn.jsdelivr.net/npm/p5-gizmo@1.0.0/gizmo.js) to a script tag in your index.html file 

```
<script src="https://cdn.jsdelivr.net/npm/p5-gizmo@1.0.0/gizmo.js"></script>
```


or Install via the command line

```bash
npm i p5-gizmo
```

## Usage


Define a camera variable called `cam` in the setup function
```javascript
cam = createCamera();
g = new gizmo(0, 0, 0)
```

Use g.show in the draw loop.

I would also recommend disabling orbitControl when gizmo is clicked: 
```javascript
if(!g.gizmoClicked) orbitControl()
```

Use g.update in the mousePressed function.
Use g.released in the mouseReleased function.

```javascript
function mousePressed() {
  if(g.hover){
    g.update()
  }
}

function mouseReleased() {
  g.released()
}
```
Complete example:
```javascript
function setup() {
  createCanvas(400, 400, WEBGL);
  cam = createCamera()
  g = new gizmo(0, 0, 0)
}

function draw() {
  background(220);
  lights()
  if(!g.gizmoClicked) orbitControl()
  g.show()
}

function mousePressed() {
  if(g.hover){
    g.update()
  }
}

function mouseReleased() {
  g.released()
}
```

## Example in p5 editor
[3D Gizmo - Transform Controls in p5js](https://editor.p5js.org/rjgilmour/sketches/hLoOCscm8)

## Dependencies

The matrix math for raycasting is done with [math.js](https://cdnjs.com/libraries/mathjs)

Copy and paste this script tag into your `index.html` file

```
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjs/11.8.1/math.js" integrity="sha512-5nftKkjZO1gtHEWFlUGXi/vuXzFnWTom549IH/gMqOiJHcPfH5z/1DO8/c0qnoG0R8RCVLOeBDXhCjg2+23nqQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

## License

[MIT](https://choosealicense.com/licenses/mit/)
