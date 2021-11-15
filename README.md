# # iOS Xcode项目文件夹

## 1、一级目录文件如下
> 注意：Category、Tools、Base、Global中的文件除引用继承pod中文件外，不能引入其他模块文件，尽可能保持纯净和可移植

> AppDelegate 和Assets.xcassets、Plist等资源文件必须暴露在文件夹外，不可以嵌套在其他文件夹
```
├── MOJi
    ├── NetWork   （网络请求基类，各功能所属继承基类请放在MVVM同级别NetWork文件夹中）
    ├── Category  （分类文件夹）
        ├── UIKit     （UIkit所属分类）
        └── Foundation（Foundation所属分类）
    ├── Global        （Macro宏、全局配置、枚举、公共Key等文件）
    ├── Tools         （登陆、本地储存、跳转、等工具类文件，必须新建文件夹，文件命名避免无意义的命名，如：MCUserDefaultsTool，应该命名为：MCKaoChangUserDefaultTool or MCGlobalUserDefaultTool）
    
    ├── Resources     （不可以直接放资源文件，必须新建二级文件夹，如GIF、Voice、Json、Plist、Text、Other等，建议不超过5个文件夹                                                  夹）
    ├── CustomView    （自定义控件放置位置）
    ├── Base          （MVVM、Controller、View、Model等基类）
    └── Module      （各功能模块，如首页、我的、登陆、搜索等）
  
```


## 2、Business业务模块文件下文件目录规则：
> 1、原则上最多只允许设置三层文件层级，文件层级过多不利于查找文件和后期文件结构维护

> 2、最底层的文件夹必须符合：ViewController、View、ViewModel、Model、NetWork。此级文件夹中不允许再建文件夹，如果需要按功能 or 业务区分模块，请在上层文件夹中新建业务文件夹。

> ３、一级文件夹下的文件必须有明确的业务含义，不能取如：Common、Global、Main、Mine等无实际业务含义的名字（除View、Model、ViewModel等文件外）
```
├── Module
    ├── Home   (一级文件夹)
        ├── KaoChang (二级文件夹)
            ├── ViewController (三级文件夹)
            ├── View       （View & Layer等UI文件）
            ├── Cell       （Cell等UI文件）
            ├── ViewModel  （继承自MVVM或遵循MVVM协议的ViewModel文件）
            ├── Model      （继承自NSObject的文件）
            └── NetWorkApi（当前模块的请求管理者，需继承基类）
        ├── Kemu14
        └── Kemu23
    ├── Login
    ├── Mine
    ├── Practice
    └── Welcome 
```
#### 错误示例：

```
├── Business
    ├── Home   (一级文件夹)
        ├── KaoChang (二级文件夹)
            ├── Main
            ├── Common       （View & Layer等UI文件）
```
#### 你应该这样写：多业务命名需用下划线分割，遵循驼峰命名规则

```
├── Business
    ├── Home   (一级文件夹)
        ├── KaoChang (二级文件夹)
            ├── KaoChang_Main
            ├── KaoChang_Common       （View & Layer等UI文件）
```
## 3、各文件命名规则
> 1、ViewController、View、ViewModel、MVVMManager、Model、NetWork、Manager文件夹中文件命名规范

```
MVVMManager     （以MVVMManager结尾）
NetWork         （以NetWork结尾）
ViewController  （以ViewController Or Vc结尾）
View            （以View结尾，如JKXTDrivingVideoView）
Cell            （以Cell结尾，如JKXTDrivingVideoCell）
ViewModel       （以CellViewModel结尾，便于与数据Model区分）
Model           （以Model结尾，不可以ViewModel结尾）
NetWorkApi      （以Api结尾）
```
