// see: https://en.wikipedia.org/wiki/6-cube
// Hexeract_008 
// by Rupert Russell
// 15 June 2019


float[] outerX = new float[13];
float[] outerY = new float[13];

float[] innerX = new float[13];
float[] innerY = new float[13];


float[] secondInnerX = new float[26];
float[] secondInnerY = new float[26];

float[] thirdInnerX = new float[13];
float[] thirdInnerY = new float[13];


int count = 0;
int es = 20; // small ellipse size

float outerRadius = 400;
float innerRadius = 107;  
float secondInnerRadius = 208;  
float thirdInnerRadius = 293; 



void setup() {
  background(255); 
  size(900, 900);
  smooth(8);
  noLoop();
  strokeWeight(3);
}



void draw() {

  translate(width/2, height/2); 
  double step = 2 * PI/12; 
  double secondInnerStep = 2 * PI/24; 


  for (float theta=0; theta < 2 * PI; theta += step) {
    float x =  outerRadius * cos(theta);
    float y =  outerRadius * sin(theta); 
    fill(255, 0, 0);
    outerX[count] = x;
    outerY[count] = y;
    count = count + 1;
    print(count);
  }


  // Locate innermost 24 points
  count = 0;
  for (float theta=0; theta < 2 * PI; theta += step) {
    float x =  innerRadius * cos(theta);
    float y =  innerRadius * sin(theta); 
    fill(255, 0, 0);
    innerX[count] = x;
    innerY[count] = y;
    count = count+ 1;
  }


  // Locate second innermost 12 points
  count = 0;
  for (float theta=0; theta < 2 * PI; theta += secondInnerStep) {
    float x =  secondInnerRadius * cos(theta);
    float y =  secondInnerRadius * sin(theta); 
    fill(255, 0, 0);
    secondInnerX[count] = x;
    secondInnerY[count] = y;
    count = count+ 1;
  }


  // Locate second innermost 12 points
  count = 0;
  for (float theta=0; theta < 2 * PI; theta += step) {
    float x =  thirdInnerRadius * cos(theta);
    float y =  thirdInnerRadius * sin(theta); 
    fill(255, 0, 0);
    thirdInnerX[count] = x;
    thirdInnerY[count] = y;
    count = count+ 1;
  }


  // Draw outermost circumference
  for (int count = 0; count < 12; count = count + 1) {
    line(outerX[count], outerY[count], outerX[count + 1], outerY[count + 1]);
  }


  line(outerX[0], outerY[0], outerX[7], outerY[7]);
  line(outerX[2], outerY[2], outerX[7], outerY[7]);
  line(outerX[1], outerY[1], outerX[6], outerY[6]);
  line(outerX[3], outerY[3], outerX[10], outerY[10]);
  line(outerX[5], outerY[5], outerX[10], outerY[10]);
  line(outerX[2], outerY[2], outerX[9], outerY[9]);
  line(outerX[4], outerY[4], outerX[9], outerY[9]);
  line(outerX[3], outerY[3], outerX[8], outerY[8]);
  line(outerX[1], outerY[1], outerX[8], outerY[8]);
  line(outerX[4], outerY[4], outerX[11], outerY[11]);
  line(outerX[6], outerY[6], outerX[11], outerY[11]);
  line(outerX[0], outerY[0], outerX[5], outerY[5]);


  // inner lines

  for (int count = 0; count < 5; count = count + 1) {
    line(innerX[count], innerY[count], innerX[count + 7], innerY[count + 7]);
    line(innerX[count], innerY[count], innerX[count + 5], innerY[count + 5]);
  }
  line(innerX[5], innerY[5], innerX[5 + 5], innerY[5 + 5]);
  line(innerX[6], innerY[6], innerX[6 + 5], innerY[6 + 5]);


  // secondInner lines
  for (int count = 3; count < 20; count = count + 4) {
    line(secondInnerX[count], secondInnerY[count], secondInnerX[count + 4], secondInnerY[count + 4]);
  }
  line(secondInnerX[3], secondInnerY[3], secondInnerX[23], secondInnerY[23]);

  for (int count = 1; count < 20; count = count + 4) {
    line(secondInnerX[count], secondInnerY[count], secondInnerX[count + 4], secondInnerY[count + 4]);
  }

  line(secondInnerX[21], secondInnerY[21], secondInnerX[1], secondInnerY[1]);

  for (int count = 1; count < 12; count = count + 2) {
    line(secondInnerX[count], secondInnerY[count], secondInnerX[count + 12], secondInnerY[count + 12]);
  }

  //guidelines
  //line(outerX[8], outerY[8], outerX[11], outerY[11]);
  //line(outerX[8], outerY[8], outerX[5], outerY[5]);
  //line(outerX[2], outerY[2], outerX[5], outerY[5]);
  //line(outerX[2], outerY[2], outerX[11], outerY[11]);

  //line(outerX[7], outerY[7], outerX[10], outerY[10]);
  //line(outerX[7], outerY[7], outerX[4], outerY[4]);
  //line(outerX[4], outerY[4], outerX[2], outerY[2]);
  //line(outerX[1], outerY[1], outerX[10], outerY[10]);

  line(thirdInnerX[1], thirdInnerY[1], outerX[0], outerY[0]);
  line(thirdInnerX[11], thirdInnerY[11], outerX[0], outerY[0]);
  line(thirdInnerX[1], thirdInnerY[1], innerX[0], innerY[0]);
  line(thirdInnerX[11], thirdInnerY[11], innerX[0], innerY[0]);

  line(thirdInnerX[0], thirdInnerY[0], outerX[1], outerY[1]);
  line(thirdInnerX[2], thirdInnerY[2], outerX[1], outerY[1]);
  line(thirdInnerX[2], thirdInnerY[2], innerX[1], innerY[1]);
  line(thirdInnerX[0], thirdInnerY[0], innerX[1], innerY[1]);

  line(thirdInnerX[1], thirdInnerY[1], outerX[2], outerY[2]);
  line(thirdInnerX[3], thirdInnerY[3], outerX[2], outerY[2]);
  line(thirdInnerX[3], thirdInnerY[3], innerX[2], innerY[2]);
  line(thirdInnerX[1], thirdInnerY[1], innerX[2], innerY[2]);

  line(thirdInnerX[4], thirdInnerY[4], outerX[3], outerY[3]);
  line(thirdInnerX[2], thirdInnerY[2], outerX[3], outerY[3]);
  line(thirdInnerX[4], thirdInnerY[4], innerX[3], innerY[3]);
  line(thirdInnerX[2], thirdInnerY[2], innerX[3], innerY[3]);

  line(thirdInnerX[5], thirdInnerY[5], outerX[4], outerY[4]);
  line(thirdInnerX[3], thirdInnerY[3], outerX[4], outerY[4]);
  line(thirdInnerX[3], thirdInnerY[3], innerX[4], innerY[4]);
  line(thirdInnerX[5], thirdInnerY[5], innerX[4], innerY[4]);

  line(thirdInnerX[4], thirdInnerY[4], outerX[5], outerY[5]);
  line(thirdInnerX[6], thirdInnerY[6], outerX[5], outerY[5]);
  line(thirdInnerX[4], thirdInnerY[4], innerX[5], innerY[5]);
  line(thirdInnerX[6], thirdInnerY[6], innerX[5], innerY[5]);

  line(thirdInnerX[5], thirdInnerY[5], outerX[6], outerY[6]);
  line(thirdInnerX[7], thirdInnerY[7], outerX[6], outerY[6]);
  line(thirdInnerX[5], thirdInnerY[5], innerX[6], innerY[6]);
  line(thirdInnerX[7], thirdInnerY[7], innerX[6], innerY[6]);

  line(thirdInnerX[6], thirdInnerY[6], outerX[7], outerY[7]);
  line(thirdInnerX[8], thirdInnerY[8], outerX[7], outerY[7]);
  line(thirdInnerX[6], thirdInnerY[6], innerX[7], innerY[7]);
  line(thirdInnerX[8], thirdInnerY[8], innerX[7], innerY[7]);


  line(thirdInnerX[7], thirdInnerY[7], outerX[8], outerY[8]);
  line(thirdInnerX[9], thirdInnerY[9], outerX[8], outerY[8]);
  line(thirdInnerX[7], thirdInnerY[7], innerX[8], innerY[8]);
  line(thirdInnerX[9], thirdInnerY[9], innerX[8], innerY[8]);

  line(thirdInnerX[8], thirdInnerY[8], outerX[9], outerY[9]);
  line(thirdInnerX[10], thirdInnerY[10], outerX[9], outerY[9]);
  line(thirdInnerX[8], thirdInnerY[8], innerX[9], innerY[9]);
  line(thirdInnerX[10], thirdInnerY[10], innerX[9], innerY[9]);

  line(thirdInnerX[9], thirdInnerY[9], outerX[10], outerY[10]);
  line(thirdInnerX[11], thirdInnerY[11], outerX[10], outerY[10]);
  line(thirdInnerX[11], thirdInnerY[11], innerX[10], innerY[10]);
  line(thirdInnerX[9], thirdInnerY[9], innerX[10], innerY[10]);

  line(thirdInnerX[0], thirdInnerY[0], outerX[11], outerY[11]);
  line(thirdInnerX[10], thirdInnerY[10], outerX[11], outerY[11]);
  line(thirdInnerX[0], thirdInnerY[0], innerX[11], innerY[11]);
  line(thirdInnerX[10], thirdInnerY[10], innerX[11], innerY[11]);



  line(thirdInnerX[3], thirdInnerY[3], outerX[2], outerY[2]);
  line(thirdInnerX[3], thirdInnerY[3], outerX[4], outerY[4]);


  // ---

  line(thirdInnerX[8], thirdInnerY[8], thirdInnerX[11], thirdInnerY[11]);
  line(thirdInnerX[11], thirdInnerY[11], thirdInnerX[2], thirdInnerY[2]);
  line(thirdInnerX[8], thirdInnerY[8], thirdInnerX[11], thirdInnerY[11]);
  line(thirdInnerX[5], thirdInnerY[5], thirdInnerX[2], thirdInnerY[2]);
  line(thirdInnerX[5], thirdInnerY[5], thirdInnerX[8], thirdInnerY[8]);

  line(thirdInnerX[7], thirdInnerY[7], thirdInnerX[10], thirdInnerY[10]);
  line(thirdInnerX[10], thirdInnerY[10], thirdInnerX[1], thirdInnerY[1]);
  line(thirdInnerX[1], thirdInnerY[1], thirdInnerX[4], thirdInnerY[4]);
  line(thirdInnerX[4], thirdInnerY[4], thirdInnerX[7], thirdInnerY[7]);

  line(thirdInnerX[5], thirdInnerY[5], thirdInnerX[8], thirdInnerY[8]);
  line(thirdInnerX[8], thirdInnerY[8], thirdInnerX[11], thirdInnerY[11]);
  line(thirdInnerX[11], thirdInnerY[11], thirdInnerX[2], thirdInnerY[2]);
  line(thirdInnerX[2], thirdInnerY[2], thirdInnerX[5], thirdInnerY[5]);

  line(thirdInnerX[9], thirdInnerY[9], thirdInnerX[0], thirdInnerY[0]);
  line(thirdInnerX[0], thirdInnerY[0], thirdInnerX[3], thirdInnerY[3]);
  line(thirdInnerX[3], thirdInnerY[3], thirdInnerX[6], thirdInnerY[6]);
  line(thirdInnerX[6], thirdInnerY[6], thirdInnerX[9], thirdInnerY[9]);

  fill(255, 0, 0);
  for (int count = 0; count < 12; count = count + 1) {
    ellipse(outerX[count], outerY[count], es, es);
  }

  fill(255,0,0);
  for (int count = 0; count < 12; count = count + 1) {
    ellipse(innerX[count], innerY[count], es, es);
  }

  fill(255, 127, 0);
  for (int count = 1; count < 24; count = count + 2) {
    ellipse(secondInnerX[count], secondInnerY[count], es, es);
  }

  fill(255, 0, 0);
  for (int count = 0; count < 12; count = count + 1) {
    ellipse(thirdInnerX[count], thirdInnerY[count], es, es);
  }

  fill(255, 255, 0);
  ellipse(0, 0, es, es);

  save("hexeract_008.png");
}
