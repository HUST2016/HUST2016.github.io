# Image Analysis and Understanding    

                       ----Color Detection and Recognition from 2D images     
                                 指导老师： 杨欣     


## 1.description of the project
   The  goal  of  color  detection  and  recognition  is,  given  an  image  including  several 
colored  objects,  to  detect  object  which has the same  color  as  the colored  objects  in a 
database  (the shape of the  query object  in an image can be different from those in the 
database)  and if yes label  the  color  on the object.
## 2.Work schedule
### 第三周    
<br />
    查看相关文献和建立网站
<br />

### 第四周
<div>&nbsp;小组讨论，查看相关文献确定研究思路以及每个组员的分工；</div><div>&nbsp;进一步美化网页；&nbsp;</div><div>&nbsp;环境配置：python 2.7.9、opencv2.4.13、Numpy1.12.1等相关库包</div><div>&nbsp;IDE &nbsp; &nbsp; &nbsp; &nbsp;：JetBrains PyCharm Community Edition&nbsp;</div><div>&nbsp;注意事项：<span style="line-height: 1.7;">建议使用python2.7版本（python3.0可能出现与相关包不兼容）&nbsp;</span></div><div>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 同时建议安装Anaconda2，里面包含了大多数的python库包，可方便使用 </div><div>     
 &nbsp;项目流程：</div>       
          
