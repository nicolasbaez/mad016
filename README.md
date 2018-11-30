# mad016
basic scale loop

![mad016](https://github.com/nicolasbaez/mad016/blob/master/mad016.gif)

```processing
float xRad;
float yRad;
float xyRadMax;
float rr;
float gg;
float bb;
float j=45;
float k=0;
float f=0;
void setup() {
  size(512, 256);
  background(255);
  noStroke();
}
void draw() {
  fill(255, 255, 255, 32);
  rect(0, 0, width, height);
  rr=map(sin(radians(k)), -1, 1, 0, 255);
  gg=random(map(sin(radians(k)), -1, 1, 255, 0));
  bb=map(sin(radians(k)), -1, 1, 255, 0);
  fill(rr, gg, bb);
  beginShape();
  for (float i=j; i<=360+j; i+=360/4) {
    float xx=xRad*cos(radians(i))+width*0.5;
    float yy=yRad*sin(radians(i))+height*0.5;
    vertex(xx, yy);
  }
  endShape();
  float xMap=map(k, 0, 360, 0, 90);
  if (xMap>0&&xMap<=22.5) {
    xRad=map(sin(radians(xMap)), 0, 1, 0, height*0.25);
    yRad=map(sin(radians(xMap)), 0, 1, 0, height*0.25);
  }
  if (xMap>22.5&&xMap<=45) {
    xRad=map(sin(radians(xMap)), 0, 1, 0, height*0.5);
    yRad=map(sin(radians(xMap)), 0, 1, 0, height*0.25);
  }
  if (xMap>45&&xMap<=67.5) {
    xRad=map(sin(radians(xMap)), 0, 1, 0, height*0.5);
    yRad=map(sin(radians(xMap)), 0, 1, 0, height*0.5);
    xyRadMax=map(sin(radians(xMap)), 0, 1, 0, height*0.5);
  }
  if (xMap>67.5&&xMap<=90) {
    xRad=map(xMap, 67.5, 90, xyRadMax, 0);
    yRad=map(xMap, 67.5, 90, xyRadMax, 0);
  }
  if (k>=360) {
    k=0;
  }
  k+=map(sin(radians(k)), -1, 1, 1, 4);
  f+=map(sin(radians(k)), -1, 1, 1, 4);
  if (f>=360&&f<=720) {
    saveFrame("gif/mad016-######.png");
  }
}
```
