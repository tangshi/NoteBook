OpenGL学习笔记
##########


## `gluLookAt()`函数的深入理解

  void gluLookAt(	GLdouble eyeX, GLdouble eyeY, GLdouble eyeZ,           // Specifies the position of the eye point.      相机位置
   	              GLdouble centerX, GLdouble centerY, GLdouble centerZ,  // Specifies the position of the reference point.参考点
   	              GLdouble upX, GLdouble upY, GLdouble upZ);             // Specifies the direction of the up vector.     上方向
   	              

`gluLookAt()`函数用于定义视图变换。深入学习该函数有助于理解OpenGL的模型视图变换。先看[官方说明](https://www.opengl.org/sdk/docs/man2/xhtml/gluLookAt.xml)：
