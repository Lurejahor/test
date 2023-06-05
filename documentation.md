
[toc]






## 接口函数



<div STYLE="page-break-after: always;"></div>

###  Oi_System_instance()

生成SDK系统实例，是构建程序的必需
**参数：** None

**返回值类型：** [Oi_System](#Oi_System)

**例子：**

```cpp
Oi_System system = Oi_System_instance();
```

<div STYLE="page-break-after: always;"></div>




### Oi_System_init(Oi_System system)

对生成的SDK系统初始化，才能调用其他SDK接口

**参数：** 
<table>
    <tr>
        <td>system</td> 
        <td>SDK系统</td> 
   </tr>
</table>


**返回值类型：** None

**例子：**

```cpp
Oi_System system = Oi_System_instance();
Oi_System_init(system);
```

<div STYLE="page-break-after: always;"></div>




### Oi_System_exit(Oi_System system)

程序退出时，释放SDK用到的所有系统资源

**参数：** 
<table>
    <tr>
        <td>system</td> 
        <td>SDK系统</td> 
   </tr>
</table>

**返回值：** None

**例子：**

```cpp
Oi_System system = Oi_System_instance();
Oi_System_init(system);

//proceeding

Oi_System_exit(system);
```

<div STYLE="page-break-after: always;"></div>




### Oi_System_count(system)

对初始化后的SDK系统计数，以便判断是否成功对SDK初始化

**参数：** 
<table>
    <tr>
        <td>system</td> 
        <td>SDK系统</td> 
   </tr>
</table>

**返回值：** int

**例子：**

```cpp
Oi_System system = Oi_System_instance();
Oi_System_init(system);

if (Oi_System_count(system) == 0)
{
    Oi_System_exit(system);
    return -1;
}
```

<div STYLE="page-break-after: always;"></div>


### （不理解）Oi_System_appendFindFolder(Oi_System system, const char* folder)


**参数：** 
<table>
    <tr>
        <td>system</td> 
        <td>SDK系统</td> 
   </tr>
   <tr>
        <td>folder</td> 
        <td>???</td> 
   </tr>
</table>

**返回值：** None

**例子：**

```cpp
```
<div STYLE="page-break-after: always;"></div>


### （不理解）Oi_System_removeFindFolder(Oi_System system, const char* folder)


**参数：** 
<table>
    <tr>
        <td>system</td> 
        <td>SDK系统</td> 
   </tr>
   <tr>
        <td>folder</td> 
        <td>???</td> 
   </tr>
</table>

**返回值：** None

**例子：**

```cpp
```
<div STYLE="page-break-after: always;"></div>





### Oi_System_driver(Oi_System system, const char* name)

通过SDK和相机厂家名称获取Driver对象实例

**参数：** 
<table>
    <tr>
        <td>system</td> 
        <td>SDK系统</td> 
   </tr>
   <tr>
        <td>name</td> 
        <td>相机厂家名称</td> 
   </tr>
</table>

**返回值：** [Oi_Driver](#Oi_Driver)

**例子：**

```cpp
Oi_Driver driver = Oi_System_driver(system, "OiSmart")；
```
<div STYLE="page-break-after: always;"></div>





### （合法性检查）Oi_System_driverAt(Oi_System system, int index)

通过SDK和Driver索引获取Driver对象实例

**参数：** 
<table>
    <tr>
        <td>system</td> 
        <td>SDK系统</td> 
   </tr>
   <tr>
        <td>index</td> 
        <td>Driver索引</td> 
   </tr>
</table>

**返回值：** [Oi_Driver](#Oi_Driver)

**例子：**

```cpp
Oi_Driver driver = Oi_System_driverAt(system, 0)；
```
<div STYLE="page-break-after: always;"></div>



### Oi_Driver_find(Oi_Driver driver)

查询本地是否存在对应驱动，驱动存在返回1，驱动不存在返回0

**参数：** 
<table>
    <tr>
        <td>driver</td> 
        <td>相机驱动</td> 
   </tr>
</table>

**返回值：** int

**例子：**

```cpp
    Oi_System system = Oi_System_instance();
    Oi_System_init(system);
    Oi_Driver driver = Oi_System_driverAt(system, 0)；
    if (Oi_Driver_find(driver) == 0)
    {
        Oi_System_exit(system);
        return -1;
    }
```
<div STYLE="page-break-after: always;"></div>






### Oi_Driver_count(Oi_Driver driver)

获取当前相机数量

**参数：** 
<table>
    <tr>
        <td>driver</td> 
        <td>相机驱动</td> 
   </tr>
</table>

**返回值：** int

**例子：**

```cpp
    Oi_System system = Oi_System_instance();
    Oi_System_init(system);
    Oi_Driver driver = Oi_System_driverAt(system, 0)；
    if (Oi_Driver_count(driver) == 0)
    {
        Oi_System_exit(system);
        return -1;
    }
```
<div STYLE="page-break-after: always;"></div>







### Oi_Driver_camera(Oi_Driver driver, const char* serial)

通过相机序列号获取相机实例

**参数：** 
<table>
    <tr>
        <td>driver</td> 
        <td>相机驱动</td> 
   </tr>
   <tr>
        <td>serial</td> 
        <td>相机序列号</td> 
   </tr>
</table>

**返回值：** [Oi_Camera](#Oi_Camera)

**例子：**

```cpp
    const char* serial = "GTC-0000000000";
    Oi_Camera camera = Oi_Driver_camera(driver, serial);
```
<div STYLE="page-break-after: always;"></div>






### （合法性检查）Oi_Driver_cameraAt(Oi_Driver driver, int index)

通过相机索引获取相机实例

**参数：** 
<table>
    <tr>
        <td>driver</td> 
        <td>相机驱动</td> 
   </tr>
   <tr>
        <td>index</td> 
        <td>相机索引</td> 
   </tr>
</table>

**返回值：** [Oi_Camera](#Oi_Camera)

**例子：**

```cpp
    Oi_Camera camera = Oi_Driver_cameraAt(driver, 0);
```
<div STYLE="page-break-after: always;"></div>







### Oi_Camera_type(Oi_Camera camera)

获取相机类型
**参数：** 
<table>
    <tr>
        <td>camera</td> 
        <td>相机实例</td> 
   </tr>
</table>

**返回值：** [Oi_CameraType](#Oi_CameraType)

**例子：**

```cpp
int type = Oi_Camera_type(camera);
```
<div STYLE="page-break-after: always;"></div>



### Oi_Camera_model(Oi_Camera camera)

获取相机型号
**参数：** 
<table>
    <tr>
        <td>camera</td> 
        <td>相机实例</td> 
   </tr>
</table>

**返回值：** const char*

**例子：**

```cpp
const char* model = Oi_Camera_model(camera);
```
<div STYLE="page-break-after: always;"></div>



### Oi_Camera_vendor(Oi_Camera camera)

获取相机厂家名称
**参数：** 
<table>
    <tr>
        <td>camera</td> 
        <td>相机实例</td> 
   </tr>
</table>

**返回值：** const char*

**例子：**

```cpp
const char* model = Oi_Camera_vendor(camera);
```
<div STYLE="page-break-after: always;"></div>



### Oi_Camera_serial(Oi_Camera camera)

获取相机序列号
**参数：** 
<table>
    <tr>
        <td>camera</td> 
        <td>相机实例</td> 
   </tr>
</table>

**返回值：** const char*

**例子：**

```cpp
const char* model = Oi_Camera_serial(camera);
```
<div STYLE="page-break-after: always;"></div>



### Oi_Camera_name(Oi_Camera camera)

获取相机名称
**参数：** 
<table>
    <tr>
        <td>camera</td> 
        <td>相机实例</td> 
   </tr>
</table>

**返回值：** const char*

**例子：**

```cpp
const char* model = Oi_Camera_name(camera);
```
<div STYLE="page-break-after: always;"></div>




### Oi_Camera_addr(Oi_Camera camera)

获取相机ip地址
**参数：** 
<table>
    <tr>
        <td>camera</td> 
        <td>相机实例</td> 
   </tr>
</table>

**返回值：** const char*

**例子：**

```cpp
const char* model = Oi_Camera_addr(camera);
```
<div STYLE="page-break-after: always;"></div>




### Oi_Camera_guid(Oi_Camera camera)

获取相机mac地址
**参数：** 
<table>
    <tr>
        <td>camera</td> 
        <td>相机实例</td> 
   </tr>
</table>

**返回值：** const char*

**例子：**

```cpp
const char* model = Oi_Camera_guid(camera);
```
<div STYLE="page-break-after: always;"></div>












## 变量类型


### Oi_System {#Oi_System}
**类型：** void*

### Oi_Driver {#Oi_Driver}
**类型：** void*

### Oi_Camera {#Oi_Camera}
**类型：** void*

### Oi_CameraType {#Oi_CameraType}

**类型：** enum

<table>
    <tr>
        <td>OI_Camera2D</td> 
        <td>2d相机</td> 
   </tr>
   <tr>
        <td>OI_Camera3D</td> 
        <td>3d相机</td> 
   </tr>
   <tr>
        <td>OI_Scanner</td> 
        <td>扫描仪</td> 
   </tr>
   <tr>
        <td>OI_Shotter</td> 
        <td>快照</td> 
   </tr>
</table>



