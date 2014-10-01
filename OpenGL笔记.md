OpenGL学习笔记
##########


## `gluLookAt()`函数的深入理解

  void gluLookAt(	GLdouble eyeX, GLdouble eyeY, GLdouble eyeZ,           // Specifies the position of the eye point.      相机位置
   	              GLdouble centerX, GLdouble centerY, GLdouble centerZ,  // Specifies the position of the reference point.参考点
   	              GLdouble upX, GLdouble upY, GLdouble upZ);             // Specifies the direction of the up vector.     上方向
   	              

`gluLookAt()`函数用于定义视图变换。深入学习该函数有助于理解OpenGL的模型视图变换。先看[官方说明](https://www.opengl.org/sdk/docs/man2/xhtml/gluLookAt.xml)：


> gluLookAt creates a viewing matrix derived from an eye point, a reference point indicating the center of the scene, and an UP vector.
> 
> The matrix maps the reference point to the negative z axis and the eye point to the origin. When a typical projection matrix is used, the center of the scene therefore maps to the center of the viewport. Similarly, the direction described by the UP vector projected onto the viewing plane is mapped to the positive y axis so that it points upward in the viewport. The UP vector must not be parallel to the line of sight from the eye point to the reference point.

#### 解读官方描述：

`gluLookAt` 使用视点、指出场景中心的参考点和上方向向量这三个参数创建了一个视图矩阵。

该矩阵的效果为：参考点(`center`)位于z轴负方向，视点(`eye`)位于原点，参考点和视点共同确定了相机坐标的z轴；当使用普通的投影矩阵(我估计就是正交投影和透视投影吧)时，场景的中心点(`center`)将被渲染到视口的中心，确定了裁切面；上方向向量在观察平面(xoy平面)上的投影 所确定的方向被映射为正y轴，从而令它指向视口上方。特别强调的是，向上矢量不可以与视线(从视点到参考点的连线)平行，否则上方向向量将无效。
