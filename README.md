# Image Analysis and Understanding    

                       ----Color Detection and Recognition from 2D images     
                                 指导老师： 杨欣     


## 1.description of the project
   The  goal  of  color  detection  and  recognition  is,  given  an  image  including  several 
colored  objects,  to  detect  object  which has the same  color  as  the colored  objects  in a 
database  (the shape of the  query object  in an image can be different from those in the 
database)  and if yes label  the  color  on the object.
***
## 2.Work schedule
### 第三周    
<br />
    查看相关文献和建立网站
<br />

### 第四周
<br />
 小组讨论，确定研究思路以及每个组员的分工;<br>
 美化网页;<br>   
   
   环境配置：python 2.7.9、opencv2.4.13、Numpy1.12.1等相关库包<br>
   IDE    ：JetBrains PyCharm Community Edition  <br>
   注意事项：建议使用python2.7版本（python3.0可能出现与相关包不兼容）<br>
	    同时建议安装Anaconda2，里面包含了大多数的python库包，可方便使用 <br>     
  项目流程：<br>       
  ![Image](https://github.com/HUST2016/HUST2016.github.io/blob/master/images/333.PNG)
<br />

### 第五周
<br />
<pre style="background-color:#2b2b2b;color:#a9b7c6;font-family:'宋体';font-size:12.0pt;"><div>相关程序代码：</div><div>M = cv2.moments(c) <span style="color:#d98b8b;">#轮廓c的  矩, 计算中心距（中心距可由原点矩（几何矩）计算）<br /></span></div><span style="color:#d98b8b;">#print('M["m00"]: ',M["m00#轮廓的  矩"])<br /></span><span style="color:#cc7832;font-weight:bold;">if </span>(M[<span style="color:#a5c261;">"m00"</span>] == <span style="color:#e9249f;">0</span>):<span style="color:#d98b8b;"><br /></span><span style="color:#d98b8b;">   </span>M[<span style="color:#a5c261;">"m00"</span>]=<span style="color:#e9249f;">1</span><span style="color:#d98b8b;"><br /></span>cX = <span style="color:#8888c6;">int</span>((M[<span style="color:#a5c261;">"m10"</span>] / M[<span style="color:#a5c261;">"m00"</span>]) * ratio)<span style="color:#d98b8b;">#M["m10"] / M["m00"] 表示x坐标（列）<br /></span>cY = <span style="color:#8888c6;">int</span>((M[<span style="color:#a5c261;">"m01"</span>] / M[<span style="color:#a5c261;">"m00"</span>]) * ratio)<span style="color:#d98b8b;">#"m10"，"m01"表示x、y方向的一阶原点矩（由原点矩可计算中心距）<br /></span><span style="color:#d98b8b;">#print('cX:', cX, 'cY: ', cY)#print(image[cY, cX])<br /></span><span style="color:#d98b8b;">#detect the shape of the contour and label the color<br /></span>shape = sd.detect(c)<span style="color: rgb(217, 139, 139); font-size: 12pt; line-height: 1.7;">#自定义的形状检测函数</span><br />color = cl.label(lab<span style="color:#cc7832;">, </span>c)<span style="color: rgb(217, 139, 139); font-size: 12pt; line-height: 1.7;">#自定义的颜色检测函数</span><br /><span style="color:#d98b8b;">#根据轮廓的坐标值进行画出轮廓<br /></span>c = c.astype(<span style="color:#a5c261;">"float"</span>)<br />c *= ratio<br />c = c.astype(<span style="color:#a5c261;">"int"</span>)<br />text = <span style="color:#a5c261;">"{} {}"</span>.format(color<span style="color:#cc7832;">, </span>shape)<br />cv2.drawContours(image<span style="color:#cc7832;">, </span>[c]<span style="color:#cc7832;">, </span>-<span style="color:#e9249f;">1</span><span style="color:#cc7832;">, </span>(<span style="color:#e9249f;">0</span><span style="color:#cc7832;">, </span><span style="color:#e9249f;">255</span><span style="color:#cc7832;">, </span><span style="color:#e9249f;">0</span>)<span style="color:#cc7832;">, </span><span style="color:#e9249f;">2</span>)<br />cv2.putText(image<span style="color:#cc7832;">, </span>text<span style="color:#cc7832;">, </span>(cX<span style="color:#cc7832;">, </span>cY)<span style="color:#cc7832;">,<br /></span><span style="color:#cc7832;">   </span>cv2.FONT_HERSHEY_SIMPLEX<span style="color:#cc7832;">, </span><span style="color:#e9249f;">0.5</span><span style="color:#cc7832;">, </span>(<span style="color:#e9249f;">255</span><span style="color:#cc7832;">, </span><span style="color:#e9249f;">255</span><span style="color:#cc7832;">, </span><span style="color:#e9249f;">255</span>)<span style="color:#cc7832;">, </span><span style="color:#e9249f;">2</span>)<br /><span style="color:#d98b8b;">#show the output image<br /></span>cv2.imshow(<span style="color:#a5c261;">"Image"</span><span style="color:#cc7832;">, </span>image)<br />cv2.waitKey(<span style="color:#e9249f;">700</span>)</pre>
<br />

### 第六周
<br />
   To Be Continued
<br />
___
## 3.The outcome of the project
<br />
<br />
   To Be Continued
<br />
<br />
___
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
        <td>M201671 </td>
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
  [1] https://www.youtube.com/watch?v=o_9lKLUpQSQ  
  [2] https://vimeo.com/2381394<br  >  
  <br>
  <br>
  [HUST](http://www.hust.edu.cn/  "悬停显示")<br>
  [Bing](http://cn.bing.com/?scope=web "悬停显示")<br>
  [Ifeng](http://www.ifeng.com/  "悬停显示")<br>
  :stuck_out_tongue_winking_eye: <br>
