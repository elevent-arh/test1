# 饥荒简易数值修改教程
dont starve together的官方游戏代码是在data文件夹的databundles文件夹内

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20260311204757455.png" alt="image-20260311204757455" style="zoom: 40%;" />

打开databundles，解压scripts.zip，scripts文件夹下就是官方的源码，都是使用lua写的脚本文件

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20260311204900116.png" alt="image-20260311204900116" style="zoom:40%;" />

## 以女武神为例，修改武器奔雷长矛的属性

打开scripts文件夹，里面有很多文件

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20260311205233964.png" alt="image-20260311205233964" style="zoom:40%;" />

搜索spear（长矛）关键字，得到搜索结果

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20260311205333099.png" alt="image-20260311205333099" style="zoom:50%;" />

点开第一个spear_wathgrithr.lua文件就是官方的奔雷长矛定义

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20260311205542858.png" alt="image-20260311205542858" style="zoom: 50%;" />

if里面判断的是奔雷矛是否已升级（.upgradeable），是否命中有效目标（.IsValidVictim），nil相当于”无“，”空“或者”不存在“，doer.IsValidVictim ~= nil是判断.IsValidVictim是否存在避免调用不存在函数， TUNING.SPEAR_WATHGRITHR_LIGHTNING_CHARGED_MAX_REPAIRS_PER_LUNGE是官方定义的一次冲刺最多修复的耐久数（奔雷矛AOE伤害，一次冲刺可能命中多目标，所以定义了一次冲刺修复的耐久上限）

如果我想让未upgradeable的奔雷矛也能修复耐久，去掉红框中的条件就行

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20260311210833933.png" alt="image-20260311210833933" style="zoom:50%;" />

inst._cooldown = TUNING.SPEAR_WATHGRITHR_LIGHTNING_LUNGE_COOLDOWN定义了奔雷矛的技能冷却时间，直接在MOD里面使用cooltime覆盖就行
