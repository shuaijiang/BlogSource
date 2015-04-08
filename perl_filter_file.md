title: Perl过滤、复制文件
date: 2014-10-16 09:57:26
tags: Perl
---

#功能
从指定的目录中，根据文件列表，将文件复制到指定的目录中。

注意：文件列表没有指定文件后缀，输入参数中要指定文件后缀。

#核心部分：复制文件
##样例（demo）
	use File::Copy;
	copy("sourcefile","destinationfile") or die "Copy failed: $!";
##介绍（description）
copy函数需要两个参数:复制源文件和复制目标文件。每个参数都可以是字符串，也可以是文件句柄引用或者文件句柄。

原文：（[http://perldoc.perl.org/File/Copy.html](http://perldoc.perl.org/File/Copy.html)）


#代码
源代码文件下载：[https://github.com/shuaijiang/PerlScript/blob/master/filter.pl](https://github.com/shuaijiang/PerlScript/blob/master/filter.pl)

    #!/bin/perl
	#This Perl script is copy files from given source directory to 
	#given target directory according to given scp
	
	#Author: shuaijiang
	#Email: zhaoshuaijiang8@gmail.com
	use strict;
	use File::Copy;
	
	if($#ARGV != 3)
	{
		print "Usage: perl file.pl scp source_path target_path suffix\n";
		exit;
	}
	my $scp = $ARGV[0];
	my $source_path = $ARGV[1];
	my $target_path = $ARGV[2];
	my $suffix = $ARGV[3];
	
	open(SCP,"<$scp") or die "Can't open $!\n";
	while (<SCP>) {
		chomp;
		my $file = $_;
		my $source_file = $source_path . '/' . $file . $suffix;
		my $target_file = $target_path . '/' . $file . $suffix;
		print "source_file=$source_file target_file=$target_file\n";
		copy("$source_file","$target_file") or die "Copy file failed!\n";
	}
	close(SCP);
