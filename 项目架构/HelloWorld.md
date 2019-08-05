# beegoApi工程项目

---

## 初始化

1. ### 创建项目

   ```
   bee api beegoApi  // $GOPATH/src下执行该命令,简单生成一个api项目
   ```
2. ### API目录结构

   ![](/assets/beegoApi_dir.png)

3. #### 运行

   ```
   bee run  // 运行,如果提示cannot find package "github.com/shiena/ansicolor",安装一下即可
   ```

## 打印Hello World

1. ### 示例

   #### ./beegoApi/routers/router.go 文件中的init方法中,用namespace方式注册控制器MainController：

   ```
   beego.NSNamespace("/main",
   	beego.NSInclude(
   		&controllers.MainController{},
   	),
   ),
   ```

   #### 创建新的控制器文件：./beegoApi/controllers/main.go：

   ```
   package controllers

   import (
   	"github.com/astaxie/beego"
   )

   // Operations about main
   type MainController struct {
   	beego.Controller
   }

   // @router /hello {get}
   func (m *MainController) Hello() {
   	m.Data["json"] = "Hello World!"
   	m.ServeJSON()
   }
   ```

   #### 最后访问:[http://localhost:8080/v1/main/hello](http://localhost:8080/v1/main/hello) 即可。



