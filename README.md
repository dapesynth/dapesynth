var img;

function preload() {
	// 500 x 500 px
	img = loadImage("Abi1.jpg");
}

function setup() {
	createCanvas(500, 500);
	background(0);
}

function draw() {
	background(255);
	//image(img, 0, 0);
	
	// Pixel in Speicher laden
	img.loadPixels();

	// Zeilen
	for (var y = 0; y < img.height; y += 20) {
		// Spalten
		for (var x = 0; x < img.width; x += 20) {
			// Simple but slow
      var pixel = img.get(x, y);
      
			// Fast but complicated
      var pixel = img.pixels[(y*img.width+x)*4];
			
			//var pixel_r = img.pixels[(y*img.width+x)*4];
			//var pixel_g = img.pixels[(y*img.width+x)*4+1];
			//var pixel_b = img.pixels[(y*img.width+x)*4+2];
			
			//fill(255);
			//textSize(8);
			//text(int(pixel), x, y);
			
			noFill();
			stroke(0);
			// Rechtecke
			//rect(x, y, pixel/20, pixel/20);
			
			stroke(0, 51, 204);
			var s = map(pixel, 0, 255, 1, 5);
			strokeWeight(s);
			//strokeCap(SQUARE);
			
		//	rectMode(CENTER);
			
			push();
			translate(x, y);
			var a = map(pixel, 0, 255, 0, PI);
			rotate(a);
			//rect(0, 0, 10, 10);
			ellipse(0, 0, 20, pixel/20);
			//line(0, 0, 20, 0);
			//line(0, 0, 0, 20);
			pop();
			
			/*
			if (pixel < 125)
				rect(x, y, pixel/20, pixel/20);
			else
				ellipse(x, y, pixel/20, pixel/20);
				*/
			
			
			
			// Windfahnen / Rechtecke
			/*
			push();
			translate(x, y);
			var a = map(pixel, 0, 255, 0, PI);
			rotate(a);
			//line(0, 0, 10, 0);
			fill(pixel_r, pixel_g, pixel_b);
			rect(0, 0, pixel/20, pixel/20);
			pop();
			*/
			
			//vertex(x, y+pixel/mouseY/2);
		}
	}
}
