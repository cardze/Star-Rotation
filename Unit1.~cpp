//---------------------------------------------------------------------------

#include <vcl.h>
#pragma hdrstop

#include "Unit1.h"
//---------------------------------------------------------------------------
#pragma package(smart_init)
#pragma link "GLCtrl"
#pragma resource "*.dfm"
TForm1 *Form1;

#define AXES 1
#define SUN 2
#define MERCURY 3
#define MERCURY_TRACE 4
#define VENUS 5
#define VENUS_TRACE 6
#define EARTH 7
#define EARTH_TRACE 8
#define MARS 9
#define MARS_TRACE 10
GLUquadricObj* Obj;
double SunRotate=0.0;
double MercuryRevolve=0.0 , MercuryRotate=0.0;
double VenusRotate=0.0, VenusRevolve=0.0 ;
double EarthRotate=0.0, EarthRevolve=0.0;
double MarsRotate=0.0, MarsRevolve=0.0;

void GenerateList(){
Obj=gluNewQuadric();
    glNewList(AXES, GL_COMPILE);
        glBegin(GL_LINES);    // axes
           glColor3f(1.0, 0.0, 0.0);
           glVertex3f(0.0, 0.0, 0.0);
           glVertex3f(24.0, 0.0, 0.0);
           glColor3f(0.0, 1.0, 0.0);
           glVertex3f(0.0, 0.0, 0.0);
           glVertex3f(0.0, 24.0, 0.0);
           glColor3f(0.0, 0.0, 1.0);
           glVertex3f(0.0, 0.0, 0.0);
           glVertex3f(0.0, 0.0, 24.0);
       glEnd();
   glEndList();
   glNewList(SUN, GL_COMPILE);
       glPushMatrix();
       gluQuadricDrawStyle(Obj, GLU_FILL);
       gluQuadricTexture(Obj,GL_TRUE);
       glColor3f (1.0, 0.04, 0.0);
       glRotatef(90.0,1.0,0.0,0.0);
       gluSphere(Obj, 1.392, 36, 12);   // sun 1.392 x 10^6 km
       glPopMatrix();
   glEndList();
   glNewList(MERCURY, GL_COMPILE);
       glPushMatrix();
       gluQuadricDrawStyle(Obj, GLU_FILL);
       glColor3f (0.94, 0.74, 0.54);
       glRotatef(52.92,1.0,0.0,0.0);
       gluSphere(Obj, 0.4868, 36, 12);   // mercury 4868 km
       glPopMatrix();
   glEndList();
   glNewList(MERCURY_TRACE, GL_COMPILE);
       glPushMatrix();
       gluQuadricDrawStyle(Obj, GLU_LINE);
       glColor3f (1.0, 1.0, 1.0);
       glRotatef(90.0,1.0,0.0,0.0);
       gluDisk(Obj, 5.8, 5.8, 500, 1);   // mercury revolve track
       glPopMatrix();
   glEndList();
   glNewList(VENUS, GL_COMPILE);
       glPushMatrix();
       gluQuadricDrawStyle(Obj, GLU_FILL);
       glColor3ub(254, 245, 215);
       glRotatef(88.74,1.0,0.0,0.0);
       gluSphere(Obj, 1.2103, 36, 12);    // venus 12103 km
       glPopMatrix();
   glEndList();
   glNewList(VENUS_TRACE, GL_COMPILE);
       glPushMatrix();
       gluQuadricDrawStyle(Obj, GLU_LINE);
       glColor3f (1.0, 1.0, 1.0);
       glRotatef(90.0,1.0,0.0,0.0);
       gluDisk(Obj, 10.75, 10.75, 500, 1);   // venus revolve track
       glPopMatrix();
   glEndList();
   glNewList(EARTH, GL_COMPILE);
       glPushMatrix();
       gluQuadricDrawStyle(Obj, GLU_LINE);
       glColor3ub(200, 200, 254);
       glRotatef(86.94,1.0,0.0,0.0);
       gluSphere(Obj, 1.2742, 24, 12);    // earth 12742 km
       glPopMatrix();
   glEndList();
   glNewList(EARTH_TRACE, GL_COMPILE);
       glPushMatrix();
       gluQuadricDrawStyle(Obj, GLU_LINE);
       glColor3f (1.0, 1.0, 1.0);
       glRotatef(90.0,1.0,0.0,0.0);
       gluDisk(Obj, 14.96, 14.96, 500, 1);   // earth revolve track
       glPopMatrix();
   glEndList();
   glNewList(MARS, GL_COMPILE);
       glPushMatrix();
       gluQuadricDrawStyle(Obj, GLU_FILL);
       glColor3ub(255, 100, 50);
       glRotatef(73.26,1.0,0.0,0.0);
       gluSphere(Obj, 0.6794, 36, 12);    // mars 6794 km
       glPopMatrix();
   glEndList();
   glNewList(MARS_TRACE, GL_COMPILE);
       glPushMatrix();
       gluQuadricDrawStyle(Obj, GLU_LINE);
       glColor3f (1.0, 1.0, 1.0);
       glRotatef(90.0,1.0,0.0,0.0);
       gluDisk(Obj, 22.794, 22.794, 500, 1);   // mars revolve track
       glPopMatrix();
   glEndList();
}

