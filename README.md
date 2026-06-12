# -D
function setup() {
  createCanvas(700, 550);
  noLoop();
}

function draw() {
  background(220, 215, 190);

  paintTexture();

  drawHouse();
  drawWindows();
  drawDoor();
  drawCharacter();

  drawFoliage(0, height * 0.6, width, height * 0.4);

  overlayBrushes();
}

function drawHouse() {
  noStroke();

  fill(205, 220, 200, 240);
  rect(160, 40, 380, 340);

  fill(220, 215, 200, 200);
  rect(270, 190, 160, 190);
}

function drawWindows() {
  fill(25, 30, 35, 230);

  rect(275, 0, 70, 80);
  rect(360, 0, 70, 80);

  rect(505, 150, 70, 110);
  rect(65, 150, 85, 110);

  stroke(80, 90, 90, 100);
  line(540, 150, 540, 260);
  line(107, 150, 107, 260);
}

function drawDoor() {
  noStroke();

  fill(125, 70, 65);
  rect(310, 225, 90, 145);

  fill(150, 90, 75, 120);
  rect(325, 240, 55, 50);
}

function drawCharacter() {
  push();
  translate(350, 300);

  fill(235, 220, 180);
  noStroke();
  ellipse(0, -35, 34, 42);

  fill(30);
  ellipse(-6, -38, 5);
  ellipse(6, -38, 5);

  fill(210, 95, 65, 200);
  quad(-18, -15, 18, -15, 30, 40, -10, 35);

  fill(60, 90, 180, 180);
  triangle(10, 0, 45, 35, 15, 55);

  stroke(50);
  strokeWeight(3);

  line(-3, 35, -10, 85);
  line(12, 35, 18, 85);

  line(-10, 0, -35, 40);
  line(12, 0, 35, 25);

  pop();
}

function drawFoliage(x, y, w, h) {
  noStroke();

  for (let i = 0; i < 900; i++) {
    let px = random(x, x + w);
    let py = random(y, y + h);

    fill(
      random(25, 90),
      random(50, 120),
      random(20, 70),
      random(40, 140)
    );

    push();
    translate(px, py);
    rotate(random(TWO_PI));

    beginShape();
    vertex(-15, 0);
    vertex(0, -8);
    vertex(15, 0);
    vertex(0, 8);
    endShape(CLOSE);

    pop();
  }

  for (let i = 0; i < 40; i++) {
    stroke(60, 70, 40, 100);
    strokeWeight(random(2, 6));

    let sx = random(width);
    let sy = random(height * 0.35);

    noFill();
    beginShape();

    for (let j = 0; j < 5; j++) {
      curveVertex(
        sx + j * random(20, 50),
        sy + random(-30, 30)
      );
    }

    endShape();
  }
}

function paintTexture() {
  noStroke();

  for (let i = 0; i < 3000; i++) {
    fill(
      random(180, 240),
      random(170, 220),
      random(140, 210),
      12
    );

    ellipse(
      random(width),
      random(height),
      random(5, 25)
    );
  }
}

function overlayBrushes() {
  strokeWeight(18);

  for (let i = 0; i < 80; i++) {
    stroke(
      random(70, 180),
      random(80, 170),
      random(70, 150),
      18
    );

    line(
      random(width),
      random(height),
      random(width),
      random(height)
    );
  }

  noStroke();

  for (let i = 0; i < 30; i++) {
    fill(
      random(120, 220),
      random(120, 200),
      random(80, 180),
      30
    );

    rect(
      random(width),
      random(height),
      random(30, 150),
      random(30, 150)
    );
  }
}
