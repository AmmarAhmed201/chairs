# chairs
from OpenGL.GL import *
from OpenGL.GLU import *
from OpenGL.GLUT import *

def init():
    glMatrixMode(GL_PROJECTION)
    gluPerspective(60,1,0.1,50)
    gluLookAt(10,10,10,0,0,0,0,1,0)
    glClearColor(0,0,0,1)

def draw1(size, x, y, z):#draw cube
    glPushAttrib(GL_ALL_ATTRIB_BITS)
    glPushMatrix()

    glMatrixMode(GL_MODELVIEW)
    glScale(x, y, z)
    glutSolidCube(size)
    glPopMatrix()
    glPopAttrib()
    glLoadIdentity()

def draw2():#draw chair
    glPushAttrib(GL_ALL_ATTRIB_BITS)
    glPushMatrix()
    glTranslate(0,0,0)
    draw1(2,3,.5,2)



    glTranslate(-8,2.5,-2.5)
    draw1(2,3,3,.5)

    glTranslate(2, 2.5, -2.5)
    draw1(2,3,3,.5)

    glTranslate(4, -5, -4.5)
    draw1(1,.6,6,.6)

    glTranslate(-7,-5,-4)
    draw1(1,.6,6,.6)

    glTranslate(4,-5,0)
    draw1(1,.6,6,.6)

    glTranslate(-7,-5,0)
    draw1(1,.6,6,.6)

    glTranslate(-3,-5,0)
    draw1(1,.6,6,.6)

    glTranslate(-14, -5, 0)
    draw1(1,.6,6,.6)

    glTranslate(-3, -5, -4.5)
    draw1(1,.6,6,.6)

    glTranslate(-14,-5,-4.5)
    draw1(1,.6,6,.6)
    glPopMatrix()
    glPopAttrib()




def draw():
    glMatrixMode(GL_MODELVIEW)
    glColor(1,1,0)
    glTranslate(-7, 0, 0)
    draw2()
    glLoadIdentity()
    glTranslate(2, 0, 0)
    draw2()
    glLoadIdentity()
    glFlush()



glutInit()
glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB)
glutInitWindowSize(600,600)
glutCreateWindow(b"First OpenGL program")
init()
glutDisplayFunc(draw)
glutMainLoop()
