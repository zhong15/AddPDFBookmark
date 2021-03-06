# AddPDFBookmark
读取文本文件中的书签信息添加到 PDF 文件

- PDF 文件需要放置在 resources 目录下，且命名为 input.pdf
- 输出 PDF 文件在 dist/output.pdf
- 配置书签文件是 ```resources/bookmark.txt```

## ```resources/bookmark.txt``` 说明

- 第一行需留空行或输入一个正整数表示实际页码基数
- 级别使用 4 个空格缩进表示，0 个空格表示 1 级目录
- 标题与页码之间至少需要 1 个空格
- 页码后面不能再有空格

### 例子 1
```

标题1   1
    标题2   1
标题3   2
    标题4   2
        标题5   3
```

则输出书签如下：
| 级别 | 显示书签 | 跳转页码 |
| -- | -- | -- |
| 1 | 1 标题1 | 1 |
| 2 | 1.1 标题2 | 1 |
| 1 | 2 标题3 | 2 |
| 2 | 2.1 标题4 | 2 |
| 3 | 2.2 标题5 | 3 |

### 例子 2
```
99
标题1   1
    标题3   2
标题2   2
    标题4   3
        标题5   4
```

| 级别 | 显示书签 | 跳转页码 |
| -- | -- | -- |
| 1 | 1 标题1 | 100 |
| 2 | 1.1 标题2 | 100 |
| 1 | 2 标题3 | 101 |
| 2 | 2.1 标题4 | 101 |
| 3 | 2.2 标题5 | 102 |