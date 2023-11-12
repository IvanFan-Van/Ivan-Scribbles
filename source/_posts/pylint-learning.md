---
title: 快速入门Pylint
date: 2023-11-12 11:26:48
tags:
---

# 快速入门 Pylint

## 如何下载 Pylint

```bash
pip install pylint
```

使用该命令来安装 pylint

## 使用 pylint

```bash
pylint <filename>
```

可以运行`pyling <filename>` 来分析某个 Python 文件, 并生成一个报告. 这个报告会包含 Pylint 发现的任何问题, 以及你的代码的总体评分.

例如想分析一个名为`main.py` 的文件, 可以运行:

```bash
pylint main.py
```

报告长这个样子捏:

![image-20231110000600341](image-20231110000600341.png)

<!-- {% asset_img image-20231110000600341.png %} -->

跟着这些分析修改代码后, 可以再次运行 **Pylint**. 它会重新生成一个分析报告, 并告诉你的分数以及提升呢. 具体报告如下:
![image-20231110001113096](image-20231110001113096.png)

<!-- {% asset_img image-20231110001113096.png %} -->

如果你在 VSCode 中安装了**Pylint 插件**, 那么**Pylint**就会在你每次保存文件后**自动运行**, 并将问题全部**高亮**出来.

## 常见的 Pylint 错误：

1. `invalid-name`: 变量、函数、类或模块的名称不符合默认的命名约定。例如，使用小写字母和下划线命名函数，使用驼峰命名法命名类。

2. `missing-docstring`: 函数、类或模块缺少文档字符串。(三对双引号括起来的注释就是 docstring 啦)

   ```python
   """
   我是一个docstring, 在三对双引号里
   """
   ```

3. `unused-variable`: 定义了一个变量但没有使用它。

4. `unused-argument`: 函数的参数没有在函数体中使用。

5. `redefined-outer-name`: 在内部作用域中重新定义了一个在外部作用域（全局作用域、类级别等）已定义的名称。

6. `import-error`: 无法导入一个模块或包。

7. `no-member`: 尝试访问一个对象的成员，但是这个成员不存在。

8. `no-name-in-module`: 尝试从一个模块导入一个不存在的名称。

9. `wrong-import-position`: 导入语句的位置不正确。按照 PEP8，所有的导入语句应该在模块的顶部。

10. `wildcard-import`: 使用通配符导入一个模块的所有名称。

## 配置 Pylint

你还可以自定义 Pylint 的行为，通过在项目的根目录下创建一个`.pylintrc`文件，然后在其中添加你的配置.

```python
.pylintrc

[MASTER]
# Pylint搜索模块的路径。
init-hook='import sys; sys.path.append("/path/to/your/module")'

[MESSAGES CONTROL]
# 禁用特定的警告和错误。
disable=bare-except,invalid-name,missing-docstring, wildcard-import

[FORMAT]
# 设置期望的缩进字符串，例如空格或制表符。
indent-string='    '

# 设置一行的最大字符数。
max-line-length=100

[BASIC]
# 设置期望的函数名样式，例如snake_case或camelCase。
function-naming-style=snake_case

# 设置期望的常量名样式，例如UPPER_CASE或camelCase。
const-naming-style=UPPER_CASE

[DESIGN]
# 设置函数或方法的最大行数。
max-function-length=50

# 设置类的最大行数。
max-class-length=100
```

Pylint 还提供了许多其他选项来控制其行为. 你可以在[Pylint 的文档](https://pylint.pycqa.org/en/latest/user_guide/configuration/all-options.html) 中找到完整的选项列表