void calllist(){
        glCallList(AXES);    // draw axes
        glPushMatrix();
        glRotatef(SunRotate, 0.0, 1.0, 0.0);
        glCallList(SUN); // draw sun
        glPopMatrix();

        glPushMatrix();
        gluQuadricDrawStyle(Obj, GLU_LINE);
        glRotatef (7.0, 1.0, 0.0, 0.0);
        glRotatef (MercuryRevolve, 0.0, 1.0, 0.0);
        glCallList(MERCURY_TRACE);   // draw mercury revolve track
        glTranslatef (5.8, 0.0, 0.0);  // 58 x 10^6 km
        glRotatef (MercuryRotate, 0.0, 1.0, 0.0);
        glCallList(MERCURY);  // draw mercury
        glPopMatrix();

        glPushMatrix();
        gluQuadricDrawStyle(Obj, GLU_LINE);
        glRotatef (3.4, 1.0, 0.0, 0.0);
        glRotatef (VenusRevolve, 0.0, 1.0, 0.0);
        glCallList(VENUS_TRACE);     // draw venus revolve track
        glTranslatef (10.75, 0.0, 0.0);  // 107.5 x 10^6 km
        glRotatef (-VenusRotate, 0.0, 1.0, 0.0);
        glCallList(VENUS);   // draw venus
        glPopMatrix();

        glPushMatrix();
        gluQuadricDrawStyle(Obj, GLU_LINE);
        glRotatef (7.1, 1.0, 0.0, 0.0);
        glRotatef (EarthRevolve, 0.0, 1.0, 0.0);
        glCallList(EARTH_TRACE);     // draw venus revolve track
        glTranslatef (14.71, 0.0, 0.0);  // 147.1 x 10^6 km
        glRotatef (-EarthRotate, 0.0, 1.0, 0.0);
        glCallList(EARTH);   // draw venus
        glPopMatrix();

        glPushMatrix();
        gluQuadricDrawStyle(Obj, GLU_LINE);
        glRotatef (1.8, 1.0, 0.0, 0.0);
        glRotatef (MarsRevolve, 0.0, 1.0, 0.0);
        glCallList(MARS_TRACE);     // draw venus revolve track
        glTranslatef (22.794, 0.0, 0.0);  // 227.94 x 10^6 km
        glRotatef (-MarsRotate, 0.0, 1.0, 0.0);
        glCallList(MARS);   // draw venus
        glPopMatrix();
}



//---------------------------------------------------------------------------
__fastcall TForm1::TForm1(TComponent* Owner)
        : TForm(Owner)
{
}
//---------------------------------------------------------------------------

void __fastcall TForm1::Draw(TObject *Sender)
{
        glClear(GL_COLOR_BUFFER_BIT|GL_DEPTH_BUFFER_BIT);

        glMatrixMode(GL_PROJECTION);
        glLoadIdentity();
        glOrtho(-25.0,25.0,-25.0,25.0,-25.0,25.0);

        gluLookAt(1.0,1.0,1.0,0.0,0.0,0.0,0.0,1.0,0.0);
        glMatrixMode(GL_MODELVIEW);
        glLoadIdentity();
        GenerateList();
        calllist();
        glFlush();

}
//---------------------------------------------------------------------------
void __fastcall TForm1::init(TObject *Sender)
{
        glEnable(GL_DEPTH_TEST);
        glClearColor(0.1,0.1,0.1,1.0);
}
//---------------------------------------------------------------------------
void __fastcall TForm1::Timer1Timer(TObject *Sender)
{
        GLBox1->Invalidate();
        const double SunRotateFactor = 360.0 / 26.9;
        const double MercuryRevolveFactor = 360.0 / 87.97;
        const double MercuryRotateFactor = 360.0 / 58.6;
        const double VenusRevolveFactor = 360.0 / 224.7;
        const double VenusRotateFactor = 360.0 / 243.01;
        const double EarthRevolveFactor = 360.0 / 365.26;
        const double MarsRevolveFactor = 360.0 / 686.98;
        const double MarsRotateFactor = 360.0 / 1.026;

        SunRotate+=SunRotateFactor;
        //SunRotate%=360.0;
        MercuryRevolve+=MercuryRevolveFactor;
        MercuryRotate+=MercuryRotateFactor;
        VenusRotate+=VenusRevolveFactor;
        VenusRevolve+=VenusRotateFactor;
        EarthRevolve+=EarthRevolveFactor;
        EarthRotate = (int) (EarthRotate + 60) % 360;
        MarsRotate+=MarsRotateFactor;
        MarsRevolve+=MarsRevolveFactor ;

}
//---------------------------------------------------------------------------

