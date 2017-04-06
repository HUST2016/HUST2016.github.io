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
  ![Image](https://github.com/HUST2016/HUST2016.github.io/blob/master/images/1.png)
<br />

### 第五周
<br />
```Python    
   <br>
M = cv2.moments(c) #轮廓的  矩   计算中心距（中心距可由原点矩（几何矩）计算）<br>    
//print('M["m00"]: ',M["m00#轮廓的  矩"])//正方形的M["m00"]为零<br>    
if (M["m00"] == 0): <br>
	M["m00"]=1  <br>
cX = int((M["m10"] / M["m00"]) * ratio)//M["m10"] / M["m00"] 表示x坐标（列）<br>
cY = int((M["m01"] / M["m00"]) * ratio)//"m10"，"m01"表示x、y方向的一阶原点矩（由原点矩可计算中心距）<br>
//print('cX:', cX, 'cY: ', cY)#print(image[cY, cX])<br>
//detect the shape of the contour and label the color<br>
shape = sd.detect(c)<br>
color = cl.label(lab, c)<br>
//multiply the contour (x, y)-coordinates by the resize ratio,<br>
//then draw the contours and the name of the shape and labeled<br>
//color on the image   根据轮廓的坐标值进行画出轮廓<br>
c = c.astype("float")<br>
c *= ratio<br>
c = c.astype("int")<br>
text = "{} {}".format(color, shape)<br>
cv2.drawContours(image, [c], -1, (0, 255, 0), 2)<br>
cv2.putText(image, text, (cX, cY),<br>
	cv2.FONT_HERSHEY_SIMPLEX, 0.5, (255, 255, 255), 2)<br>

//show the output image<br>
cv2.imshow("Image", image)
<br>
<br>     
```
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
