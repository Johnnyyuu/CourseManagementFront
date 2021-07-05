# Course managing System

This project aims to add Programe and Emphasis management to the UofT system, so that students can plan graduate courses more conveniently. This project is the secondary development of vue-admin-template. In order to facilitate my study, this project uses native Axios and vue-router to replace some of the integrated functions of the original project. 



This is just my simple attempt at front-end development in my graduate course, and the project continues to be updated...



All vue page files are stored in /src/views



#### Management Page:

When the user logs in as an administrator, the management of the course list (not the real name) is displayed, and the background uses node.js and mongodb to complete the corresponding additions, deletions, and changes. 



Supports course name, code search, etc., and can group courses to manage, click on the course to view the corresponding information.

![image-20210705201046238](C:\Users\johny\AppData\Roaming\Typora\typora-user-images\image-20210705201046238.png)



update 7.5: 

Added request interface throttling and search debounce function









#### Main Page:

Show the overall situation. Support project overview, quickly add courses, and schedule generation, etc. 



![image-20210705202006011](C:\Users\johny\AppData\Roaming\Typora\typora-user-images\image-20210705202006011.png)



#### Course Table:

Support dynamic display of courses, click to display course details

![image-20210705200915079](C:\Users\johny\AppData\Roaming\Typora\typora-user-images\image-20210705200915079.png)



#### Course Selection and Emphasis Management Page:



