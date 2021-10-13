### Install typescript: 
  npm install -g typescript
  
- Typescript compiler version => tsc -version
- Transpile ts to js => tsc file_name.ts


#### Declaring variables

let - can access within that block.
var - can access within that function. 

#### Types:

number
boolean
string
any
number[]
any[]

enum Color {Red, Blue, Green} or {Red=0, Blue=1, Green=2} both are same

#### Type assertions

let message; => type of any

message = 'any' , when you enter message. you won't get type intelisense

casting 

- (<string>message).endsWith or (message as string).endsWith
  
### arrow function:
  
  let log = function(message){
    console.log(message)
  } 
  
  transform to 
  
  let log = (message) => {
  console.log(message)
  }
  
  
  can rewritten to 
  
  let log = message => console.log(message);
  
  
  ### interface 
  
interface Point {
  x:number,
  y: number
  }
  
  drawpoint = (point: Point) =>{
  
  
  
  ### Classes
  
  class Point {
    private x:number;
    private y:number;
  
  constructor(x?:number, y?: number){
    this.x = x;
    this.y = y;
  }
  
  draw(){
    console.log(this.x, this.y)
  }
  
  let point = new Point(1, 2);
  this.draw();
  
  
  This can be written as simple as 
  
     
  constructor(private x?:number, private y?: number){
   }
  
  Constructor automatically does create variable and initialize
  
  
  ### Properties
  
  
  get X(){
    return this.x;
  }
  
  set X(value){
    this.x = value
  }
  
  this can accessed using instance variable 
  point = new Point();
  let x = point.X;
  point.X = 10;
  
  
  Instead of using variable using capital x, y 
  
  contructor(private _x?:number, private _y?:number){
  }
  
  get x(){
  }
  
  set x(){
  }
  
  Now this can be used as regular variable point.x instead of point.X
