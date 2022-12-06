#include <GL/gl.h>
#include <GL/glut.h>
#include<bits/stdc++.h>
#include <stdio.h>
 #include<Windows.h>
 #include<mmsystem.h>

int intVariable=0;
static float	tx	=  0.0;
static float	ty	=  0.0;
int mm=0;/////
int k=0;
float p = 0;
float anti=0;
float j = 0;
float c=0;
float px=0;
float py=0;
float mo=0;


float f = -1;
bool flag = true;

void declare(char* string) {
    while (*string) {
        glutBitmapCharacter(GLUT_BITMAP_9_BY_15, *string++);
    }
}

void target() {


    glColor3f(0.9,0.2,0.9 );
    glRasterPos2f(-2.86, 80.59);
    declare(" Successfully Destroyed");
}

void gameover() {

    glColor3f(1.0, 0.0, 0.0);
    glRasterPos2f(-2.86, 80.59);
    declare("Target Failed. Please try again.");
}

void axis()
{
    glColor3f (1.0, 1.0, 0.0);
glBegin(GL_LINES);
//axix-Y
glVertex2f(0.0f, 100.0f );
glVertex2f(0.0f, -100.0f );
glEnd();

    glColor3f (1.0, 1.0, 0.0);
glBegin(GL_LINES);
//axix-X
glVertex2f(-100.0f, 0.0f );
glVertex2f(100.0f, 0.0f );
glEnd();
}
void sky()///////////////////////////////////////////////////// sky
{
glBegin(GL_POLYGON);

//glColor3f(0.5,0.9,1);
glColor3f(0.5,1,1);
glVertex2f(-100.0f, 0.0f );
glVertex2f(100.0f, 0.0f );
glVertex2f(100.0f, 100.0f );
glVertex2f(-100.0f, 100.0f );

glEnd();
}
void cloud(GLfloat rx, GLfloat ry, GLfloat cx, GLfloat cy)/////////////////////////////$$$$ cloud
{
glBegin(GL_TRIANGLE_FAN);
glColor3f(1.0,1.0,1.0);
glVertex2f(cx, cy);
for (int i = 0;i <= 100;i++)
{
float angle = 2.0f * 3.1416f * i / 100;
float x = rx * cosf(angle);
float y = ry * sinf(angle);
glVertex2f((x + cx), (y + cy));
}
glEnd();
}
void runcloud()
{
    if(c<=200)
{
    c=c+.005;
}
else{
    c=-100;
}
///////////////////////////--------------cloud-2---------/////////////
    cloud(5,7,c-36,67);
cloud(5,7,c-36,60);
cloud(5,7,c-28,67);
cloud(5,7,c-28,60);
cloud(5,7,c-21,67);
cloud(5,7,c-21,60);
///////////////////////////--------------cloud-2---------/////////////
cloud(5,7,c+5,67);
cloud(5,7,c+5,60);
cloud(5,7,c+14,67);
cloud(5,7,c+14,60);
cloud(5,7,c+21,67);
cloud(5,7,c+21,60);
}

void half(GLfloat rx, GLfloat ry, GLfloat cx, GLfloat cy)////////////////////black
{
glBegin(GL_TRIANGLE_FAN);
glColor3f(0.0,0.3,0.9);
glVertex2f(cx, cy);
for (int i = 50;i <= 100;i++)
{
float angle = 2.0f * 3.1416f * i / 100;
float x = rx * cosf(angle);
float y = ry * sinf(angle);
glVertex2f((x + cx), (y + cy));
}
glEnd();
}
void circle(GLfloat rx, GLfloat ry, GLfloat cx, GLfloat cy)/////circle
{
glBegin(GL_TRIANGLE_FAN);
glColor3f(0.0f, 0.50f, 0.90f);
glVertex2f(cx, cy);
for (int i = 0;i <= 100;i++)
{
float angle = 2.0f * 3.1416f * i / 100;
float x = rx * cosf(angle);
float y = ry * sinf(angle);
glVertex2f((x + cx), (y + cy));
}
glEnd();
}
void helicopter()//////////****************************************** helicopter
{
    glBegin(GL_POLYGON); //// pankha
     //glColor3f (1,0.9,0.1);
     glColor3f(0.0,0.20,0.20);
     //glColor3f(0.6,0,0.3);

glVertex2f(p+-60.0f, 76.0f );
glVertex2f(p+-50.0f, 76.0f );
glVertex2f(p+-50.0f, 75.0f );
glVertex2f(p+-60.0f, 75.0f );

glEnd();

   glBegin(GL_POLYGON); //// danda
     //glColor3f (1,0.9,0.1);
     glColor3f(0.0,0.20,0.20);
     //glColor3f(0.6,0,0.3);

glVertex2f(p+-55.0f, 75.0f );
glVertex2f(p+-54.0f, 75.0f );
glVertex2f(p+-54.0f, 74.0f );
glVertex2f(p+-55.0f, 74.0f );

glEnd();

   glBegin(GL_POLYGON); //// head
     //glColor3f (1,0.9,0.1);
     //glColor3f(0.7,0,0.1 );
     glColor3f(0.0,0.20,0.20);

glVertex2f(p+-53.0f, 74.0f );
glVertex2f(p+-51.0f, 72.0f );
glVertex2f(p+-51.0f, 71.0f );
glVertex2f(p+-53.0f, 71.0f );

glEnd();
   glBegin(GL_POLYGON); //// body
     //glColor3f (1,0.9,0.1);
     //glColor3f(0.5,0.5,0);
      //glColor3f(0.7,0,0.1 );
      glColor3f(0.0,0.20,0.20);

glVertex2f(p+-56.0f, 74.0f );
glVertex2f(p+-53.0f, 74.0f );
glVertex2f(p+-53.0f, 71.0f );
glVertex2f(p+-56.0f, 71.0f );
glVertex2f(p+-58.0f, 71.0f );
glVertex2f(p+-58.0f, 72.0f );

glEnd();

   glBegin(GL_POLYGON); //// danda of lenjja
     //glColor3f (1,0.9,0.1);
     //glColor3f(0.5,0.5,0);
     //glColor3f(0.7,0,0.1 );
     glColor3f(0.0,0.20,0.20);

glVertex2f(p+-62.0f, 72.0f );
glVertex2f(p+-58.0f, 72.0f );
glVertex2f(p+-58.0f, 71.0f );
glVertex2f(p+-62.0f, 71.0f );

glEnd();

   glBegin(GL_POLYGON); //// tail
     //glColor3f (1,0.9,0.1);
     //glColor3f(0.5,0.5,0);
      //glColor3f(0.7,0,0.1 );
      glColor3f(0.0,0.20,0.20);

glVertex2f(p+-64.0f, 74.0f );
glVertex2f(p+-62.0f, 74.0f );
glVertex2f(p+-61.0f, 72.0f );
glVertex2f(p+-61.0f, 71.0f );
glVertex2f(p+-64.0f, 71.0f );
glEnd();

/////////////////////////////////////for helicopter
if(p<=200)
{
    p=p+.02;

}
else{
    p=-100;
}

}
void radar()////////////################################################### radar
{


     glBegin(GL_POLYGON); //// triangle
     //glColor3f (1,0.9,0.1);
     glColor3f(0.5,0.5,0);

glVertex2f(90.0f, -42.0f );
glVertex2f(92.0f, -45.0f );
glVertex2f(88.0f, -45.0f );

glEnd();
    glBegin(GL_POLYGON); //// rectangle
     //glColor3f (1,0.9,0.1);
     glColor3f(0.1,0.1,0.2);

glVertex2f(88.0f, -45.0f );
glVertex2f(92.0f, -45.0f );
glVertex2f(92.0f, -60.0f );
glVertex2f(88.0f, -60.0f );
glEnd();

    glBegin(GL_POLYGON); //// triangle
     //glColor3f (1,0.9,0.1);
     glColor3f(0.0,0.5,0.9);

glVertex2f(95.0f, -52.0f );
glVertex2f(95.0f, -60.0f );
glVertex2f(85.0f, -60.0f );
glEnd();

circle(2,2,90,-40);
 half(7,6,90,-45);

}

