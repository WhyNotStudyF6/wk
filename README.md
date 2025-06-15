# wk
wk的库

import tkinter as tk

# ==============================
# 获取屏幕信息
# ==============================

def huoqu_pingmu_chicun():
    """获取屏幕尺寸"""
    chuangkou = tk.Tk()
    chuangkou.withdraw()
    kuan = chuangkou.winfo_screenwidth()
    gao = chuangkou.winfo_screenheight()
    chuangkou.destroy()
    return kuan, gao

PINGMU_KUAN, PINGMU_GAO = huoqu_pingmu_chicun()

# ==============================
# 创建基础窗口函数
# ==============================

def chuangjian_chuangkou(
    chuangkou_mingcheng="我的窗口",         # 窗口名称
    x_weizhi=100,                          # 窗口首次出现位置，以屏幕左上角为原点，x_weizhi、y_weizhi分别为窗口左上角横坐标、纵坐标。
    y_weizhi=100,                          
    moshi="百分比窗口大小",                 # 设置窗口大小的模式："自定义窗口大小" 或 "百分比窗口大小"
    kuan=800,                              # 自定义窗口大小模式下，窗口宽度
    gao=600,                               # 自定义窗口大小模式下，窗口高度
    baifenbi=0.5                           # 百分比窗口大小模式下，窗口大小占屏幕大小的百分比
):
    """
    创建基础窗口

    - 模式为 "自定义窗口大小"：窗口大小=kuan*gao
    - 模式为 "百分比窗口大小"：窗口大小 = 屏幕大小 * 百分比
    """
    win = tk.Tk()
    win.title(chuangkou_mingcheng)

    if moshi == "百分比窗口大小":
        kuan = int(PINGMU_KUAN * baifenbi)
        gao = int(PINGMU_GAO * baifenbi)

    win.geometry(f"{kuan}x{gao}+{x_weizhi}+{y_weizhi}")
    return win

# ==============================
# 示例用法（直接运行此模块时执行）
# ==============================

if __name__ == "__main__":
    # 示例：创建一个窗口，占屏幕60%，居中显示
    baifenbi = 0.6
    kuan = int(PINGMU_KUAN * baifenbi)
    gao = int(PINGMU_GAO * baifenbi)
    x = (PINGMU_KUAN - kuan) // 2
    y = (PINGMU_GAO - gao) // 2

    win = chuangjian_chuangkou(
        chuangkou_mingcheng="我的窗口",
        x_weizhi=x,
        y_weizhi=y,
        moshi="百分比窗口大小",
        baifenbi=baifenbi
    )

    win.mainloop()
