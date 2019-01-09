# 3DEngineToolsBox使用手册

> 3DEngineToolsBox是引擎的二次封装,绝大部分api不需要再次封装直接调用即可（详见：[官方api](http://glendale.com.cn/template/default/Twodevelopment/api.html)），这里封装的是部分api，或为方便调用，或为将某些复杂组合封装起来,本次封装仅是个人见解可供参考，最终以官方api为准

1. [setSelectedModel - 加载模型（多个）](#setSelectedModel)
1. [setSelectedModelAndPath -加载模型-自定义子目录](#setSelectedModelAndPath)
1. [setSelectedModelWithUrl - 加载模型（拓展方法）-加载网络模型](#setSelectedModelWithUrl)
1. [removeMulModelsByIds - 移除模型(多个)](#removeMulModelsByIds)
1. [setModelAlpha - 设置多个模型半透明](#setModelAlpha)
1. [setModelIsAlpha - 设置模型是否半透明](#setModelIsAlpha)
1. [setModelVisibleLocal - 设置模型隐藏/显示](#setModelVisibleLocal)
1. [setModelWireFrame - 设置模型线框模式](#setModelWireFrame)
1. [setRenderMode - 模型渲染模式-光照、边框、材质](#setRenderMode)
1. [setRotateSpeed - 设置旋转速度](#setRotateSpeed)
1. [setPanSpeed - 设置平移速度](#setPanSpeed)
1. [setZoomSpeed - 设置缩放速度](#setZoomSpeed)
1. [showActorsOnly - 只特定构件显示](#showActorsOnly)
1. [setActorsColor - 批量设置模型构件颜色](#setActorsColor)
1. [resetActorsColor - 批量恢复模型构件颜色](#resetActorsColor)
1. [setActorsAlpha - 设置构件透明度](#setActorsAlpha)
1. [setActorsIsAlpha - 设置构件是否透明](#setActorsIsAlpha)
1. [setActorsVisible - 设置构件是否显示/隐藏](#setActorsVisible)
1. [resetActors - 构件状态恢复](#resetActors) 
1. [highLightActors - 构件高亮，高亮的构件永远处于渲染的最前端，别的构件挡不住](#highLightActors)
1. [resetHighLightActors - 清除构件高亮效果](#resetHighLightActors)
1. [setIsClick2ZoomTo - 是否开启点选构件时漫游到选中构件跟前](#setIsClick2ZoomTo)
1. [zoomToWhitDistance - 漫游](#zoomToWhitDistance)
1. [zoomTo - 漫游，漫游距离为之前通过setIsClick2ZoomTo()设置好的,没有设置则默认是1.0](#zoomTo)
1. [highlightGuidsRGB - 平站转换 模型半透明，高亮显示指定构件](#highlightGuidsRGB)
1. [highlightGuids - 平站转换 模型半透明，高亮显示指定构件(高亮色默认蓝色 #0000ff)](#highlightGuids)
1. [setClickMode - 设置点击模式](#setClickMode)
1. [setAutoCorrection - 设置测量点击点是否校正](#setAutoCorrection)
1. [addAnchor - 添加标签](#addAnchor)
1. [removeAnchor - 移除标签](#removeAnchor)
1. [setAnchorSize - 修改标签尺寸](#setAnchorSize)
1. [setAnchorVisible - 设置标签隐藏显示](#setAnchorVisible)
1. [getImage - 获取当前视点缩略图](#getImage)
1. [getCameraPosition - 获取视点](#getCameraPosition)
1. [setCameraPosition - 设置视点](#setCameraPosition)
1. [getCameraAndImage - 获取视点 和 当前视点缩略图](#getCameraAndImage)
1. [zoomFitAll - 模型恢复到初始状态-位置恢复默认](#zoomFitAll)
1. [playRoam - 漫游播放](#playRoam)
1. [setPlateClip - 裁剪](#setPlateClip)
1. [resetClip - 取消裁剪](#resetClip)
1. [setPopOut - 爆炸](#setPopOut)
1. [resetPopOut - 爆炸恢复](#resetPopOut)
1. [setActorsSelectSingleOrMultiple - 设置构件选择单选或多选](#setActorsSelectSingleOrMultiple)
1. [getSelectedGuids - 主动获取选中的构件](#getSelectedGuids)
1. [clearSelectedGuids - 清除之前已选中的构件ID](#clearSelectedGuids)
1. [resetModels - 模型整体恢复默认](#resetModels)
1. [setDebug - 设置是否debug模式](#setDebug)
1. [isDebug - 获取当前是debug模式还是release模式](#isDebug)

<span id = "setSelectedModel"></span>
## 加载模型（多个）
> setSelectedModel(json)

参数：
* `json` 把要加载的模型id和name做成特定格式的json串，例如：
``` json
[{"modelId":"661","modelName":"ZD_H_1F_S_0100"},{"modelId":"650","modelName":"ZD_H_1F_A_0000"}]
```

<span id = "setSelectedModelAndPath"></span>
## 加载模型-自定义子目录
> setSelectedModelAndPath(json, path)

参数：
* `json`把要加载的模型id和name做成特定格式的json串，例如：
``` json
[{"modelId":"661","modelName":"ZD_H_1F_S_0100"},{"modelId":"650","modelName":"ZD_H_1F_A_0000"}]
```
* `path` model文件夹下的一级目录，如果模型文件存放在根目录则为 "",如果分模块存放在不同子文件夹里，这里填写该子文件夹目录结构，例如：在model文件夹下有个model01的目录存放第一阶段的模型，则path为 "model01/"

<span id = "setSelectedModelWithUrl"></span>
## 加载模型（拓展方法）-加载网络模型
> setSelectedModelWithUrl(json)

参数：
* `json` 把要加载的模型id和name做成特定格式的json串， 例如：
``` json
[{"modelId": "20180930", "modelName": "http://117.34.118.8:9011/BIMsample/BIMsampleList.json"}]
```

<span id = "removeMulModelsByIds"></span>
## 移除模型(多个)
> removeMulModelsByIds(tags)

参数：
* `tags` 模型ID用 , 间隔,例如：removeMulModelsByIdsJson("661,650")

<span id = "setModelAlpha"></span>
## 设置多个模型半透明
> setModelAlpha(tags, alpha)

参数：
* `tags` 模型的标识id,多个“,”间隔
* `alpha` 为模型的透明度，取值范围0.0-1.0(0.0:代表隐藏；1.0：代表实体；值越小表示透明度约高);

<span id = "setModelIsAlpha"></span>
## 设置模型是否半透明
> setModelIsAlpha(tags, isAlpha)

参数：
* `tags` 模型的标识id,多个“,”间隔
* `isAlpha` true半透明（alpha=0.4） false不透明(alpha=1.0)

<span id = "setModelVisibleLocal"></span>
## 设置模型隐藏/显示
> setModelVisibleLocal(tags, isVisible)

参数：
* `tags` 模型的标识id,多个“,”间隔
* `isVisible` true 显示，false 隐藏

<span id = "setModelWireFrame"></span>
## 设置模型线框模式
> setModelWireFrame(tags, isWireFrame)

参数：
* `tags` 模型的标识id,多个“,”间隔
* `isWireFrame` true线框模式，false线框模式恢复

<span id = "setRenderMode"></span>
## 模型渲染模式-光照、边框、材质
> setRenderMode(tags, renderMode)

参数：
* `tags` 模型的标识id,多个“,”间隔
* `renderMode` 0光照模式 1边框模式 2材质模式（需新版本引擎和转换工具）

<span id = "setRotateSpeed"></span>
## 设置旋转速度
> setRotateSpeed(speed)

参数：
* `speed` 越大越快,默认1

<span id = "setPanSpeed"></span>
## 设置平移速度
> setPanSpeed(speed)

参数：
* `speed` 越大越快,默认1

<span id = "setZoomSpeed"></span>
## 设置缩放速度
> setZoomSpeed(speed)

参数：
* `speed` 越大越快,默认1

<span id = "showActorsOnly"></span>
## 只特定构件显示
> showActorsOnly(guids)

参数：
* `guids` 多个构件ID用“,”或“#”间隔

<span id = "setActorsColor"></span>
## 批量设置模型构件颜色
> setActorsColor(guids, r, g, b)

参数：
* `guids` 多个构件ID用“,”或“#”间隔
* `r` red通道 0-255
* `g` green通道 0-255
* `b` blue通道 0-255

<span id = "resetActorsColor"></span>
## 批量恢复模型构件颜色
> resetActorsColor(guids)

参数：
* `guids` 多个构件ID用“,”或“#”间隔

<span id = "setActorsAlpha"></span>
## 设置构件透明度
> setActorsAlpha(guids, alpha)

参数：
* `guids` 多个构件ID用“,”或“#”间隔
* `alpha` 透明度alpha通道 0.0-1.0

<span id = "setActorsIsAlpha"></span>
## 设置构件是否透明
> setActorsIsAlpha(guids, isAlpha)

参数：
* `guids` 多个构件ID用“,”或“#”间隔
* `isAlpha` true透明0.3 false不透明1.0

<span id = "setActorsVisible"></span>
## 设置构件是否显示/隐藏
> setActorsVisible(guids, isVisible)

参数：
* `guids` 多个构件ID用“,”或“#”间隔
* `isVisible` true显示 false隐藏

<span id = "resetActors"></span>
## 构件状态恢复
一般用于对构件做了颜色，透明，隐藏等设置后，调用此接口可以恢复到模型原始状态,引擎本不支持批量，这里恢复多个通过遍历实现
> resetActors(guids) 

参数：
* `guids` 多个构件ID用“,”或“#”间隔

<span id = "highLightActors"></span>
## 构件高亮
高亮的构件永远处于渲染的最前端，别的构件挡不住
> highLightActors(guids, r, g, b)

参数：
* `guids` 多个构件ID用“,”或“#”间隔
* `r` red通道 0-255
* `g` green通道 0-255
* `b` blue通道 0-255

<span id = "resetHighLightActors"></span>
## 清除构件高亮效果
> resetHighLightActors()

参数：
* 无

<span id = "setIsClick2ZoomTo"></span>
## 是否开启点选构件时漫游到选中构件跟前
> setIsClick2ZoomTo(isClick2ZoomTo, distance)

参数：
* `isClick2ZoomTo` true开启 false关闭
* `distance` 距离默认1.0，值越大镜头越远,相反,值越小镜头越近

<span id = "zoomToWhitDistance"></span>
## 漫游
> zoomToWhitDistance(guid, distance)

参数：
* `guid` 构件ID
* `distance` 控制远近,不传的时候默认为1.0，单位是浮点型，值越大镜头越远,相反,值越小镜头越近

<span id = "zoomTo"></span>
## 漫游，漫游距离为之前通过setIsClick2ZoomTo()设置好的,没有设置则默认是1.0
> zoomTo(guid)

参数：
* `guid` 构件ID

<span id = "highlightGuidsRGB"></span>
## 平站转换 模型半透明，高亮显示指定构件
> highlightGuidsRGB(guids,r,g,b)

参数：
* `guids` 指定的构件，多个可“,”或“#”间隔，如 “661_65282,661_65360” 或 “661_65282#661_65360” 
* `r` red通道 0-255
* `g` green通道 0-255
* `b` blue通道 0-255

<span id = "highlightGuids"></span>
##  平站转换 模型半透明，高亮显示指定构件(高亮色默认蓝色 #0000ff)
> highlightGuids(guid)

参数：
* `guid` 指定的构件，多个可“,”或“#”间隔，如 “661_65282,661_65360” 或 “661_65282#661_65360” 

<span id = "setClickMode"></span>
##  设置点击模式
> setClickMode(mode)

参数：
* `mode` 

        0:为查看模型,鼠标点击不响应任何事件；
        1:为坐标拾取模式,触发鼠标点击模型构件的碰撞点坐标事件；
        2:为ID拾取模式,触发鼠标点击模型构件拾取构件的ID值事件；
        3:为ID拾取+坐标拾取模式,触发鼠标点击模型构件拾取构件的ID值和坐标值事件；
        4:为距离测量模式,响应鼠标点击模型构件两点测距方法；
        5:为角度测量模式,响应鼠标点击模型构件三点测量角度方法；
        6:为平面面积测量模式,响应鼠标点击模型构件计算模型平面面积测量方法；
        7:为表面积测量模式,响应鼠标点击模型构件计算模型表面积测量方法；
        8:为体积测量模式,响应鼠标点击模型构件计算模型体积测量方法；
        9:为重量测量模式,响应鼠标点击模型构件计算模型重量测量方法；目前引擎设置密度为固定值，参数可以修改
        -1:设置模型旋转中心点模式（这个是附加组合的，坐标拾取模式下点击模型设置模型中心点）
        -2:设置构件隐藏（设置之后依次点击模型构件将依次隐藏，被隐藏的构件存在 mHidedGuids 里,如需恢复，从 mHidedGuids 里取出来做恢复操作：setActorsVisible(guids,true)）
        -3:设置构件透明（设置之后依次点击模型构件将依次透明，被透明的构件存在 mTransparentGuids 里,如需恢复，从 mHidedGuids 里取出来做恢复操作：setActorsIsAlpha(guids,false)）

<span id = "setAutoCorrection"></span>
##  设置测量点击点是否校正
> setAutoCorrection(isAuto)

参数：
* `isAuto` true 自动校正，false不校正，默认开启自动校正

<span id = "addAnchor"></span>
##  添加标签
> addAnchor(clickpos, imgPath, width, height, tag, bFront)

参数：
* `clickpos`  标签所在坐标
* `imgPath` 标签图片文件路径
* `width`  标签宽度
* `height`  标签高度
* `tag` tag标识，用于区分是哪个标签
* `bFront`  是否置前，true置前则别的面挡不住他，false不置前

<span id = "removeAnchor"></span>
##  移除标签
> removeAnchor(tag)

参数：
* `tag` tag标识，用于区分是哪个标签

<span id = "setAnchorSize"></span>
##  修改标签尺寸
> setAnchorSize(tag, width, height)

参数：
* `tag` tag标识，用于区分是哪个标签
* `width`  标签宽度
* `height`  标签高度

<span id = "setAnchorVisible"></span>
##  设置标签隐藏显示
> setAnchorVisible(tag, isVisible)

参数：
* `tag` tag标识，用于区分是哪个标签
* `isVisible`  true显示，false隐藏

<span id = "getImage"></span>
##  获取当前视点缩略图
> getImage()

参数：
* 无
返回：
* 缩略截图base64

<span id = "getCameraPosition"></span>
##  获取视点
> getCameraPosition()

参数：
* 无
返回：
* 视点坐标

<span id = "getCameraAndImage"></span>
## 获取视点 和 获取当前视点缩略图
> getCameraAndImage()

参数：
* 无
返回：
* 视点坐标&视图base64

<span id = "setCameraPosition"></span>
##  设置视点
> setCameraPosition(cameraPos)

参数：
* `cameraPos` 视点坐标

<span id = "zoomFitAll"></span>
##  模型恢复到初始状态-位置恢复默认
> zoomFitAll()

参数：
* `cameraPos` 视点坐标

<span id = "playRoam"></span>
##  漫游播放
> playRoam(positions, duration)

参数：
* `positions` 轨迹点 & 分割
* `duration` 播放时长 s

示例：
``` javascript
var positions = "47608.228759765625,141956.37109375,2900,0.7853981633974483,0,0.7853981633974483&50535.241721336846,76319.08603732027,4073.853990270034,0.7853981633974483,0,0.7853981633974483&50535.241721336846,76319.08603732027,4073.853990270034,0.5771689639327126,0,1.5931235845246516&52742.964850893644,52200.60833273884,8017.544399510898,0.5771689639327126,0,1.5931235845246516&52742.964850893644,52200.60833273884,8017.544399510898,0.2791009341783047,0,1.6317457704503433&51849.49230669129,32949.21168125819,8924.670588633562,0.2791009341783047,0,1.6317457704503433&51849.49230669129,32949.21168125819,8924.670588633562,0.2791009341783047,0,1.6317457704503433&51849.49230669129,32949.21168125819,8924.670588633562,0.18506313112414857,0,1.5897634223709975"
playRoam(positions,20)
```

<span id = "setPlateClip"></span>
##  裁剪
> setPlateClip(type, value)

参数：
* `type` 为裁剪的类型，类型分为'X-MIN'，'X-MAX'，'Y-MIN'，'Y-MAX'，'Z-MIN'，'Z-MAX'
* `value` 为裁剪的程度，值为0.0-1.0

<span id = "resetClip"></span>
##  取消裁剪
> resetClip()

参数：
* 无

<span id = "setPopOut"></span>
##  爆炸
> setPopOut(value)

参数：
* `value` 爆炸程度，0为不爆炸。每+1值爆炸距离离中心点越远

<span id = "resetPopOut"></span>
##  爆炸恢复
> resetPopOut()

参数：
* 无

<span id = "setActorsSelectSingleOrMultiple"></span>
##  设置构件选择单选或多选
> setActorsSelectSingleOrMultiple(isSingle)

参数：
* `isSingle` true单选，false多选，默认单选

<span id = "getSelectedGuids"></span>
##  主动获取选中的构件
> getSelectedGuids()

参数：
* 无

返回：
* 单选模式下只有一个，多选模式下会返回多个“,”间隔

<span id = "clearSelectedGuids"></span>
##  清除之前已选中的构件ID
> clearSelectedGuids()

参数：
* 无

<span id = "resetModels"></span>
## 模型整体恢复默认
> resetModels()

参数：
* 无

<span id = "setDebug"></span>
## 设置是否debug模式
> setDebug(debug)

参数：
* `debug` true:debug模式会输出日志，false:release模式不输出日志

<span id = "isDebug"></span>
## 获取当前是debug模式还是release模式
> isDebug()

参数：
* 无

返回：
* true:debug模式会输出日志，false:release模式不输出日志
