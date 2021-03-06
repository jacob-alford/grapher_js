# grapher_js
A simple javascript R2xR2 graphing library

![exGraph](graph.png)
## Dependencies
Requires:
* [p5.js](https://p5js.org/)
* [matrix_js](https://github.com/jacob-alford/matrix_js) (my matrix library)

## Example
### Vectors
#### Creation
```
let a = new Matrix([2,2]);
let b = new Matrix([-1,3]);
let c = Matrix.add(a,b);
```
#### Graphing
```
stroke("blue");
drawVector(a,origin);

stroke("green");
drawVector(b,toCoords(a));

stroke("yellow");
drawVector(c,origin);
```
### Scatter Plots
#### Creation
```
let points = [];
for(let i=0;i<500;i++){
  points.push(mat_rand([2],0,15));
}
```
#### Graphing
```
stroke("pink");
scatter(points);
```
### Functions in Rn
#### Creation
```
const f = (x,coeff = 1) => x*sin(-coeff*x) + 3;
```
#### Graphing
```
stroke("red");
graph(f);
```
### Configuration
```
const xLim = [-2,16];
const yLim = [-2,16];
const dims = [500,500];
const filename = "graph";
const backgroundColor = "black";
const majorGridLineColor = 200;
const minorGridLineColor = 50;
const textColor = 200;
const textSz = 15;
const textOffset = [-4,18];
```
*Note:*
> The origin object referenced above is an array which determines the pixel dimensions of the origin point depending on initial configuration.
## Initial Configuration
Title | Function | Type
------------ | ------------- | -------------
xLim | Sets the limits of the x-axis, each integer is its own line. | Array, length 2
yLim | Sets the limits of the y-axis, each integer is its own line. | Array, length 2
dims | Sets the diminsions of the canvas (in pixels). | Array, length 2
filename | The filename of the saved image. | String
backgroundColor | The background color of the graph | [p5.js Color Object](https://p5js.org/reference/#/p5.Color); Integer [0-255]; String ("black")
majorGridColor | The major axis color of the graph | [p5.js Color Object](https://p5js.org/reference/#/p5.Color); Integer [0-255]; String ("black")
minorGridColor | The grid line color of the graph | [p5.js Color Object](https://p5js.org/reference/#/p5.Color); Integer [0-255]; String ("white")
textColor | The color of the numbers on the graph | [p5.js Color Object](https://p5js.org/reference/#/p5.Color); Integer [0-255]; String ("gray")
textSz | The size of the numbers on the graph | Number
textOffset | The x and y offset in pixels of the numbers on the graph | Array, length 2

## Supporting Functions
Title | Description | Returns
------------ | ------------- | -------------
toCoords(mat) | Takes a matrix_js vector and returns an array whose values are converted into the specs of the graph. | Array
drawVector(mat,initPt) | Takes a matrix_js vector and draws a vector to the graph.  InitPt is the origin point of the vector. | N/A
saveImage() | Saves the canvas to a png file | N/A
graph(function) | Graphs a function in Rn | N/A
scatter(array) | Graphs an array of matrix_js vectors as points with radius 1.5px | N/A
createGraph() | The function which draws the grid to the canvas with numbers. | N/A
