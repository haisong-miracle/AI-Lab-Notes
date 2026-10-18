# AI-Lab 通识学习计划与环境踩坑记录

## 一、我的学习计划与目录体系
- [x] 1. 环境配置（已完成 Task 01）
- [x] 2. 排错记录（记录踩坑经验）
- [x] 3. 代码实验（测试 AI 生成的代码）
- [ ] 4. 文献/技术摘记（后续补充）

## 二、环境踩坑记录（表格）
在搭建现代 AI 编程环境时，遇到了一些问题，记录如下：

| 问题现象 | 原因分析 | 解决办法 |
| :--- | :--- | :--- |
| GitHub 网页打不开 | 国内网络环境 DNS 污染 | 使用 Watt Toolkit 加速 |
| 终端提示找不到 npm 命令 | 电脑未安装 Node.js | 下载 Node.js 并勾选 Add to PATH |
| OpenCode 配置报错 | 配置文件格式不对或缺少 Key | 仔细检查 opencode.json 语法 |

## 三、代码实验（代码块语法高亮）
在终端测试 OpenCode 时，让它写了一段 Python 的快速排序代码：

```python
def quicksort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quicksort(left) + middle + quicksort(right)

# 测试运行
print(quicksort([3, 6, 8, 10, 1, 2, 1]))
 ```
四、环境截图（本地图片引用）
 
以下是配置成功后的界面截图：
 
![环境截图](env.png)。
 
五、外部参考链接与公式（LaTeX基础）
- 参考链接：[Markdown 官方基础语法教程](https://www.markdownguide.org/basic-syntax/)
- 数学公式测试：当 $a \neq 0$ 时，方程 $ax^2 + bx + c = 0$ 的解为 $x = \frac{-b \pm \sqrt{b^2-4ac}}{2a}$。