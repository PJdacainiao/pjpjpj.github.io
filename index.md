## Welcome to PJ Pages

### JNI学习

[JNI资料](https://zhuanlan.zhihu.com/p/25554150)

### Jython学习

#### 遇到的问题
1. Jython 2.7.1会遇到Error Loading Python DLL错误，通过Google查到的方法：更新VC2008不能解决问题，使用PyInstaller将jython.py生成jython.exe仍然不能解决问题。最后下载使用Jython 2.7.0解决问题。
2. 使用Jython在Java中调用Python代码，在Eclispse中只要将py文件放置在src目录下就可以引用到py文件实例化的类。如果出现No Module named错误，说明是类的路径或者类名错误，如果是Class cannot import错误，说明找到了类但不能正确导入，如果出现Exception In Thread Main, NotImplementError,说明找到了对应的class,但是class并没有正确实例化接口，有可能是自己的py文件中有方法名称写错了，Eclipse不会指明具体的错误。
3. 在Itellij IDEA中使用jython需要设置全局的python SDK,并且.py文件需要放置在resource目录(如果是gradle构建的)，gradle构建的项目引入Lib需要在build文件中引用，使用project Structure加入module dependence找不到依赖，在普通的JAVA project中，这种方式是可以的。
4. 在使用构建工具如gradle的项目中使用jython中的pythonInterpreter会遇到如下错误，需要想、添加pyInterpreter的初始化参数才可以。
```
ImportError: Cannot import site module and its dependencies:
             No module named site
```
```
#增加的初始化语句
+Properties props = new Properties();
+props.put("python.import.site", "false");
+Properties preprops = System.getProperties();
+PythonInterpreter.initialize(preprops, props, new String[0]);
PythonInterpreter interpreter = new PythonInterpreter();
interpreter.exec("from Building import Building");
buildingClass = interpreter.get("Building");
```
### git资料
中文版资料 http://gitbook.liuhui998.com/index.html

[中文版资料](https://github.com/PJdacainiao/pjpjpj.github.io/blob/master/index1.md)


### java学习
[为什么通过引用计数会产生循环引用，且发生循环引用时只能手动释放内存？](https://www.zhihu.com/question/21539353/answer/95667088)

