# Python pandas读写csv文件

## pandas.read_csv函数

```python
pandas.read_csv(filepath_or_buffer,
 				sep=', ', 
 				usecols=None, 
 				engine=None, 
                header='infer',
                skiprows=None,
                nrows=None, 
                skipfooter=0
               )


```

- `filepath_or_buffer`：可以是一个URL或者本地文件。有效的URL包括http，ftp，s3和文件。也可以是本地文件：table.csv（在本机的绝对地址）。
- `sep`：分隔符。如果sep为None，那么C引擎不会自动检测到分隔符，但是Python解释器可以使用，这意味着后者将被使用，并通过Python的内置嗅探工具csv.Sniffer自动检测分隔符。 另外，长度超过1个字符且与’\ s +‘不同的分隔符将被解释为正则表达式，并且还将强制使用Python解释器。 请注意，正则表达式分隔符很容易忽略带引号的数据。 正则表达式示例：’\ r \ t’
- `usecols`：返回列的一个子集。 如果是数组的，所有元素必须是位置索引的（即文档列中的整数索引），或者是与由用户提供的名称或从文档标题行推断的列名相对应的字符串。 例如，有效的类似数组的usecols参数应该是[0,1,2]或[‘foo’，‘bar’，‘baz’]。如果可调用，则可调用函数将根据列名进行评估，返回可调用函数评估为True的名称。 一个有效的可调用参数的例子是[‘AAA’，‘BBB’，‘DDD’]中的lambda x：x.upper（）。 使用此参数可以缩短解析时间并降低内存使用量。
- `header`：指定第几行来作为列名，默认是数据最开始的那一行。如果文件中没有列名，则默认为0，否则设置为None。如果明确设定header=0就会替换掉原来存在列名。header参数可以是一个list例如：[0,1,3]，这个list表示将文件中的这些行作为列标题（意味着每一列有多个标题），介于中间的行将被忽略掉（例如本例中的2；本例中的数据1,2,4行将被作为多级标题出现，第3行数据将被丢弃，dataframe的数据从第5行开始。）。 注意：如果skip_blank_lines=True 那么header参数忽略注释行和空行，所以header=0表示第一行数据而不是文件的第一行。
- `skiprows`：list-like，int或callable，optional 要在文件开头跳过
  （0索引）或要跳过的行数（int）的行号。 如果是可调用的，则将根据行索引计算可调用函数，如果应该跳过该行则返回True，否则返回False。
  有效可调参数的一个例子是[0,2]中的lambda x：x。
- `nrows`：int，可选 要读取的文件行数。用于读取大文件。
- `engine`：使用的解释器。{‘c’, ‘python’}二选一。
- `skipfooter`：文件底部要跳过的行数（不支持引擎=‘c’）