void mountain()////////////################################################### mountain
{
     glBegin(GL_POLYGON); //// mountain1
     //glColor3f (1,0.9,0.1);
     glColor3f(0.5,0.5,0);

glVertex2f(-100.0f, 0.0f );
glVertex2f(-75.0f, 40.0f );
glVertex2f(-50.0f, 0.0f );

glEnd();

     glBegin(GL_POLYGON); //// mountain2
     //glColor3f (1,0.9,0.1);
     glColor3f(0.5,0.5,0);

glVertex2f(-75.0f, 0.0f );
glVertex2f(-50.0f, 40.0f );
glVertex2f(-25.0f, 0.0f );

glEnd();
     glBegin(GL_POLYGON); //// mountain3
     //glColor3f (1,0.9,0.1);
     glColor3f(0.5,0.5,0);

glVertex2f(-50.0f, 0.0f );
glVertex2f(-25.0f, 40.0f );
glVertex2f(0.0f, 0.0f );

glEnd();

     glBegin(GL_POLYGON); //// mountain5
     //glColor3f (1,0.9,0.1);
     glColor3f(0.5,0.5,0);

glVertex2f(-60.0f, 0.0f );
glVertex2f(-37.0f, 35.0f );
glVertex2f(-10.0f, 0.0f );

glEnd();

     glBegin(GL_POLYGON); //// mountain4
     //glColor3f (1,0.9,0.1);
     glColor3f(0.5,0.5,0);

glVertex2f(-25.0f, 0.0f );
glVertex2f(0.0f, 40.0f );
glVertex2f(20.0f, 0.0f );

glEnd();

     glBegin(GL_LINES); //// mountain line0-------
glColor3f(0.0,0.0,0);
glVertex2f(-100.0f, 0.0f );
glVertex2f(-75.0f, 40.0f );
glEnd();
     glBegin(GL_LINES); //// mountain line1-------
glColor3f(0.0,0.0,0);
glVertex2f(-75.0f, 40.0f );
glVertex2f(-59.0f, 14.70f );
glEnd();
     glBegin(GL_LINES); //// mountain line2-------
glColor3f(0.0,0.0,0);
glVertex2f(-62.60f, 20.0f );
glVertex2f(-50.0f, 40.0f );
glEnd();
     glBegin(GL_LINES); //// mountain line3-------
glColor3f(0.0,0.0,0);
glVertex2f(-50.0f, 40.0f );
glVertex2f(-38.0f, 21.0f);
glEnd();
     glBegin(GL_LINES); //// mountain line4-------
glColor3f(0.0,0.0,0);
glVertex2f(-42.0f, 27.0f );
glVertex2f(-37.0f, 35.0f );
glEnd();
     glBegin(GL_LINES); //// mountain line5-------
glColor3f(0.0,0.0,0);
glVertex2f(-37.0f, 35.0f );
glVertex2f(-32.0f, 28.90f );
glEnd();
     glBegin(GL_LINES); //// mountain line6-------
glColor3f(0.0,0.0,0);
glVertex2f(-42.0f, 13.0f );
glVertex2f(-25.0f, 40.0f );
glEnd();
     glBegin(GL_LINES); //// mountain line7-------
glColor3f(0.0,0.0,0);
glVertex2f(-25.0f, 40.0f);
glVertex2f(-8.0f, 13.0f );
glEnd();
     glBegin(GL_LINES); //// mountain line8-------
glColor3f(0.0,0.0,0);
glVertex2f(-42.0f, 13.0f );
glVertex2f(-25.0f, 40.0f );
glEnd();
     glBegin(GL_LINES); //// mountain line9-------
glColor3f(0.0,0.0,0);
glVertex2f(-12.30f, 20.0f);
glVertex2f(0.0f, 40.0f );
glEnd();
     glBegin(GL_LINES); //// mountain line10-------
glColor3f(0.0,0.0,0);
glVertex2f(0.0f, 40.0f);
glVertex2f(20.0f, 0.0f );
glEnd();

}
void wheel(GLfloat rx, GLfloat ry, GLfloat cx, GLfloat cy)////////////////////wheel
{
glBegin(GL_TRIANGLE_FAN);
glColor3f(0.7,0.3,0);
glVertex2f(cx, cy);
for (int i = 0;i <= 100;i++)
{
float angle = 2.0f * 3.1416f * i / 100;
float x = rx * cosf(angle);
float y = ry * sinf(angle);
glVertex2f((x + cx), (y + cy));
}
glEnd();
}

