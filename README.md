# Course managing System

This project aims to add Programe and Emphasis management to the UofT system, so that students can plan graduate courses more conveniently. This project is the secondary development of vue-admin-template. In order to facilitate my study, this project uses native Axios and vue-router to replace some of the integrated functions of the original project. 



This is just a simple attempt at front-end development in my graduate course, and the project continues to be updated...



All vue page files are stored in /src/views

#### Login Page:
support the basic login and register function. Use token for validating.
![image](https://user-images.githubusercontent.com/55111215/124765676-c931a980-df68-11eb-9ebe-2395f1188bcc.png)


#### Management Page:

When the user logs in as an administrator, the management of the course list (not the real name) is displayed, and the background uses node.js and mongodb to complete the corresponding additions, deletions, and changes. 



Supports course name, code search, etc., and can group courses to manage, click on the course to view the corresponding information.


![image](https://user-images.githubusercontent.com/55111215/124474711-71156e80-ddd3-11eb-9b58-6b55cf52bb82.png)



update 7.5: 

Added request interface throttling and search debounce function

![image](https://user-images.githubusercontent.com/55111215/124474765-8094b780-ddd3-11eb-80b3-4705b41c3a0b.png)









#### Main Page:

Show the overall situation. Support project overview, quickly add courses, and schedule generation, etc. 

![image-20210705202006011](https://user-images.githubusercontent.com/55111215/124470640-71f7d180-ddce-11eb-989a-b44cc4b9fe3b.png)







#### Course Table:

Support dynamic display of courses, click to display course details

![image-20210705200915079](https://user-images.githubusercontent.com/55111215/124470483-3c52e880-ddce-11eb-9d4a-8e9fb2d80ab0.png)




#### Course Selection and Emphasis Management Page:


Still learning and updating...

