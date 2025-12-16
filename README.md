# 本地安装指南

https://blog.csdn.net/qq_53186375/article/details/136031876?fromshare=blogdetail&sharetype=blogdetail&sharerId=136031876&sharerefer=PC&sharesource=rozier&sharefrom=from_link

！注意osqp与osqp-eigen版本依赖问题，建议直接按照网址终端的参考链接1安装

# 虚拟手柄的使用
终端1
```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py cmd_vel:=/keyboard_twist
```
终端2
```
rosrun <your_package_name> twist_to_joy.py
```
ROS 话题通信流程：

键盘 (Publisher) →keyboard_twist​ 转换脚本 (Subscriber/Publisher) →joy​ A1 控制器 (Subscriber)

# 按键映射表

| 按键 | 运动方向 | 对应的 $\mathbf{Twist}$ 轴 | 变化值 | $\text{A1}$ 机器人控制用途 |
| :--- | :--- | :--- | :--- | :--- |
| **`i`** | 前进 | $\mathbf{linear.x}$ | $+ \text{x}$ (正值) | 主运动：对应 $\text{Joy axes[5]}$ |
| **`,`** | 后退 | $\mathbf{linear.x}$ | $- \text{x}$ (负值) | 主运动：对应 $\text{Joy axes[5]}$ |
| **`j`** | 左转 | $\mathbf{angular.z}$ | $+ \text{z}$ (正值) | 偏航/转向：对应 $\text{Joy axes[0]}$ |
| **`l`** | 右转 | $\mathbf{angular.z}$ | $- \text{z}$ (负值) | 偏航/转向：对应 $\text{Joy axes[0]}$ |
| **`u`** | 左前斜向 | $\mathbf{linear.x}$ ($\text{+}$) 和 $\mathbf{angular.z}$ ($\text{+}$) | 混合 | 混合运动 |
| **`o`** | 右前斜向 | $\mathbf{linear.x}$ ($\text{+}$) 和 $\mathbf{angular.z}$ ($\text{-}$) | 混合 | 混合运动 |
| **`m`** | 左后斜向 | $\mathbf{linear.x}$ ($\text{-}$) 和 $\mathbf{angular.z}$ ($\text{+}$) | 混合 | 混合运动 |
| **`.`** | 右后斜向 | $\mathbf{linear.x}$ ($\text{-}$) 和 $\mathbf{angular.z}$ ($\text{-}$) | 混合 | 混合运动 |
| **`k`** | **停止** | 所有轴 $\mathbf{0}$ | $\mathbf{0}$ | 停止运动 |

---

# 躯干高度控制 (垂直速度)

| 按键 | 运动方向 | 对应的 $\mathbf{Twist}$ 轴 | 变化值 | $\text{A1}$ 机器人控制用途 |
| :--- | :--- | :--- | :--- | :--- |
| **`t`** | **上升** | $\mathbf{linear.z}$ | $+ \text{z}$ (正值) | **躯干高度**：对应 $\text{Joy axes[1]}$ |
| **`b`** | **下降** | $\mathbf{linear.z}$ | $- \text{z}$ (负值) | **躯干高度**：对应 $\text{Joy axes[1]}$ |

---

# 速度调整和切换按键

| 按键 | 功能 | 描述 |
| :--- | :--- | :--- |
| **`q / z`** | 最大速度 | 增加 ($\text{q}$) 或减少 ($\text{z}$) **所有**最大速度限制 ($\text{10\%}$ 步长) |
| **`w / x`** | 线性速度 | 仅增加 ($\text{w}$) 或减少 ($\text{x}$) **线性**最大速度限制 ($\text{10\%}$ 步长) |
| **`e / c`** | 角速度 | 仅增加 ($\text{e}$) 或减少 ($\text{c}$) **角速度**最大限制 ($\text{10\%}$ 步长) |
| **按住 $\text{Shift}$** | Holonomic 模式 | 启用横向平移（侧移，映射到 $\mathbf{linear.y}$），但 $\text{A1}$ 控制器可能不使用这个轴。 |