void black(GLfloat rx, GLfloat ry, GLfloat cx, GLfloat cy)////////////////////black
{
glBegin(GL_TRIANGLE_FAN);
glColor3f(0.0f, 0.0f, 0.0f);
glVertex2f(cx, cy);
for (int i = 0;i <= 100;i++)
{
float angle = 2.0f * 3.1416f * i / 100;
float x = rx * cosf(angle);
float y = ry * sinf(angle);
glVertex2f((x + cx), (y + cy));
}
glEnd();
}
void border()////#############################################$$$$$$$$$$$ border
{
                glBegin(GL_POLYGON); //eit1
//glColor3f (0.5,0.6,0.5);
glColor3f (0.7,0.4,0);

glVertex2f(45.0f, 0.0f );
glVertex2f(50.0f, 0.0f );
glVertex2f(50.0f, -1.0f );
glVertex2f(45.0f, -1.0f );
glEnd();
                glBegin(GL_POLYGON); //eit2
//glColor3f (0.5,0.6,0.5);
glColor3f (0.7,0.4,0);

glVertex2f(45.0f, 0.0f );
glVertex2f(45.0f, -1.0f );
glVertex2f(35.0f, -15.0f );
glVertex2f(34.0f, -15.0f );
glEnd();
                glBegin(GL_POLYGON); //eit3
//glColor3f (0.5,0.6,0.5);
glColor3f (0.7,0.4,0);

glVertex2f(34.0f, -15.0f );
glVertex2f(35.0f, -15.0f );
glVertex2f(100.0f, -80.0f );
glVertex2f(100.0f, -83.0f );
glEnd();
                glBegin(GL_POLYGON); // wall 1
glColor3f (0.4,0.5,0.5);

glVertex2f(45.0f, -1.0f );
glVertex2f(50.0f, -1.0f );
glVertex2f(50.0f, -5.0f );
glVertex2f(45.0f, -5.0f );
glEnd();


                glBegin(GL_POLYGON); // wall 2
glColor3f (0.4,0.5,0.5);

glVertex2f(45.0f, -1.0f );
glVertex2f(45.0f, -5.0f );
glVertex2f(37.0f, -17.0f );
glVertex2f(35.0f, -15.0f );
glEnd();

                glBegin(GL_POLYGON); // wall 3
glColor3f (0.4,0.5,0.5);

glVertex2f(34.0f, -15.0f );
glVertex2f(100.0f, -83.0f );
glVertex2f(100.0f, -100.0f );
glVertex2f(34.0f, -25.0f );
glEnd();

               glBegin(GL_LINES); // wall line
glColor3f (0.7,0.4,0);

glVertex2f(45.0f, -1.0f );
glVertex2f(45.0f, -5.0f );
glEnd();
}
void truck()////############################################# Truck
{
            glBegin(GL_POLYGON); //track part1
//glColor3f (0.5,0.6,0.5);
glColor3f (0,0.3,0 );
int yadd=50;
glVertex2f(-50.0f, yadd+-50.0f );
glVertex2f(-50.0f, yadd+-52.0f );
glVertex2f(-73.0f, yadd+-52.0f );
glVertex2f(-73.0f, yadd+-50.0f );
glEnd();

        glBegin(GL_POLYGON); //track part2
glColor3f (0,0.3,0  );

glVertex2f(-50.0f, yadd+-50.0f );
glVertex2f(-50.0f, yadd+-45.0f );
glVertex2f(-52.0f, yadd+-40.0f );
glVertex2f(-56.0f, yadd+-40.0f );
glVertex2f(-56.0f, yadd+-50.0f );
glEnd();

        glBegin(GL_POLYGON); //track part3------
glColor3f (0.8,0.8,0.9);

glVertex2f(-50.0f, yadd+-49.0f );
glVertex2f(-50.0f, yadd+-45.0f );
glVertex2f(-52.0f, yadd+-40.0f );
glVertex2f(-54.0f, yadd+-40.0f );
glVertex2f(-54.0f, yadd+-49.0f );
glEnd();

        glBegin(GL_POLYGON); //track part3------4

     glColor3f (0,0.3,0  );

glVertex2f(-56.0f, yadd+-40.0f );
glVertex2f(-56.0f, yadd+-39.0f );
glVertex2f(-52.0f, yadd+-39.0f );
glVertex2f(-52.0f, yadd+-40.0f );

glEnd();

        glBegin(GL_POLYGON); //track part4
glColor3f (0,0.3,0  );

glVertex2f(-73.0f, yadd+-50.0f );
glVertex2f(-60.0f, yadd+-41.0f );
glVertex2f(-59.0f, yadd+-42.0f );
glVertex2f(-71.0f, yadd+-50.0f );
glEnd();


        glBegin(GL_POLYGON); //track part5
glColor3f (0,0.3,0  );

glVertex2f(-62.0f, yadd+-50.0f );
glVertex2f(-62.0f, yadd+-44.0f );
glVertex2f(-61.0f, yadd+-43.0f );
glVertex2f(-61.0f, yadd+-50.0f );
glEnd();
        glBegin(GL_POLYGON); //track part6
glColor3f (0,0.3,0  );

glVertex2f(-50.0f, yadd+-52.0f );
glVertex2f(-50.0f, yadd+-53.0f );
glVertex2f(-57.0f, yadd+-53.0f );
glVertex2f(-57.0f, yadd+-52.0f );
glEnd();

        glBegin(GL_POLYGON); //track part6
glColor3f (0,0.3,0  );

glVertex2f(-73.0f, yadd+-52.0f );
glVertex2f(-62.0f, yadd+-52.0f );
glVertex2f(-62.0f, yadd+-53.0f );
glVertex2f(-73.0f, yadd+-53.0f );
glEnd();

glBegin(GL_POLYGON);

glColor3f (0,0.3,0  );

glVertex2f(-75.0f, yadd+-45.0f );
//glVertex2f(-62.0f, -35.50f );
glVertex2f(-62.0f, yadd+-36.0f );
glVertex2f(-59.90f, yadd+-41.0f );
glVertex2f(-73.0f, yadd+-50.0f );

glEnd();

black(2.3,2.7,-53,yadd+-55);
black(2.3,2.7,-65,yadd+-55);
black(2.3,2.7,-70,yadd+-55);

wheel(1.3,1.7,-53,yadd+-55);
wheel(1.3,1.7,-65,yadd+-55);
wheel(1.3,1.7,-70,yadd+-55);
}
void truck1()////############################################# rocket truck1
{
       glPushMatrix();
    glTranslatef(20.0, 3.0, 0);
    glScalef(0.50, 0.50, 0.0);
    truck();
    glLoadIdentity();
glPopMatrix();
}
void truck2()////############################################# rocket truck2
{
       glPushMatrix();
    glTranslatef(-33.0, 3.0, 0);
    glScalef(0.50, 0.50, 0.0);
    truck();
    glLoadIdentity();
glPopMatrix();
}
void truck3()////############################################# rocket truck3
{
       glPushMatrix();
    glTranslatef(-6.0, 3.0, 0);
    glScalef(0.50, 0.50, 0.0);
    truck();
    glLoadIdentity();
glPopMatrix();
}
void struck()////############################################# sajua truck
{
            glBegin(GL_POLYGON); //track part1
//glColor3f (0.5,0.6,0.5);
int yadd=60;
glColor3f (0,0.3,0 );

glVertex2f(-50.0f, yadd+-50.0f );
glVertex2f(-50.0f, yadd+-52.0f );
glVertex2f(-73.0f, yadd+-52.0f );
glVertex2f(-73.0f, yadd+-50.0f );
glEnd();

        glBegin(GL_POLYGON); //track part2
glColor3f (0,0.3,0  );

glVertex2f(-50.0f, yadd+-50.0f );
glVertex2f(-50.0f, yadd+-45.0f );
glVertex2f(-52.0f, yadd+-40.0f );
glVertex2f(-56.0f, yadd+-40.0f );
glVertex2f(-56.0f, yadd+-50.0f );
glEnd();

        glBegin(GL_POLYGON); //track part3------
glColor3f (0.8,0.8,0.9);

glVertex2f(-50.0f, yadd+-49.0f );
glVertex2f(-50.0f, yadd+-45.0f );
glVertex2f(-52.0f, yadd+-40.0f );
glVertex2f(-54.0f, yadd+-40.0f );
glVertex2f(-54.0f, yadd+-49.0f );
glEnd();

        glBegin(GL_POLYGON); //track part3------4

     glColor3f (0,0.3,0  );

glVertex2f(-56.0f, yadd+-40.0f );
glVertex2f(-56.0f, yadd+-39.0f );
glVertex2f(-52.0f, yadd+-39.0f );
glVertex2f(-52.0f, yadd+-40.0f );

glEnd();


        glBegin(GL_POLYGON); //container
glColor3f (0.6,0.6,0.1);

glVertex2f(-73.0f, yadd+-50.0f );
glVertex2f(-73.0f, yadd+-38.0f );
glVertex2f(-57.0f, yadd+-38.0f );
glVertex2f(-57.0f, yadd+-50.0f );
glEnd();



        glBegin(GL_POLYGON); //track part6
glColor3f (0,0.3,0  );

glVertex2f(-50.0f, yadd+-52.0f );
glVertex2f(-50.0f, yadd+-53.0f );
glVertex2f(-57.0f, yadd+-53.0f );
glVertex2f(-57.0f, yadd+-52.0f );
glEnd();

        glBegin(GL_POLYGON); //track part6
glColor3f (0,0.3,0  );

glVertex2f(-73.0f, yadd+-52.0f );
glVertex2f(-62.0f, yadd+-52.0f );
glVertex2f(-62.0f, yadd+-53.0f );
glVertex2f(-73.0f, yadd+-53.0f );
glEnd();


black(2.3,2.7,-53,yadd+-55);
black(2.3,2.7,-65,yadd+-55);
black(2.3,2.7,-70,yadd+-55);

wheel(1.3,1.7,-53,yadd+-55);
wheel(1.3,1.7,-65,yadd+-55);
wheel(1.3,1.7,-70,yadd+-55);
}
void struck5()////################################################### struck5
{
      glPushMatrix();
    glTranslatef(-60.0, -2.0, 0);
    glScalef(0.50, 0.50, 0.0);
    struck();
    glLoadIdentity();
glPopMatrix();
}
void struck4()////################################################### struck4
{
      glPushMatrix();
    glTranslatef(-47.0, -2.0, 0);
    glScalef(0.50, 0.50, 0.0);
    struck();
    glLoadIdentity();
glPopMatrix();
}
void struck3()////################################################### struck3
{
      glPushMatrix();
    glTranslatef(-20.0, -2.0, 0);
    glScalef(0.50, 0.50, 0.0);
    struck();
    glLoadIdentity();
glPopMatrix();
}
void struck2()////################################################### struck2
{
      glPushMatrix();
    glTranslatef(-7.0, -2.0, 0);
    glScalef(0.50, 0.50, 0.0);
    struck();
    glLoadIdentity();
glPopMatrix();
}
void struck1()////################################################### struck1
{
      glPushMatrix();
    glTranslatef(6.0, -2.0, 0);
    glScalef(0.50, 0.50, 0.0);
    struck();
    glLoadIdentity();
glPopMatrix();
}
void tank()///////#######################################################tank1---------------
{

black(2, 3, -87.0,-21);
black(2, 3, -82.5,-21);
black(2, 3, -77.5,-21);
black(2, 3, -73,-21);

wheel(0.80, 1.0, -87.0,-21);
wheel(0.8, 1, -82.5,-21);
wheel(0.8, 1, -77.5,-21);
wheel(0.8, 1, -73,-21);

    glBegin(GL_POLYGON); //Body1
//square
//glColor3f (0.6,0.6,0.5 );
//glColor3f(0.1,0.4,0);
//glColor3f(0.1,0.2,0);
glColor3f(0.1,0.3,0.1);//**

glVertex2f(-88.0f, -15.0f );
glVertex2f(-72.0f, -15.0f );
glVertex2f(-70.0f, -19.0f );
glVertex2f(-90.0f, -19.0f );

glEnd();

    glBegin(GL_POLYGON); //body2
//square
//glColor3f (0.6,0.6,0.5);
//glColor3f(0.1,0.4,0);
glColor3f(0.1,0.3,0.1);

glVertex2f(-87.0f, -15.0f );
glVertex2f(-87.0f, -13.0f );
glVertex2f(-76.0f, -13.0f );
glVertex2f(-76.0f, -19.0f );

glEnd();
    glBegin(GL_POLYGON); //body3
//square
//glColor3f (0.6,0.6,0.7);
//glColor3f(0.1,0.3,0.1 );
glColor3f(0.1,0.2,0);

glVertex2f(-86.0f, -13.0f );
glVertex2f(-86.0f, -12.0f );
glVertex2f(-77.0f, -12.0f );
glVertex2f(-77.0f, -13.0f );

glEnd();

    glBegin(GL_POLYGON); //body4
//square
//glColor3f (0.6,0.6,0.7);
glColor3f(0.1,0.3,0.2);

glVertex2f(-86.0f, -12.0f );
glVertex2f(-85.0f, -9.0f );
glVertex2f(-78.0f, -9.0f );
glVertex2f(-77.0f, -12.0f );
glEnd();

    glBegin(GL_POLYGON); //body5
//square
//glColor3f (0.5,0.6,0.5);
glColor3f(0.1,0.2,0);

glVertex2f(-84.0f, -9.0f );
glVertex2f(-84.0f, -7.0f );
glVertex2f(-79.0f, -7.0f );
glVertex2f(-79.0f, -9.0f );
glEnd();

    glBegin(GL_POLYGON); //danda1
//square
glColor3f (0.7,0.4,0.2);


glVertex2f(-78.0f, -9.0f );
glVertex2f(-75.20f, -9.0f );
glVertex2f(-75.0f, -12.0f );
glVertex2f(-77.0f, -12.0f );
glEnd();

    glBegin(GL_POLYGON); //danda2
//square
//glColor3f (0.6,0.6,0.5);
glColor3f(0.1,0.3,0.1);


glVertex2f(-75.0f, -9.50f );
glVertex2f(-67.0f, -9.50f );
glVertex2f(-67.0f, -11.50f );
glVertex2f(-75.0f, -11.50f );
glEnd();
    glBegin(GL_POLYGON); //danda3
//square
glColor3f (0.7,0.4,0.2);


glVertex2f(-67.0f, -9.0f );
glVertex2f(-65.0f, -9.0f );
glVertex2f(-65.0f, -12.0f );
glVertex2f(-67.0f, -12.0f );
glEnd();


    glBegin(GL_POLYGON); //wheel part1
//square
glColor3f (0.0, 0.0, 0.0);


glVertex2f(-88.0f, -25.0f );
glVertex2f(-88.0f, -24.0f );
glVertex2f(-73.0f, -24.0f );
glVertex2f(-73.0f, -25.0f );
glEnd();

    glBegin(GL_POLYGON); //wheel part2
glColor3f (0.0, 0.0, 0.0);


glVertex2f(-90.0f, -19.0f );
glVertex2f(-89.0f, -19.0f );
glVertex2f(-87.0f, -25.0f );
glVertex2f(-88.0f, -25.0f );
glEnd();


    glBegin(GL_POLYGON); //wheel part3
glColor3f (0.0, 0.0, 0.0);

glVertex2f(-71.0f, -19.0f );
glVertex2f(-70.0f, -19.0f );
glVertex2f(-72.0f, -25.0f );
glVertex2f(-73.0f, -25.0f );
glEnd();

}

