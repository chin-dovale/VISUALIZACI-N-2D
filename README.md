


PFont textos;
int bs, bc, es, ec, mc, qs, qc, fs, fc, ms;
float tbs, tbc, tes, tec, tms, tmc, tqc, tqs, tfs, tfc, bmax, emax, mmax, qmax;
String year[]= {"2013", "2012", "2011", "2010", "2009", "2008", "2007", "2006", "2005", "2004", "2004", "2005", "2006", "2007", "2008", "2009", "2010", "2011", "2012", "2013"};

// Sectores
String message = "Biotecnología                               Ingeniería Eléctrica                                                                                                                                                                                                                                     Ingeniería Mecánica                                                                                                                                                                                                   Ingeniería Química                                                Q. Farmacéutica";

PFont f;
// The radius of a circle
float r = 440;


Table patentes;




void setup() {

  size(1200, 1000);


  textos= loadFont("CenturyGothic-15.vlw"); 
  textFont (textos, 15); 
  smooth(5);



  f = createFont("CenturyGothic", 15, true);
  textFont(f);
  textAlign(CENTER);
}

void draw() {
  
  


  background(255);

  fill(69);
  textFont (textos, 15); 
  text("PATENTES DE INVENCIÓN SOLICITADAS Y CONCEDIDAS POR RESIDENTES ANTE LA SUPERINTENDENCIA DE INDUSTRIA Y COMERCIO, POR SECTOR", 
    width / 2, height-30);


  pushMatrix();
  sectores_Ciencia();
  popMatrix();




  for (int p=0; p<20; p=p+2 ) { 

    strokeWeight(p+2);
    strokeCap(SQUARE);
    stroke(250);

    patentes= loadTable("TABLA PATENTES SIMPLIFICADA.csv", "header");   

    bc=patentes.getInt(0, p+2);//biotecnologia concedido - valor
    bs=patentes.getInt(0, p+1); //biotecnologia solicitado - valor
    tbs= map(bs, 0, 268, 0, 360);//biotecnologia solicitado - angulo equivalente
    tbc= map(bc, 0, 268, 0, 360);//biotecnologia concedido - angulo equivalente
    bmax=(360*(patentes.getInt(0, 19))/268);// máximo valor solicitado - angulo

    ec=patentes.getInt(1, p+2);//Ing eléctrica concedido - valor
    es=patentes.getInt(1, p+1);//Ing eléctrica solicitado-valor
    tes=map(es, 0, 268, 0, 360);//Ing eléctrica solicitado - angulo equivalente
    tec=map(ec, 0, 268, 0, 360);//Ing eléctrica concedido - angulo equivalente
    emax=(360*(patentes.getInt(1, 19))/268); //máximo valor solicitado - ángulo

    mc=patentes.getInt(2, p+2);//Ing mecánica concedido - valor
    ms=patentes.getInt(2, p+1);//Ing mecánica solicitado - valor
    tms=map(ms, 0, 268, 0, 360);//Ing mecánica solicitado - angulo equivalente
    tmc=map(mc, 0, 268, 0, 360);//Ing mecánica concedido - angulo equivalente
    mmax=(360*(patentes.getInt(2, 17))/268); //máximo valor solicitado - ángulo

    qc=patentes.getInt(3, p+2);//Ing química concedido - valor
    qs=patentes.getInt(3, p+1);//Ing química solicitado - valor
    tqs=map(qs, 0, 268, 0, 360);//Ing química solicitado - angulo equivalente
    tqc=map(qc, 0, 268, 0, 360);//Ing química concedido - angulo equivalente
    qmax=(360*(patentes.getInt(3, 20))/268); //máximo valor solicitado - ángulo

    fc=patentes.getInt(4, p+2);// química farmacéutica concedido - valor
    fs=patentes.getInt(4, p+1); // química farmacéutica solicitado - valor
    tfs=map(fs, 0, 268, 0, 360);// química farmacéutica concedido - angulo equivalente
    tfc=map(fc, 0, 268, 0, 360);// química farmacéutica concedido - angulo equivalente

    noFill();
    strokeWeight(p+2);
    strokeCap(SQUARE);
    stroke(250);

    ellipse(width/2, height/2, (p+10)*30, (p+10)*30);

    //BIOTECH

    //SOLICITADAS
    stroke(17, 239, 255, 70);//AZUL CLARITO
    arc(width/2, height/2, (p+10)*30, (p+10)*30, radians(0), radians(tbs), OPEN);

    //CONCEDIDAS
    stroke(17, 239, 255);//azul
    arc(width/2, height/2, (p+10)*30, (p+10)*30, radians(0), radians(tbc), OPEN);

    //ING ELÉCTRICA

    //SOLICITADAS
    stroke(224, 15, 47, 50);//ROJO CLARITO
    arc(width/2, height/2, (p+10)*30, (p+10)*30, radians(bmax), 
      radians(tbs+tes), OPEN);

    //CONCEDIDAS
    stroke(224, 15, 47);//ROJO
    arc(width/2, height/2, (p+10)*30, (p+10)*30, radians(bmax), radians(bmax+tec), OPEN);

    //ING MECÁNICA

    //SOLICITADAS
    stroke(12, 173, 184, 50);//AQUA CLARITO
    arc(width/2, height/2, (p+10)*30, (p+10)*30, radians(bmax+emax), 
      radians(bmax+emax+tms), OPEN);

    //CONCEDIDAS
    stroke(12, 173, 184);//AQUA
    arc(width/2, height/2, (p+10)*30, (p+10)*30, radians(bmax+emax), radians(bmax+emax+tmc), OPEN);

    //ING QUÍMICA

    //SOLICITADAS
    stroke(216, 246, 10, 50);//VERDE LIMON CLARITO
    arc(width/2, height/2, (p+10)*30, (p+10)*30, radians(bmax+emax+mmax), 
      radians(bmax+emax+mmax+tqs), OPEN);

    //CONCEDIDAS
    stroke(216, 246, 10);//VERDE LIMON
    arc(width/2, height/2, (p+10)*30, (p+10)*30, radians(bmax+emax+mmax), radians(bmax+emax+mmax+tqc), OPEN);

    // QUÍMICA FARMACÉUTICA

    //SOLICITADAS
    stroke(191, 28, 190, 50);//MAGENTA CLARITO
    arc(width/2, height/2, (p+10)*30, (p+10)*30, radians(bmax+emax+mmax+qmax), 
      radians(bmax+emax+mmax+qmax+tfs), OPEN);

    //CONCEDIDAS
    stroke(191, 28, 190);//MAGENTA
    arc(width/2, height/2, (p+10)*30, (p+10)*30, radians(bmax+emax+mmax+qmax), radians(bmax+emax+mmax+qmax+tfc), OPEN);
  }


  for (int y=0; y<20; y=y+2 ) { 

    stroke(0);
    fill(69);
    textFont (f, 10); 
    text(year[y/2], (width/2), (y+4.6)*15);
  }
}

void sectores_Ciencia() {

  translate(width / 2, height / 2);
  
  textFont(f);
  float arclength = 0;

  for (int i = 0; i < message.length(); i++)
  {
    // Instead of a constant width, we check the width of each character.
    char currentChar = message.charAt(i);
    float w = textWidth(currentChar);

    // Each box is centered so we move half the width
    arclength += w/2;
    // Angle in radians is the arclength divided by the radius
    // Starting on the left side of the circle by adding PI
    float theta = arclength / r;    

    pushMatrix();
    // Polar to cartesian coordinate conversion
    translate(r*cos(theta), r*sin(theta));
    // Rotate the box
    rotate(theta+PI/2); // rotation is offset by 90 degrees
    // Display the character
    fill(69);
    text(currentChar, 0, 0);
    popMatrix();
    // Move halfway again
    arclength += w/2;
  }
}
