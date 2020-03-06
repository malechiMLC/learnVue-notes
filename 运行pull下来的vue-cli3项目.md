# 运行一个pull下来的vue-cli3项目步骤  
**特别注意：一定要是在项目目录下！！！就是`OnLine-BookStore\online-bookstore>`**  

第一步：`OnLine-BookStore\online-bookstore>` : `cnpm install`  

第二步：`OnLine-BookStore\online-bookstore>` : `cnpm install -g @vue/cli`  

第三步：`OnLine-BookStore\online-bookstore>` : `cnpm install -g @vue/cli-service-global`  

第四步：我引用的是ant-design-vue组件库，`OnLine-BookStore\online-bookstore>` : `cnpm install ant-design-vue --save`

第四步：`OnLine-BookStore\online-bookstore>` : `cnpm run serve`  
  
  
**发现pull下来的一个项目的目录框架跟我自己新建的不一样，得知是vue-cli版本的区别。**  

## vue-cli2  
初始化方法：`vue init webpack myproject`  
目录框架为：  
![vue/cli3目录框架](/pictures/notes/vue-cli3目录框架.jpg)  
 

## vue-cli3  
初始化方法：`vue create myproject`  
目录框架为：  
![vue-cli2目录框架](/pictures/notes/vue-cli2目录框架.jpg)  