void tank2()////##################################################################tank2
{
   glPushMatrix();
    glTranslatef(-0.3, 3.0, 0);
    glScalef(0.70, 0.70, 0.0);
    tank();
    glLoadIdentity();
glPopMatrix();
}

void tank3()////##################################################################tank3
{
   glPushMatrix();
    glTranslatef(8.0, 5.0, 0);
    glScalef(.6, .6, 0.0);
    tank();
    glLoadIdentity();
glPopMatrix();
}

void rocketlauncher()////////////################################################ Rocket launcher
{
        glBegin(GL_POLYGON); //track part1
//glColor3f (0.5,0.6,0.5);
glColor3f (0,0.3,0 );

glVertex2f(-50.0f, -50.0f );
glVertex2f(-50.0f, -52.0f );
glVertex2f(-73.0f, -52.0f );
glVertex2f(-73.0f, -50.0f );
glEnd();

        glBegin(GL_POLYGON); //track part2
glColor3f (0,0.3,0  );

glVertex2f(-50.0f, -50.0f );
glVertex2f(-50.0f, -45.0f );
glVertex2f(-52.0f, -40.0f );
glVertex2f(-56.0f, -40.0f );
glVertex2f(-56.0f, -50.0f );
glEnd();

        glBegin(GL_POLYGON); //track part3------
glColor3f (0.8,0.8,0.9);

glVertex2f(-50.0f, -49.0f );
glVertex2f(-50.0f, -45.0f );
glVertex2f(-52.0f, -40.0f );
glVertex2f(-54.0f, -40.0f );
glVertex2f(-54.0f, -49.0f );
glEnd();

        glBegin(GL_POLYGON); //track part3------4

     glColor3f (0,0.3,0  );

glVertex2f(-56.0f, -40.0f );
glVertex2f(-56.0f, -39.0f );
glVertex2f(-52.0f, -39.0f );
glVertex2f(-52.0f, -40.0f );

glEnd();

        glBegin(GL_POLYGON); //track part4
glColor3f (0,0.3,0  );

glVertex2f(-73.0f, -50.0f );
glVertex2f(-60.0f, -41.0f );
glVertex2f(-59.0f, -42.0f );
glVertex2f(-71.0f, -50.0f );
glEnd();


        glBegin(GL_POLYGON); //track part5
glColor3f (0,0.3,0  );

glVertex2f(-62.0f, -50.0f );
glVertex2f(-62.0f, -44.0f );
glVertex2f(-61.0f, -43.0f );
glVertex2f(-61.0f, -50.0f );
glEnd();
        glBegin(GL_POLYGON); //track part6
glColor3f (0,0.3,0  );

glVertex2f(-50.0f, -52.0f );
glVertex2f(-50.0f, -53.0f );
glVertex2f(-57.0f, -53.0f );
glVertex2f(-57.0f, -52.0f );
glEnd();

        glBegin(GL_POLYGON); //track part6
glColor3f (0,0.3,0  );

glVertex2f(-73.0f, -52.0f );
glVertex2f(-62.0f, -52.0f );
glVertex2f(-62.0f, -53.0f );
glVertex2f(-73.0f, -53.0f );
glEnd();
////////extra

////////end of extra

black(2.3,2.7,-53,-55);
black(2.3,2.7,-65,-55);
black(2.3,2.7,-70,-55);

wheel(1.3,1.7,-53,-55);
wheel(1.3,1.7,-65,-55);
wheel(1.3,1.7,-70,-55);

}
void Trocketlauncher()////////////################################################ Rocket launcher Tranfer
{
        glBegin(GL_POLYGON); //track part1
//glColor3f (0.5,0.6,0.5);
glColor3f (0,0.3,0 );

glVertex2f(-50.0f, -50.0f );
glVertex2f(-50.0f, -52.0f );
glVertex2f(-73.0f, -52.0f );
glVertex2f(-73.0f, -50.0f );
glEnd();

        glBegin(GL_POLYGON); //track part2
glColor3f (0,0.3,0  );

glVertex2f(-50.0f, -50.0f );
glVertex2f(-50.0f, -45.0f );
glVertex2f(-52.0f, -40.0f );
glVertex2f(-56.0f, -40.0f );
glVertex2f(-56.0f, -50.0f );
glEnd();

        glBegin(GL_POLYGON); //track part3------
glColor3f (0.8,0.8,0.9);

glVertex2f(-50.0f, -49.0f );
glVertex2f(-50.0f, -45.0f );
glVertex2f(-52.0f, -40.0f );
glVertex2f(-54.0f, -40.0f );
glVertex2f(-54.0f, -49.0f );
glEnd();

        glBegin(GL_POLYGON); //track part3------4

     glColor3f (0,0.3,0  );

glVertex2f(-56.0f, -40.0f );
glVertex2f(-56.0f, -39.0f );
glVertex2f(-52.0f, -39.0f );
glVertex2f(-52.0f, -40.0f );

glEnd();

        glBegin(GL_POLYGON); //track part4
glColor3f (0,0.3,0  );

glVertex2f(-73.0f, -50.0f );
glVertex2f(-60.0f, -41.0f );
glVertex2f(-59.0f, -42.0f );
glVertex2f(-71.0f, -50.0f );
glEnd();


        glBegin(GL_POLYGON); //track part5
glColor3f (0,0.3,0  );

glVertex2f(-62.0f, -50.0f );
glVertex2f(-62.0f, -44.0f );
glVertex2f(-61.0f, -43.0f );
glVertex2f(-61.0f, -50.0f );
glEnd();
        glBegin(GL_POLYGON); //track part6
glColor3f (0,0.3,0  );

glVertex2f(-50.0f, -52.0f );
glVertex2f(-50.0f, -53.0f );
glVertex2f(-57.0f, -53.0f );
glVertex2f(-57.0f, -52.0f );
glEnd();

        glBegin(GL_POLYGON); //track part6
glColor3f (0,0.3,0  );

glVertex2f(-73.0f, -52.0f );
glVertex2f(-62.0f, -52.0f );
glVertex2f(-62.0f, -53.0f );
glVertex2f(-73.0f, -53.0f );
glEnd();
////////extra

////////end of extra

black(2.3,2.7,-53,-55);
black(2.3,2.7,-65,-55);
black(2.3,2.7,-70,-55);

wheel(1.3,1.7,-53,-55);
wheel(1.3,1.7,-65,-55);
wheel(1.3,1.7,-70,-55);


/////////////////rocket
glBegin(GL_POLYGON);////body
//glColor3f (0.4,0.4,0.2 );
glColor3f (0.4,0.5,0.3 );

glVertex2f(px-75.0f, py-45.0f );
glVertex2f(px-63.0f, py-37.0f );
glVertex2f(px-60.50f, py-41.0f );/////
glVertex2f(px-73.0f, py-50.0f );

glEnd();



glBegin(GL_POLYGON);////////////head
//glColor3f (0.6,0,0.1 );
glColor3f (0.5,0.1,0);

glVertex2f(px-63.0f, py-37.0f );
glVertex2f(px-58.0f, py-36.0f );
glVertex2f(px-61.40f, py-42.0f );

glEnd();

///////////////////fire
glBegin(GL_POLYGON);////middle part
//glColor3f (0.6,0.7,0.2 );
glColor3f (1.0,1.0,0 );

glVertex2f(px+f-75.0f, py-45.0f );
glVertex2f(px+f-87.0f, py-55.0f );
glVertex2f(px+f-73.0f, py-50.0f );
glEnd();
glBegin(GL_POLYGON);////upper part

glColor3f (1.0,1.0,0 );

glVertex2f(px+f-75.0f, py-45.0f );
glVertex2f(px+f-85.0f, py-45.0f );
glVertex2f(px+f-80.0f, py-49.30f );
glEnd();
glBegin(GL_POLYGON);////lower part
glColor3f (1.0,1.0,0 );

glVertex2f(px+f-79.0f, py-51.0f );
glVertex2f(px+f-80.0f, py-59.0f );
glVertex2f(px+f-73.0f, py-50.0f );
glEnd();

}


void rocketlauncher2()//////////######################### rocket launcher 2
{
          glPushMatrix();
    glTranslatef(17.0, 10.0, 0);
    glScalef(0.80, 0.80, 0.0);
    Trocketlauncher();
    glLoadIdentity();
glPopMatrix();
}

void rocket()//////////////$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$ Rocket
{
glBegin(GL_POLYGON);////body
//glColor3f (0.6,0.7,0.2 );
glColor3f (0.2,0.4,0 );

glVertex2f(-75.0f, -45.0f );
glVertex2f(-63.0f, -37.0f );
glVertex2f(-60.50f, -41.0f );/////
glVertex2f(-73.0f, -50.0f );

glEnd();



glBegin(GL_POLYGON);////////////head
//glColor3f (1.0, 0.0, 0.0);
glColor3f (0.40, 0.0, 0.0);

glVertex2f(-63.0f, -37.0f );
glVertex2f(-58.0f, -36.0f );
glVertex2f(-61.40f, -42.0f );

glEnd();

//////////////////////////////////// fire

glBegin(GL_POLYGON);////middle part
//glColor3f (0.6,0.7,0.2 );
glColor3f (1.0,1.0,0 );

glVertex2f(f-75.0f, -45.0f );
glVertex2f(f-87.0f, -55.0f );
glVertex2f(f-73.0f, -50.0f );
glEnd();
glBegin(GL_POLYGON);////upper part

glColor3f (1.0,1.0,0 );

glVertex2f(f-75.0f, -45.0f );
glVertex2f(f-85.0f, -45.0f );
glVertex2f(f-80.0f, -49.30f );
glEnd();
glBegin(GL_POLYGON);////lower part
glColor3f (1.0,1.0,0 );

glVertex2f(f-79.0f, -51.0f );
glVertex2f(f-80.0f, -59.0f );
glVertex2f(f-73.0f, -50.0f );
glEnd();

if (f > 0)flag = !flag;
if (f <= -2) flag = !flag;
if (flag)f += 0.1;
else f -= 0.1;


}

void jet()//////////////////////////////////////////////////// jet palne
{
    glBegin(GL_POLYGON);/////body1
glColor3f (0.3,0.4,0.3);

glVertex2f(-70.0f, 45.0f );
glVertex2f(-50.0f, 45.0f );
glVertex2f(-50.0f, 40.0f );
glVertex2f(-70.0f, 40.0f );
glEnd();
    glBegin(GL_POLYGON);/////body2
glColor3f (0.3,0.4,0.3);

glVertex2f(-50.0f, 45.0f );
glVertex2f(-46.0f, 45.0f );
glVertex2f(-44.0f, 44.0f );
glVertex2f(-44.0f, 41.0f );
glVertex2f(-46.0f, 40.0f );
glVertex2f(-50.0f, 40.0f );
glEnd();

    glBegin(GL_POLYGON);/////body3
glColor3f (0.3,0.4,0.3);

glVertex2f(-44.0f, 44.0f );
glVertex2f(-40.0f, 44.0f );
glVertex2f(-38.0f, 42.50f );
glVertex2f(-40.0f, 41.0f );
glVertex2f(-44.0f, 41.0f );
glEnd();

    glBegin(GL_POLYGON);/////body4
glColor3f (0.3,0.4,0.3);

glVertex2f(-70.0f, 45.0f );
glVertex2f(-70.0f, 40.0f );
glVertex2f(-75.0f, 40.0f );
glVertex2f(-75.0f, 45.0f );

glEnd();

    glBegin(GL_POLYGON);/////body5
glColor3f (0.3,0.4,0.3);

glVertex2f(-75.0f, 44.0f );
glVertex2f(-75.0f, 41.0f );
glVertex2f(-78.0f, 41.0f );
glVertex2f(-78.0f, 44.0f );

glEnd();

    glBegin(GL_POLYGON);//////////////wings1
glColor3f (0.3,0.3,0.7);

glVertex2f(-65.0f, 45.0f );
glVertex2f(-65.0f, 55.0f );
glVertex2f(-60.0f, 55.0f );
glVertex2f(-50.0f, 45.0f );
glVertex2f(-65.0f, 45.0f );
glEnd();


    glBegin(GL_POLYGON);//////////////wings2
glColor3f (0.3,0.3,0.7);

glVertex2f(-50.0f, 41.0f );
glVertex2f(-50.0f, 40.0f );
glVertex2f(-60.0f, 30.0f );
glVertex2f(-65.0f, 30.0f );
glVertex2f(-65.0f, 41.0f );
glEnd();

    glBegin(GL_POLYGON);//////////////lenga1
glColor3f (0.3,0.3,0.7);

glVertex2f(-75.0f, 45.0f );
glVertex2f(-75.0f, 50.0f );
glVertex2f(-72.0f, 50.0f );
glVertex2f(-70.0f, 45.0f );
//glVertex2f(-65.0f, 41.0f );
glEnd();

    glBegin(GL_POLYGON);//////////////lenga2
glColor3f (0.3,0.3,0.7);

glVertex2f(-70.0f, 41.0f );
glVertex2f(-70.0f, 40.0f );
glVertex2f(-72.0f, 35.0f );
glVertex2f(-75.0f, 35.0f );
glVertex2f(-75.0f, 41.0f );
glEnd();

    glBegin(GL_POLYGON);//////////////bomb1
glColor3f (0.0,0.0,0.0);

glVertex2f(-66.0f, 56.0f );
glVertex2f(-58.0f, 56.0f );
glVertex2f(-57.0f, 55.50f );
glVertex2f(-58.0f, 55.0f );
glVertex2f(-66.0f, 55.0f );
glEnd();

    glBegin(GL_POLYGON);//////////////bomb2
glColor3f (0.0,0.0,0.0);

glVertex2f(-66.0f, 30.0f );
glVertex2f(-58.0f, 30.0f );
glVertex2f(-57.0f, 29.50f );
glVertex2f(-58.0f, 29.0f );
glVertex2f(-66.0f, 29.0f );
glEnd();

if(j<=200)
{
    j=j+.01;
}
else{
    j=-100;
}

}

void jet1()/////////////////////////////////######################### jet1
{
          glPushMatrix();
    glTranslatef(j-50.0, 50.0, 0);
    glScalef(0.40, 0.40, 0.0);
    jet();
    glLoadIdentity();
glPopMatrix();
}

void jet2()/////////////////////////////////######################### jet2
{
          glPushMatrix();
    glTranslatef(j-40.0, 35.0, 0);
    glScalef(0.40, 0.40, 0.0);
    jet();
    glLoadIdentity();
glPopMatrix();
}

void jet3()/////////////////////////////////######################### jet3
{
          glPushMatrix();
    glTranslatef(j-50.0, 20.0, 0);
    glScalef(0.40, 0.40, 0.0);
    jet();
    glLoadIdentity();
glPopMatrix();
}
void building()////////////################################################### building
{

                                    glBegin(GL_POLYGON);//////////////flag middle white
glColor3f (1.0,1.0,1);

glVertex2f(80.0f, 70.0f );
glVertex2f(94.0f, 70.0f );
glVertex2f(94.0f, 64.0f );
glVertex2f(80.0f, 64.0f );
glEnd();

   glBegin(GL_LINES);//////////////flag star
glColor3f (0.4,0.3,1);

glVertex2f(85.0f, 66.0f );
glVertex2f(87.0f, 69.0f );
glEnd();
   glBegin(GL_LINES);//////////////flag star
glColor3f (0.4,0.3,1);

glVertex2f(89.0f, 66.0f );
glVertex2f(87.0f, 69.0f );
glEnd();

   glBegin(GL_LINES);//////////////flag star
glColor3f (0.4,0.3,1);

glVertex2f(89.0f, 66.0f );
glVertex2f(85.0f, 66.0f );
glEnd();
   glBegin(GL_LINES);//////////////flag star
glColor3f (0.4,0.3,1);

glVertex2f(85.0f, 68.0f );
glVertex2f(87.0f, 65.0f );
glEnd();
   glBegin(GL_LINES);//////////////flag star
glColor3f (0.4,0.3,1);

glVertex2f(89.0f, 68.0f );
glVertex2f(85.0f, 68.0f );
glEnd();
   glBegin(GL_LINES);//////////////flag star
glColor3f (0.4,0.3,1);

glVertex2f(89.0f, 68.0f );
glVertex2f(87.0f, 65.0f);
glEnd();
                                glBegin(GL_POLYGON);//////////////flag upper blue
glColor3f (0.4,0.3,1);

glVertex2f(80.0f, 72.0f );
glVertex2f(94.0f, 72.0f );
glVertex2f(94.0f, 70.0f );
glVertex2f(80.0f, 70.0f );
glEnd();
                            glBegin(GL_POLYGON);//////////////flag lower blue
glColor3f (0.4,0.3,1);

glVertex2f(80.0f, 64.0f );
glVertex2f(94.0f, 64.0f );
glVertex2f(94.0f, 62.0f );
glVertex2f(80.0f, 62.0f );
glEnd();
                        glBegin(GL_POLYGON);//////////////flag danda
glColor3f (0.3,0.30,0.30);

glVertex2f(79.0f, 72.0f );
glVertex2f(80.0f, 72.0f );
glVertex2f(80.0f, 60.0f );
glVertex2f(79.0f, 60.0f );
glEnd();

                    glBegin(GL_POLYGON);//////////////building 4.1
glColor3f (0.6,0.4,0.4);

glVertex2f(75.0f, 60.0f );
glVertex2f(85.0f, 60.0f );
glVertex2f(85.0f, 50.0f );
glVertex2f(75.0f, 50.0f );
glEnd();
                glBegin(GL_POLYGON);//////////////building 4.0
glColor3f (0.6,0.4,0.4);

glVertex2f(70.0f, 50.0f );
glVertex2f(90.0f, 50.0f );
glVertex2f(90.0f, 0.0f );
glVertex2f(70.0f, 0.0f );
glEnd();

            glBegin(GL_POLYGON);//////////////building 3
glColor3f (0.5,0.2,0.7);

glVertex2f(60.0f, 0.0f );
glVertex2f(60.0f, 30.0f );
glVertex2f(80.0f, 30.0f );
glVertex2f(80.0f, 0.0f );
glEnd();

            glBegin(GL_POLYGON);//////////////building 2
glColor3f (0.6,0.7,0.7);

glVertex2f(55.0f, 20.0f );
glVertex2f(70.0f, 20.0f );
glVertex2f(70.0f, -8.0f );
glVertex2f(55.0f, -8.0f );
glEnd();
            glBegin(GL_POLYGON);//////////////building 1.3
glColor3f (0.5,0.4,0.1 );

glVertex2f(85.0f, 25.0f );
glVertex2f(100.0f, 25.0f );
glVertex2f(100.0f, -8.0f );
glVertex2f(85.0f, -8.0f );
glEnd();

            glBegin(GL_POLYGON);//////////////building 1.2
glColor3f (0.4,0.5,0.3);

glVertex2f(78.0f, 20.0f );//////75
glVertex2f(90.0f, 20.0f );
glVertex2f(90.0f, -8.0f );
glVertex2f(78.0f, -8.0f );/////75
glEnd();
            glBegin(GL_POLYGON);//////////////building 1.1
glColor3f (0.8,0.6,0);

glVertex2f(65.0f, 10.0f );
glVertex2f(75.0f, 10.0f );
glVertex2f(75.0f, -8.0f );
glVertex2f(65.0f, -8.0f );
glEnd();
        glBegin(GL_POLYGON);//////////////building 1
glColor3f (0.8,0.6,0);

glVertex2f(50.0f, 10.0f );
glVertex2f(60.0f, 10.0f );
glVertex2f(60.0f, -8.0f );
glVertex2f(50.0f, -8.0f );
glEnd();


}

