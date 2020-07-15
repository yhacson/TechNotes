# 渲染管线（临时）

参考:
[猴子也能看懂的渲染管线](https://zhuanlan.zhihu.com/p/137780634)
[OpenGL Wiki Rendering Pipeline](https://www.khronos.org/opengl/wiki/Rendering_Pipeline_Overview)

## 坐标转换

---

### 法线 局部模型坐标转换到世界坐标

需要高度注意的是：顶点法向量在模型文件中属于 object space，在 GPU 的
顶点程序中必须将法向量转换到 world space 中才能使用，如同必须将顶点坐标
从 object space 转换到 world space 中一样，但两者的转换矩阵是不同的，准确的
说，法向量从 object space 到 world space 的转换矩阵是 world matrix 的转置矩阵
的逆矩阵（许多人在顶点程序中会将两者的转换矩阵当作同一个，结果会出现难
以查找的错误）。（参阅潘李亮的 3D 变换中法向量变换矩阵的推导一文）

—— 《GPU编程与CG语言之阳春白雪下里巴人》（2.1.1 从 object space 到 world space）

---