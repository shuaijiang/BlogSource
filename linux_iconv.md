title: Linux系统环境下使用iconv实现文件编码格式的转换
date: 2015-03-31 22:30:25
tags: Linux
---
#简介
Linux系统环境下，有很多处理文件编码格式的方法，比如vim中，使用“set fileencoding=utf-8”可以实现编码格式到UTF8格式的转换。但是个人觉得iconv更加好用些，下面就介绍下如何使用。

#iconv使用方法
下面是iconv的使用方法，比较重要的参数就是 “-f”：给出输入文件的编码格式，比如GBK； “-t”：指定输出文件的编码格式； “-o”：指定输出文件的文件名。
<!--more-->

	Usage: iconv [OPTION...] [FILE...]
	Convert encoding of given files from one encoding to another.
	
	 Input/Output format specification:
	  -f, --from-code=NAME       encoding of original text
	  -t, --to-code=NAME         encoding for output
	
	 Information:
	  -l, --list                 list all known coded character sets
	
	 Output control:
	  -c                         omit invalid characters from output
	  -o, --output=FILE          output file
	  -s, --silent               suppress warnings
	      --verbose              print progress information
	
	  -?, --help                 Give this help list
	      --usage                Give a short usage message
	  -V, --version              Print program version
	
	Mandatory or optional arguments to long options are also mandatory or optional
	for any corresponding short options.
	
	For bug reporting instructions, please see:
	<http://www.gnu.org/software/libc/bugs.html>.


#Examples
如何确定文件的格式呢，使用“file”来查看文件的编码格式，比如：
	file train.data

举个例子，一个编码格式为GBK的文件train.data，如果要对该文件转换成UTF8格式的文件，可以这样来实现：
	
	iconv -f GBK -t UTF-8 train.data -o train_utf8.data
