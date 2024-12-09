let circles = [];

function setup() {
  createCanvas(600, 400);
  
  // Create 10 circles with random positions and sizes
  for (let i = 0; i < 10; i++) {
    circles.push({
      x: random(width),
      y: random(height),
      size: random(10, 50),
      speedX: random(-2, 2),
      speedY: random(-2, 2)
    });
  }
}

function draw() {
  background(30);

  for (let circle of circles) {
    // Update the position
    circle.x += circle.speedX;
    circle.y += circle.speedY;

    // Update the size
    circle.size += 0.5;

    // Conditional: If the circle gets too big, change its color
    if (circle.size > 100) {
      fill(255, 0, 0); // Red
    } else {
      fill(0, 255, 0); // Green
    }

    // Draw the circle
    noStroke();
    ellipse(circle.x, circle.y, circle.size);

    // Wrap around the edges
    if (circle.x > width) circle.x = 0;
    if (circle.x < 0) circle.x = width;
    if (circle.y > height) circle.y = 0;
    if (circle.y < 0) circle.y = height;
  }
}
