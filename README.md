# chuangjian

一个中文友好的 Tkinter 简易窗口与控件库，适合初学者和中文用户快速开发桌面 GUI 程序。

## 安装

将 `chuangjian` 文件夹放入你的项目目录即可。

## 使用方法

### 1. 获取屏幕分辨率
```python
from chuangjian import huoqu_pingmu_fenbianlv

huoqu_pingmu_fenbianlv()  # 直接显示本机屏幕分辨率
```

### 2. 创建基础窗口
```python
from chuangjian.chuangjian_chuangkou import chuangjian_chuangkou

# 默认参数创建窗口（占屏幕50%，位置在100,100）
win = chuangjian_chuangkou()

# 自定义窗口
win = chuangjian_chuangkou(
    chuangkou_mingcheng="我的程序",    # 窗口标题
    x_weizhi=200,                      # 窗口左上角x坐标
    y_weizhi=150,                      # 窗口左上角y坐标
    moshi="自定义窗口大小",            # 可选："自定义窗口大小" 或 "百分比窗口大小"
    kuan=1024,                         # 窗口宽度
    gao=768,                           # 窗口高度
    baifenbi=0.7                       # 百分比模式时占屏幕比例
)
```

### 3. 添加按钮
```python
from chuangjian import chuangjian_anni

# 创建简单按钮
chuangjian_anni(win, wenzi="点我", x=50, y=50)

# 创建带功能的按钮
def dianji_anni():
    print("按钮被点击了！")

chuangjian_anni(win, wenzi="点我", mingling=dianji_anni, x=50, y=100)
```

### 4. 添加标签
```python
from chuangjian import chuangjian_biaoqian

chuangjian_biaoqian(win, wenzi="这是一个标签", x=50, y=150)
```

### 5. 添加输入框
```python
from chuangjian import chuangjian_shurukuang

shurukuang = chuangjian_shurukuang(win, x=50, y=200, kuan=20)  # kuan为输入框宽度
```

### 6. 显示消息弹窗
```python
from chuangjian import xianshi_xiaoxi

xianshi_xiaoxi(wenzi="这是一条消息", biaoti="提示")
```

## 完整示例

```python
from chuangjian import (
    chuangjian_chuangkou,
    huoqu_pingmu_fenbianlv,
    chuangjian_anni,
    chuangjian_biaoqian,
    chuangjian_shurukuang,
    xianshi_xiaoxi
)

# 显示本机屏幕分辨率
huoqu_pingmu_fenbianlv()  # 输出类似：本机屏幕分辨率：1920 x 1080

# 创建一个窗口
win = chuangjian_chuangkou()

# 在窗口中添加控件
chuangjian_biaoqian(win, wenzi="欢迎使用", x=50, y=30)
chuangjian_anni(win, wenzi="点我", mingling=lambda: xianshi_xiaoxi("你点击了按钮！"), x=50, y=70)
chuangjian_shurukuang(win, x=50, y=110)

# 显示窗口
win.mainloop()
```

## 主要模块

- chuangjian_chuangkou.py  基础窗口与屏幕分辨率
- chuangjian_anni.py       按钮控件
- chuangjian_biaoqian.py   标签控件
- chuangjian_shurukuang.py 输入框控件
- chuangjian_xiaoxikuang.py 消息弹窗

## 许可证

MIT 