void antimissilesystem()///////########################################## antimissilesystem
{
          glBegin(GL_POLYGON);////////////// floor 1
glColor3f (0.5,0.3,0.2 );

glVertex2f(55.0f, -30.0f );
glVertex2f(95.0f, -30.0f );
glVertex2f(95.0f, -33.0f );
glVertex2f(55.0f, -33.0f );
glEnd();

          glBegin(GL_POLYGON);////////////// floor 2
glColor3f (0.5,0.4,0.3 );

glVertex2f(57.0f, -28.0f );
glVertex2f(92.0f, -28.0f );
glVertex2f(95.0f, -30.0f );
glVertex2f(55.0f, -30.0f );
glEnd();

          glBegin(GL_POLYGON);////////////// antimissile body1
glColor3f (0.4,0.4,0.2  );

glVertex2f(57.0f, -15.0f );
glVertex2f(63.0f, -15.0f );
glVertex2f(63.0f, -30.0f );
glVertex2f(57.0f, -30.0f );
glEnd();
          glBegin(GL_POLYGON);////////////// antimissile body2
glColor3f (0.4,0.4,0.2  );

glVertex2f(65.0f, -15.0f );
glVertex2f(71.0f, -15.0f );
glVertex2f(71.0f, -30.0f );
glVertex2f(65.0f, -30.0f );
glEnd();

          glBegin(GL_POLYGON);////////////// antimissile head1
glColor3f (0.90,0.0,0.0 );

glVertex2f(57.0f, -15.0f );
glVertex2f(58.0f, -13.0f );
glVertex2f(62.0f, -13.0f );
glVertex2f(63.0f, -15.0f );
glEnd();
          glBegin(GL_POLYGON);////////////// antimissile head2
glColor3f (0.90,0.0,0.0 );

glVertex2f(65.0f, -15.0f );
glVertex2f(66.0f, -13.0f );
glVertex2f(70.0f, -13.0f );
glVertex2f(71.0f, -15.0f );
glEnd();

          glBegin(GL_POLYGON);////////////// antimissile rocket body
glColor3f (0.4,0.4,0.4 );

glVertex2f(80.0f, anti-15.0f );
glVertex2f(85.0f, anti-15.0f );
glVertex2f(85.0f, anti-30.0f );
glVertex2f(80.0f, anti-30.0f );
glEnd();

          glBegin(GL_POLYGON);////////////// antimissile rocket head
glColor3f (0.70,0.0,0.0);

glVertex2f(80.0f, anti+-15.0f );
glVertex2f(82.50f, anti+-10.0f );
glVertex2f(85.0f, anti+-15.0f );
glEnd();

          glBegin(GL_POLYGON);////////////// antimissile rocket wings1
glColor3f (0.70,0.0,0.0);

glVertex2f(75.0f, anti+-28.0f );
glVertex2f(80.0f, anti+-20.0f );
glVertex2f(80.0f, anti+-28.0f );
glEnd();
          glBegin(GL_POLYGON);////////////// antimissile rocket wings2
glColor3f (0.70,0.0,0.0);

glVertex2f(85.0f, anti+-28.0f );
glVertex2f(85.0f, anti+-20.0f );
glVertex2f(90.0f, anti+-28.0f );
glEnd();
          glBegin(GL_POLYGON);////////////// antimissile rocket bottom
glColor3f (0.70,0.0,0.0);

glVertex2f(80.0f, anti+-28.0f );
glVertex2f(85.0f, anti+-28.0f );
glVertex2f(85.0f, anti+-30.0f );
glVertex2f(80.0f, anti+-30.0f );

glEnd();
/////////////////////fire1
glBegin(GL_POLYGON);
glColor3f (1.0,1.0,0.0);

glVertex2f(80.0f, anti+f-30.0f );
glVertex2f(85.0f, anti+f-30.0f );
glVertex2f(82.50f, anti+f-40.0f );
glEnd();
/////////////////////fire2
glBegin(GL_POLYGON);
glColor3f (1.0,1.0,0.0);

glVertex2f(80.0f, anti+f-30.0f );
glVertex2f(85.0f, anti+f-30.0f );
glVertex2f(77.0f, anti+f-37.0f );
glEnd();
/////////////////////fire3
glBegin(GL_POLYGON);
glColor3f (1.0,1.0,0.0);

glVertex2f(80.0f, anti+f-30.0f );
glVertex2f(85.0f, anti+f-30.0f );
glVertex2f(87.00f, anti+f-37.0f );
glEnd();

if(anti<=200)
{
    anti=anti+.05;//.2
    //printf("   %f\n",anti);
    k=k+1;

}
else{
    anti=0;
    k=0;
}
}
void window()/////////////////////////////////////################### window
{
glBegin(GL_POLYGON);
glColor3f (0.0,0.2,0.2);

glVertex2f(51.0f, 8.0f );
glVertex2f(54.0f, 8.0f );
glVertex2f(54.0f, 5.0f );
glVertex2f(51.0f, 5.0f );
glEnd();
}
void windows()/////////////////////////////////////###################*********** windows
{
 glPushMatrix();//////////////////////////////////
    glTranslatef(0.0, .00, 0);
   // glScalef(.5, .5, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();

 glPushMatrix();//////////////////////////////////
    glTranslatef(4.80, .00, 0);
    glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
 glPushMatrix();//////////////////////////////////
    glTranslatef(0.0, -5.00, 0);
   // glScalef(.5, .5, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();

 glPushMatrix();//////////////////////////////////
    glTranslatef(4.80, -5.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();

 glPushMatrix();//////////////////////////////////
    glTranslatef(0.0, -10.00, 0);
   // glScalef(.5, .5, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();

 glPushMatrix();//////////////////////////////////
    glTranslatef(4.80, -10.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();

    //////////////////// for senond house
glPushMatrix();//////////////////////////////////
    glTranslatef(5.0, 10.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
glPushMatrix();//////////////////////////////////
    glTranslatef(10.0, 10.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
    glPushMatrix();//////////////////////////////////
    glTranslatef(15.0, 10.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
glPushMatrix();//////////////////////////////////
    glTranslatef(5.0, 5.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
glPushMatrix();//////////////////////////////////
    glTranslatef(10.0, 5.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
    glPushMatrix();//////////////////////////////////
    glTranslatef(15.0, 5.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
    glPushMatrix();//////////////////////////////////
    glTranslatef(10.0, 0.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
        glPushMatrix();//////////////////////////////////
    glTranslatef(10.0, -5.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
            glPushMatrix();//////////////////////////////////
    glTranslatef(10.0, -10.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
    ///////////////////////////// for second building
                glPushMatrix();//////////////////////////////////
    glTranslatef(15.0, 0.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                    glPushMatrix();//////////////////////////////////
    glTranslatef(20.0, 0.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
    ////
                    glPushMatrix();//////////////////////////////////
    glTranslatef(15.0, -5.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                    glPushMatrix();//////////////////////////////////
    glTranslatef(20.0, -5.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
    ////
                    glPushMatrix();//////////////////////////////////
    glTranslatef(15.0, -10.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                    glPushMatrix();//////////////////////////////////
    glTranslatef(20.0, -10.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();

    ///////////////////////// for building 3
                        glPushMatrix();//////////////////////////////////
    glTranslatef(10.0, 20.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                        glPushMatrix();//////////////////////////////////
    glTranslatef(15.0, 20.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                            glPushMatrix();//////////////////////////////////
    glTranslatef(20.0, 20.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                glPushMatrix();//////////////////////////////////
    glTranslatef(25.0, 20.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
    /////************
                            glPushMatrix();//////////////////////////////////
    glTranslatef(10.0, 15.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                        glPushMatrix();//////////////////////////////////
    glTranslatef(15.0, 15.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                            glPushMatrix();//////////////////////////////////
    glTranslatef(20.0, 15.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                glPushMatrix();//////////////////////////////////
    glTranslatef(25.0, 15.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
/////************
                            glPushMatrix();//////////////////////////////////
    glTranslatef(10.0, 10.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                        glPushMatrix();//////////////////////////////////
    glTranslatef(15.0, 10.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                            glPushMatrix();//////////////////////////////////
    glTranslatef(20.0, 10.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                glPushMatrix();//////////////////////////////////
    glTranslatef(20.0, 5.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();

    glBegin(GL_POLYGON);
glColor3f (0.0,0.2,0.2);

glVertex2f(76.0f, 18.0f );
glVertex2f(78.0f, 18.0f );
glVertex2f(78.0f, 15.0f );
glVertex2f(76.0f, 15.0f );
glEnd();

    glBegin(GL_POLYGON);
glColor3f (0.0,0.2,0.2);

glVertex2f(76.0f, 13.0f );
glVertex2f(78.0f, 13.0f );
glVertex2f(78.0f, 10.0f );
glVertex2f(76.0f, 10.0f );
glEnd();

    glBegin(GL_POLYGON);
glColor3f (0.0,0.2,0.2);

glVertex2f(76.0f, 8.0f );
glVertex2f(78.0f, 8.0f );
glVertex2f(78.0f, 5.0f );
glVertex2f(76.0f, 5.0f );
glEnd();
/////////////for building 5
                                glPushMatrix();//////////////////////////////////
    glTranslatef(29.0, 10.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                    glPushMatrix();//////////////////////////////////
    glTranslatef(35.0, 10.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                    glPushMatrix();//////////////////////////////////
    glTranslatef(29.0, 5.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                    glPushMatrix();//////////////////////////////////
    glTranslatef(35.0, 5.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                        glPushMatrix();//////////////////////////////////
    glTranslatef(29.0, 0.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                    glPushMatrix();//////////////////////////////////
    glTranslatef(35.0, 0.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                            glPushMatrix();//////////////////////////////////
    glTranslatef(29.0, -5.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                    glPushMatrix();//////////////////////////////////
    glTranslatef(35.0, -5.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                            glPushMatrix();//////////////////////////////////
    glTranslatef(29.0, -10.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                    glPushMatrix();//////////////////////////////////
    glTranslatef(35.0, -10.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
 /////// for building 6
                                     glPushMatrix();//////////////////////////////////
    glTranslatef(35.0, 15.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                     glPushMatrix();//////////////////////////////////
    glTranslatef(40.0, 15.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(45.0, 15.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(40.0, 10.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(45.0, 10.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(40.0, 5.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(45.0, 5.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(40.0, 0.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(45.0, 0.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(40.0, -5.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(45.0, -5.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(40.0, -10.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(45.0, -10.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();

    /////for the big building
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(20.0, 40.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(25.0, 40.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                             glPushMatrix();//////////////////////////////////
    glTranslatef(30.0, 40.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(35.0, 40.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
    ////////////////111111111111
                                          glPushMatrix();//////////////////////////////////
    glTranslatef(20.0, 35.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(25.0, 35.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                             glPushMatrix();//////////////////////////////////
    glTranslatef(30.0, 35.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(35.0, 35.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
        ////////////////22222222222
                                          glPushMatrix();//////////////////////////////////
    glTranslatef(20.0, 30.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(25.0, 30.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                             glPushMatrix();//////////////////////////////////
    glTranslatef(30.0, 30.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(35.0, 30.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
        ////////////////3333333333333333
                                          glPushMatrix();//////////////////////////////////
    glTranslatef(20.0, 25.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(25.0, 25.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                             glPushMatrix();//////////////////////////////////
    glTranslatef(30.0, 25.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
                                         glPushMatrix();//////////////////////////////////
    glTranslatef(35.0, 25.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
    glPushMatrix();//////////////////////////////////
        glTranslatef(30.0, 20.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();

        glPushMatrix();//////////////////////////////////
        glTranslatef(35.0, 20.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
        glPushMatrix();//////////////////////////////////
        glTranslatef(30.0, 15.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
    /////////////////////top
        glPushMatrix();//////////////////////////////////
        glTranslatef(25.0, 50.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
        glPushMatrix();//////////////////////////////////
        glTranslatef(30.0, 50.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();

            glPushMatrix();//////////////////////////////////
        glTranslatef(25.0, 45.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
        glPushMatrix();//////////////////////////////////
        glTranslatef(30.0, 45.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    window();
    glLoadIdentity();
    glPopMatrix();
}


void blast()///////////////////######################################### blast
{
glBegin(GL_POLYGON);////////////// squre
glColor3f (1.0,1.0,0.0);

glVertex2f(70.0f, 50.0f );
glVertex2f(90.0f, 50.0f );
glVertex2f(90.0f, 30.0f );
glVertex2f(70.0f, 30.0f );
glEnd();

glBegin(GL_POLYGON);////////////// tringle1
glColor3f (1.0,1.0,0.0);

glVertex2f(f+75.0f, 53.0f );
glVertex2f(f+75.0f, 38.0f );
glVertex2f(f+55.0f, 45.0f );
glEnd();
glBegin(GL_POLYGON);////////////// tringle2
glColor3f (1.0,1.0,0.0);

glVertex2f(f+75.0f, 42.0f );
glVertex2f(f+75.0f, 28.0f );
glVertex2f(f+55.0f, 35.0f );
glEnd();
/////////////////////////upper
glBegin(GL_POLYGON);////////////// tringle3
glColor3f (1.0,1.0,0.0);

glVertex2f(75.0f, f+67.0f );
glVertex2f(82.0f, f+45.0f );
glVertex2f(67.0f, f+45.0f );
glEnd();

glBegin(GL_POLYGON);////////////// tringle4
glColor3f (1.0,1.0,0.0);

glVertex2f(85.0f, f+67.0f );
glVertex2f(92.0f, f+45.0f );
glVertex2f(77.0f, f+45.0f );
glEnd();

////////// right
glBegin(GL_POLYGON);////////////// tringle5
glColor3f (1.0,1.0,0.0);

glVertex2f(f+88.0f, 51.0f );
glVertex2f(f+100.0f, 45.0f );
glVertex2f(f+88.0f, 40.0f );
glEnd();
glBegin(GL_POLYGON);////////////// tringle6
glColor3f (1.0,1.0,0.0);

glVertex2f(f+88.0f, 41.0f );
glVertex2f(f+100.0f, 35.0f );
glVertex2f(f+88.0f, 30.0f );
glEnd();

//////////////////// lower
glBegin(GL_POLYGON);////////////// tringle7
glColor3f (1.0,1.0,0.0);

glVertex2f(70.0f, f+40.0f );
glVertex2f(83.0f, f+40.0f );
glVertex2f(75.0f, f+5.0f );
glEnd();
glBegin(GL_POLYGON);////////////// tringle8
glColor3f (1.0,1.0,0.0);

glVertex2f(77.0f, f+40.0f );
glVertex2f(90.0f, f+40.0f );
glVertex2f(85.0f, f+5.0f );
glEnd();

glBegin(GL_POLYGON);////////////// corner 1
glColor3f (1.0,1.0,0.0);

glVertex2f(f+70.0f, f+45.0f );
glVertex2f(f+64.0f, f+60.0f );
glVertex2f(f+75.0f, f+50.0f );
glEnd();

glBegin(GL_POLYGON);////////////// corner 2
glColor3f (1.0,1.0,0.0);

glVertex2f(f+85.0f, f+50.0f );
glVertex2f(f+100.0f, f+60.0f );
glVertex2f(f+90.0f, f+45.0f );
glEnd();

glBegin(GL_POLYGON);////////////// corner 3
glColor3f (1.0,1.0,0.0);

glVertex2f(f+90.0f,f+35.0f );
glVertex2f(f+95.0f, f+20.0f );
glVertex2f(f+85.0f, f+30.0f );
glEnd();

glBegin(GL_POLYGON);////////////// corner 4
glColor3f (1.0,1.0,0.0);

glVertex2f(f+70.0f, f+35.0f );
glVertex2f(f+75.0f, f+30.0f );
glVertex2f(f+60.0f, f+20.0f );
glEnd();
}
void blast1()//////////////////////////////////////////blast 1
{glPushMatrix();
    glTranslatef(0.0, 0.00, 0);
    //glScalef(1.0, 1.0, 0.0);
    blast();
    glLoadIdentity();
    glPopMatrix();
}
void blast2()//////////////////////////////////////////blast 2
{glPushMatrix();
    glTranslatef(28.0, 55.00, 0);
    glScalef(0.70, 0.70, 0.0);
    blast();
    glLoadIdentity();
    glPopMatrix();
}
void movingline()
{

      glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo-77.0f, -25.0f );
glVertex2f(mo-72.0f, -25.0f );
glEnd();

     glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo-67.0f, -25.0f );
glVertex2f(mo-56.0f, -25.0f );
glEnd();

     glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo+10.0f, -25.0f );
glVertex2f(mo+15.0f, -25.0f );
glEnd();


  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo-50.0f, -25.0f );
glVertex2f(mo-40.0f, -25.0f );
glEnd();

  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo-30.0f, -25.0f );
glVertex2f(mo-20.0f, -25.0f );
glEnd();

  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo+30.0f, -25.0f );
glVertex2f(mo+20.0f, -25.0f );
glEnd();

  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo-30.0f, -15.0f );
glVertex2f(mo-20.0f, -15.0f );
glEnd();

  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo-80.0f, -15.0f );
glVertex2f(mo-90.0f, -15.0f );
glEnd();

  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo-10.0f, -15.0f );
glVertex2f(mo+0.0f, -15.0f );
glEnd();

  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo-30.0f, -5.0f );
glVertex2f(mo-20.0f, -5.0f );
glEnd();
  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo-10.0f, -5.0f );
glVertex2f(mo+0.0f, -5.0f );
glEnd();

  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo-30.0f, 0.0f );
glVertex2f(mo-25.0f, 0.0f );
glEnd();
  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo-20.0f, 0.0f );
glVertex2f(mo-15.0f, 0.0f );
glEnd();

  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo-30.0f, -2.0f );
glVertex2f(mo-25.0f, -2.0f );
glEnd();
  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo-20.0f, -2.0f );
glVertex2f(mo-15.0f, -2.0f );
glEnd();

  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo-20.0f, -2.0f );
glVertex2f(mo-15.0f, -2.0f );
glEnd();
  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo-10.0f, -2.0f );
glVertex2f(mo-5.0f, -2.0f );
glEnd();

  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo+20.0f, -2.0f );
glVertex2f(mo+15.0f, -2.0f );
glEnd();

  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo+10.0f, -2.0f );
glVertex2f(mo+5.0f, -2.0f );
glEnd();

////
  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo-10.0f, -15.0f );
glVertex2f(mo-5.0f, -15.0f );
glEnd();

  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo+20.0f, -10.0f );
glVertex2f(mo+15.0f, -10.0f );
glEnd();

  glBegin(GL_LINES);
glColor3f (0.0,0.0,0.0);

glVertex2f(mo+10.0f, -7.0f );
glVertex2f(mo+5.0f, -7.0f );
glEnd();
 /////////////////////////////////
if(mo>=-100)
{
    mo=mo-.02;

}
else{
    mo=10;
}
}

void palestine()
{


        glBegin(GL_POLYGON);///// danda
glColor3f (0.3,0.3,0.5);

glVertex2f(0.0f, -45.0f );
glVertex2f(1.0f, -45.0f );
glVertex2f(1.0f, -70.0f );
glVertex2f(0.0f, -70.0f );
glEnd();

            glBegin(GL_POLYGON);///// danda gora
glColor3f (0.3,0.3,0.1);

glVertex2f(-1.0f, -68.0f );
glVertex2f(2.0f, -68.0f );
glVertex2f(2.0f, -70.0f );
glVertex2f(-1.0f, -70.0f );
glEnd();

        glBegin(GL_POLYGON);///// black
glColor3f (0.0,0.0,0.0);

glVertex2f(1.0f, -45.0f );
glVertex2f(15.0f, -45.0f );
glVertex2f(15.0f, -48.0f );
glVertex2f(1.0f, -48.0f );
glEnd();
        glBegin(GL_POLYGON);///// white
glColor3f (1.0,1.0,1.0);

glVertex2f(1.0f, -48.0f );
glVertex2f(15.0f, -48.0f );
glVertex2f(15.0f, -52.0f );
glVertex2f(1.0f, -52.0f );
glEnd();
        glBegin(GL_POLYGON);///// green
glColor3f (0.0,0.7,0.0);
glVertex2f(1.0f, -52.0f );
glVertex2f(15.0f, -52.0f );
glVertex2f(15.0f, -55.0f );
glVertex2f(1.0f, -55.0f );
glEnd();
        glBegin(GL_POLYGON);///// triangle
glColor3f (1.0,0.0,0.0);

glVertex2f(1.0f, -45.0f );
glVertex2f(5.0f, -50.0f );
glVertex2f(1.0f, -55.0f );
//glVertex2f(0.0f, -70.0f );
glEnd();



}
void bottom()
{
    glBegin(GL_POLYGON);
glColor3f (0.5,0.7,0.3);

glVertex2f(-100.0f, 0.0f );
glVertex2f(100.0f, 0.0f );
glVertex2f(100.0f, -100.0f );
glVertex2f(-100.0f, -100.0f );
glEnd();

}
void soundbomb() {
    PlaySound("bomb.wav", NULL, SND_ASYNC );

       // getch();
        //return 0;
    //sndPlaySound("bomb.wav", SND_ASYNC);
}
void back() {
    //PlaySound("back.wav", NULL, SND_ASYNC );
        PlaySound("back.wav", NULL, SND_ASYNC | SND_FILENAME | SND_LOOP);
    //sndPlaySound("bomb.wav", SND_ASYNC);
}
void soundNull() {
    PlaySound(NULL, 0, 0);
}
void display(void)//////////////////////****************************** DISPLAY*************************
{
/* clear all pixels */
glClear(GL_COLOR_BUFFER_BIT);

 glutPostRedisplay();

bottom();
sky();
//axis();
runcloud();
mountain();
movingline();
//////helicopter
helicopter();

////////////////struck
struck1();
//struck2();
struck4();
struck5();
////////////// truck
truck2();
truck1();

///////////////////////////////////////tank
tank3();
tank2();
tank();


border();
//////////// building
building();
//////// windows
windows();
antimissilesystem();
/////// radar
radar();

/////////////// jet
jet1();
jet2();
jet3();

palestine();
//blast2();/////////////////////////////blast 2
///////////////////////////////// gamming
///////////////////// rocket launcher
rocketlauncher();
//rocket();
rocketlauncher2();

///// for target rocket

printf("   %d\n",k);
///////////////////// end of target rocket

	//glPushMatrix();
glPushMatrix();

glTranslatef(tx,ty,0);
printf("%d\n", intVariable);
rocket();
//board2();////////////////////////text

glPopMatrix();
////////////////////////////////////////// condition 1
if(intVariable>139 && intVariable<147)
{
 if(k>1800 && k<2400)//2300
    {
       // soundbomb();
      blast2();
      if(px<=250)//250//150
        {
         px=px+2;
         py=py+.9;
         blast1();


         for(int i=0;i<10;i++)
            {
             target();
            }
            tx=0;
            ty=0;
           if(px>150)//200well but (150 more)
             {
               px=0;
               py=0;
             }

             }

             else{
                 //soundNull() ;
             }
             }

            else{
                //soundNull() ;
                px=0;
                py=0;
                                         //gameover();
                }

}
////////////////////// end of condition 1
////////////////////////////////////////// condition 2
else if(intVariable>137 )//&& intVariable<147 )
{

 if(k<1800 || k>2400)//2300
{

      gameover();
     px=0;
     py=0;


}
}
////////////////////// end of condition 2
if(intVariable>150)
{
    tx=0;
    ty=0;
    intVariable=0;
}

glFlush();
}
void init(void)
{
glClearColor(0.90, 0.60, 1.0, 0.0);
glMatrixMode(GL_PROJECTION);
glLoadIdentity();
glOrtho(-100, 100, -100, 100, -15, 15);
//-x,x,-y,y
}

void spe_key(int key, int x, int y)////////////////////////////////// key
{

	switch (key) {

		case GLUT_KEY_LEFT:
				tx -=1;
				ty-=.9;
				 intVariable=intVariable-1;

				glutPostRedisplay();

				break;

		case GLUT_KEY_RIGHT:
				tx +=1;
				ty+=.9;
				intVariable=intVariable+1;
				glutPostRedisplay();
				break;



          case GLUT_KEY_UP:
                ty +=1;
                soundbomb();
				glutPostRedisplay();
				break;
          case GLUT_KEY_DOWN:
                ty -=1;
				glutPostRedisplay();
				break;

	  default:
			break;
	}
}

int main(int argc, char** argv)
{
glutInit(&argc, argv);
glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB);
glutInitWindowSize(1000, 600);
glutInitWindowPosition(100, 100);
glutCreateWindow("Syeed MD Tuaha(192-15-13126) Computer Graphics Lab Project-- Free Palestine Game");
init();
back();
glutDisplayFunc(display);
glutSpecialFunc(spe_key);
glutMainLoop();
return 0; /* ISO C requires main to return int. */
}
