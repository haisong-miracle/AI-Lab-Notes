# Linux 常用命令速查

> 环境：WSL2 + Ubuntu ｜ 整理自 Task 03 的实际操作

## 一、目录与文件

| 命令 | 作用 | 用法示例 |
| :--- | :--- | :--- |
| `pwd` | 显示当前目录 | `pwd` |
| `cd` | 切换目录 | `cd ~/my_task03` |
| `ls` | 列目录 | `ls -l` / `ls -R` / `ls -a` |
| `mkdir` | 建目录 | `mkdir -p a/b/c` |
| `cp` | 复制 | `cp -r 目录1 目录2` |
| `mv` | 移动 / 重命名 | `mv a.txt b.txt` |
| `rm` | 删除（无回收站） | `rm -r 目录` |
| `cat` | 输出全文 | `cat app.log` |
| `head` / `tail` | 取头 / 尾 | `head -5 x.log` / `tail -f x.log` |
| `find` | 按条件查找 | `find . -name "*.log"` |

## 二、文本过滤与重定向

```bash
grep "ERROR" app.log > error_only.log    # 过滤并写入新文件（覆盖）
grep -c "ERROR" app.log                  # 统计命中行数
grep "ERROR" app.log | wc -l             # 管道 + 计数
cat app.log | grep ERROR | tail -2       # 读全文 → 过滤 → 取末尾
```

| 符号 | 含义 |
| :--- | :--- |
| `>` | 覆盖写入，原内容清空 |
| `>>` | 追加到末尾 |
| `\|` | 管道，前一个命令的输出作为后一个的输入 |

## 三、进程与系统状态

```bash
ps aux | head -10        # 进程快照
ps aux | grep bash       # 按关键字筛进程
sleep 300 &              # 后台运行，打印作业号
kill %1                  # 按作业号终止
kill -9 <PID>            # 按 PID 强制终止
df -h                    # 磁盘空间
free -m                  # 内存（MB）
top                      # 实时监控，q 退出
```

## 四、权限

| 数字 | 含义 | 典型场景 |
| :--- | :--- | :--- |
| `644` | 属主读写，他人只读 | 普通文档 |
| `755` | 属主全权，他人可读可执行 | 脚本、目录 |
| `600` | 仅属主读写 | 密钥、密码文件 |

```bash
chmod 600 secret.txt     # 权限位 4=读 2=写 1=执行
chmod +x run.sh          # 添加执行权限
sudo chown $USER:$USER file   # 修改属主
```

> 注意：`/mnt/` 下是 Windows 文件系统映射，**不保存 Linux 权限位**，在那里执行 `chmod` 会静默失效。

## 五、批量操作

```bash
# 批量改名：draft_1.txt → app_1.txt
for f in draft_*.txt; do mv "$f" "app_${f#draft_}"; done

# 批量改扩展名：.txt → .log
for f in *.txt; do mv "$f" "${f%.txt}.log"; done
```

| 语法 | 含义 |
| :--- | :--- |
| `${f#前缀}` | 从左侧删除最短匹配的前缀 |
| `${f%后缀}` | 从右侧删除最短匹配的后缀 |