<br />       
![image](https://raw.githubusercontent.com/HUST2016/HUST2016.github.io/master/images/1.png)          
<br />
### 第五周
<br />
<div>编程实现，部分相关程序代码：</div><div><pre style="font-family: 宋体; color: rgb(169, 183, 198); font-size: 12pt; background-color: rgb(43, 43, 43);"><div><span style="font-size: 12pt; line-height: 1.7;">M = cv2.moments(c) </span><span style="font-size: 12pt; line-height: 1.7; color: rgb(217, 139, 139);">#轮廓c的  矩, 计算中心距（中心距可由原点矩（几何矩）计算）</span></div><span style="color: rgb(217, 139, 139);">#print('M["m00"]: ',M["m00#轮廓的  矩"])<br /></span><span style="color: rgb(204, 120, 50); font-weight: bold;">if </span>(M[<span style="color: rgb(165, 194, 97);">"m00"</span>] == <span style="color: rgb(233, 36, 159);">0</span>):<span style="color: rgb(217, 139, 139);"><br /></span><span style="color: rgb(217, 139, 139);">   </span>M[<span style="color: rgb(165, 194, 97);">"m00"</span>]=<span style="color: rgb(233, 36, 159);">1</span><span style="color: rgb(217, 139, 139);"><br /></span>cX = <span style="color: rgb(136, 136, 198);">int</span>((M[<span style="color: rgb(165, 194, 97);">"m10"</span>] / M[<span style="color: rgb(165, 194, 97);">"m00"</span>]) * ratio)<span style="color: rgb(217, 139, 139);">#M["m10"] / M["m00"] 表示x坐标（列）<br /></span>cY = <span style="color: rgb(136, 136, 198);">int</span>((M[<span style="color: rgb(165, 194, 97);">"m01"</span>] / M[<span style="color: rgb(165, 194, 97);">"m00"</span>]) * ratio)<span style="color: rgb(217, 139, 139);">#"m10"，"m01"表示x、y方向的一阶原点矩（由原点矩可计算中心距）<br /></span><span style="color: rgb(217, 139, 139);">#print('cX:', cX, 'cY: ', cY)#print(image[cY, cX])<br /></span><span style="color: rgb(217, 139, 139);">#detect the shape of the contour and label the color<br /></span>shape = sd.detect(c)<span style="color: rgb(217, 139, 139); font-size: 12pt; line-height: 1.7;">#自定义的形状检测函数</span><br />color = cl.label(lab<span style="color: rgb(204, 120, 50);">, </span>c)<span style="color: rgb(217, 139, 139); font-size: 12pt; line-height: 1.7;">#自定义的颜色检测函数</span><br /><span style="color: rgb(217, 139, 139);">#根据轮廓的坐标值进行画出轮廓<br /></span>c = c.astype(<span style="color: rgb(165, 194, 97);">"float"</span>)<br />c *= ratio<br />c = c.astype(<span style="color: rgb(165, 194, 97);">"int"</span>)<br />text = <span style="color: rgb(165, 194, 97);">"{} {}"</span>.format(color<span style="color: rgb(204, 120, 50);">, </span>shape)<br />cv2.drawContours(image<span style="color: rgb(204, 120, 50);">, </span>[c]<span style="color: rgb(204, 120, 50);">, </span>-<span style="color: rgb(233, 36, 159);">1</span><span style="color: rgb(204, 120, 50);">, </span>(<span style="color: rgb(233, 36, 159);">0</span><span style="color: rgb(204, 120, 50);">, </span><span style="color: rgb(233, 36, 159);">255</span><span style="color: rgb(204, 120, 50);">, </span><span style="color: rgb(233, 36, 159);">0</span>)<span style="color: rgb(204, 120, 50);">, </span><span style="color: rgb(233, 36, 159);">2</span>)<br />cv2.putText(image<span style="color: rgb(204, 120, 50);">, </span>text<span style="color: rgb(204, 120, 50);">, </span>(cX<span style="color: rgb(204, 120, 50);">, </span>cY)<span style="color: rgb(204, 120, 50);">,<br /></span><span style="color: rgb(204, 120, 50);">   </span>cv2.FONT_HERSHEY_SIMPLEX<span style="color: rgb(204, 120, 50);">, </span><span style="color: rgb(233, 36, 159);">0.5</span><span style="color: rgb(204, 120, 50);">, </span>(<span style="color: rgb(233, 36, 159);">255</span><span style="color: rgb(204, 120, 50);">, </span><span style="color: rgb(233, 36, 159);">255</span><span style="color: rgb(204, 120, 50);">, </span><span style="color: rgb(233, 36, 159);">255</span>)<span style="color: rgb(204, 120, 50);">, </span><span style="color: rgb(233, 36, 159);">2</span>)<br /><span style="color: rgb(217, 139, 139);">#show the output image<br /></span>cv2.imshow(<span style="color: rgb(165, 194, 97);">"Image"</span><span style="color: rgb(204, 120, 50);">, </span>image)<br />cv2.waitKey(<span style="color: rgb(233, 36, 159);">700</span>)</pre></div>
<br />

### 第六周
<br />    
项目各个部分展示：      
（1）原始图像、高斯滤波、图像二值化     
![image](https://raw.githubusercontent.com/HUST2016/HUST2016.github.io/master/images/2.jpg)       
 对二值化后的图像进行形状检测，并计算出各个轮廓的质心          
 ![image](https://raw.githubusercontent.com/HUST2016/HUST2016.github.io/master/images/3.gif)       
 （2）识别各个形状的具体类型（三角形、长（正）方形、五边形、圆形），并标出          
 ![image](https://raw.githubusercontent.com/HUST2016/HUST2016.github.io/master/images/4.gif)     
（3）识别各个形状的颜色     
（4）结合（1）、（2）、（3），在每个形状的质心处输出 “ 形状+颜色  ” 的信息标注       
![image](https://raw.githubusercontent.com/HUST2016/HUST2016.github.io/master/images/5.gif)      
 
<br /> 

## 3.The outcome of the project
<br />
<br />   
   To Be Continued    
<br />
<br />
## Group Members
<div>
    <table border="0">
      <tr>
        <th>NAME</th>
        <th>Student ID</th>
      </tr>
      <tr>
        <td>张蓥 </td>
        <td>M201671 </td>
      </tr>
      <tr>
        <td>朱冉 </td>
        <td>M201671 </td>
      </tr>
      <tr>
        <td>艾维 </td>
        <td>M201671795 </td>
      </tr>
      <tr>
        <td>陈怡 </td>
        <td>M201671 </td>
      </tr>
      <tr>
        <td>于胜举 </td>
        <td>M201671793  </td>
      </tr>      
    </table>
</div>      

## Reference   
<div>[1]<a href="https://www.youtube.com/watch?v=o_9lKLUpQSQ" _src="https://www.youtube.com/watch?v=o_9lKLUpQSQ">https://www.youtube.com/watch?v=o_9lKLUpQSQ</a></div><div>[2]<a href="https://vimeo.com/2381394" _src="https://vimeo.com/2381394">https://vimeo.com/2381394</a></div><div>[3]<a href="http://dsqiu.iteye.com/blog/1638589" _src="http://dsqiu.iteye.com/blog/1638589">http://dsqiu.iteye.com/blog/1638589</a></div><div>[4]<a href="http://www.csdn.net/article/2012-07-03/2807073-k-means" _src="http://www.csdn.net/article/2012-07-03/2807073-k-means">http://www.csdn.net/article/2012-07-03/2807073-k-means</a></div>
