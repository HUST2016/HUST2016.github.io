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
  对于每一个形状区域，构建图像掩模，经过腐蚀操作后（为了使形状更精准），计算形状区域在Lab空间的均值，之后，再与数据库中的颜色进行欧氏距离运算，找出距   离最小的，视为形状所属的颜色。              
        
  相关代码：                
  <div style="line-height:1.7;color:#000000;font-size:14px;font-family:Arial"><div><pre style="background-color:#2b2b2b;color:#a9b7c6;font-family:'宋体';font-size:12.0pt;">mask = np.zeros(<span style="color:#e7287d;">image</span>.shape[:<span style="color:#e9249f;">2</span>]<span style="color:#cc7832;">, </span><span style="color:#aa4926;">dtype</span>=<span style="color:#a5c261;">"uint8"</span>)<span style="color:#d98b8b;"><br /></span>cv2.drawContours(mask<span style="color:#cc7832;">, </span>[<span style="color:#e7287d;">c</span>]<span style="color:#cc7832;">, </span>-<span style="color:#e9249f;">1</span><span style="color:#cc7832;">, </span><span style="color:#e9249f;">255</span><span style="color:#cc7832;">, </span>-<span style="color:#e9249f;">1</span>)#构建图像掩膜<br />mask = cv2.erode(mask<span style="color:#cc7832;">, </span><span style="color:#8888c6;">None</span><span style="color:#cc7832;">, </span><span style="color:#aa4926;">iterations</span>=<span style="color:#e9249f;">2</span>)#进行腐蚀操作<br />mean = cv2.mean(<span style="color:#e7287d;">image</span><span style="color:#cc7832;">, </span><span style="color:#aa4926;">mask</span>=mask)[:<span style="color:#e9249f;">3</span>]#计算均值、之后进行欧氏距离比较即可<br /></pre></div>  </div>  
<br /> 

## 3.The outcome of the project
<br />          
  完善上周工作（1）、（2）、（3），在每个形状的质心处输出 “ 形状+颜色  ” 的信息标注                   
  ![image](https://raw.githubusercontent.com/HUST2016/HUST2016.github.io/master/images/5.gif)                  
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
<div><div style="box-sizing: border-box; color: rgb(36, 41, 46); font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol'; font-size: 16px; line-height: 24px;">[1]<a href="https://www.youtube.com/watch?v=o_9lKLUpQSQ" _src="https://www.youtube.com/watch?v=o_9lKLUpQSQ">https://www.youtube.com/watch?v=o_9lKLUpQSQ</a></div><div style="box-sizing: border-box; color: rgb(36, 41, 46); font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol'; font-size: 16px; line-height: 24px;">[2]<a href="https://vimeo.com/2381394" _src="https://vimeo.com/2381394">https://vimeo.com/2381394</a></div><div style="box-sizing: border-box; color: rgb(36, 41, 46); font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol'; font-size: 16px; line-height: 24px;">[3]<a href="http://dsqiu.iteye.com/blog/1638589" _src="http://dsqiu.iteye.com/blog/1638589">http://dsqiu.iteye.com/blog/1638589</a></div><div style="box-sizing: border-box; color: rgb(36, 41, 46); font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol'; font-size: 16px; line-height: 24px; margin-bottom: 0px !important;">[4]<a href="http://www.csdn.net/article/2012-07-03/2807073-k-means" _src="http://www.csdn.net/article/2012-07-03/2807073-k-means">http://www.csdn.net/article/2012-07-03/2807073-k-means</a></div></div><div>[5]<a href="http://blog.csdn.net/jinxiaonian11/article/details/53467437" _src="http://blog.csdn.net/jinxiaonian11/article/details/53467437">http://blog.csdn.net/jinxiaonian11/article/details/53467437</a> </div><div>[6]<a href="http://blog.csdn.net/huang9012/article/details/21811715" _src="http://blog.csdn.net/huang9012/article/details/21811715">http://blog.csdn.net/huang9012/article/details/21811715</a> </div><div>[7]<a href="http://blog.sina.com.cn/s/blog_6be2963e0100xg72.html" _src="http://blog.sina.com.cn/s/blog_6be2963e0100xg72.html">http://blog.sina.com.cn/s/blog_6be2963e0100xg72.html</a> </div><div>[8]<a href="http://www.opencv.org.cn/" _src="http://www.opencv.org.cn/">http://www.opencv.org.cn/</a></div><div>[9]<a href="http://blog.csdn.net/spw_1201/article/details/53690321" _src="http://blog.csdn.net/spw_1201/article/details/53690321">http://blog.csdn.net/spw_1201/article/details/53690321</a> </div><div>[10]<a href="http://www.cnblogs.com/hrlnw/p/4126017.html" _src="http://www.cnblogs.com/hrlnw/p/4126017.html">http://www.cnblogs.com/hrlnw/p/4126017.html</a></div><div>[11]<a href="http://blog.csdn.net/qq_15947787/article/details/51087196" _src="http://blog.csdn.net/qq_15947787/article/details/51087196">http://blog.csdn.net/qq_15947787/article/details/51087196</a> </div><div><br /></div><div><br /></div><div><br /></div>
