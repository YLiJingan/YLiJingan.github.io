---
title: Shell  
comments: true   
tags: ['shell','学习笔记']
--- 
### Shell
#### 什么是Shell?
shell 是一个命令语言解释器（command-language interpreter）,简单来说就是一组linux命令的集合.
> Shell是你（用户）和Linux（或者更准确的说，是你和Linux内核）之间的接口程序。你输入的每个命令都由shell先解释然后传给Linux内核。

#### Shell分类
 * sh：Bourne Shell 的缩写。可以说是目前所有 Shell 的祖先。
 * bash：Bourne Again Shell 的缩写。因此说明 bash 是 sh 的一个进阶版本，比 sh 更优。bash 是目前大多数 Linux 发行版和苹果的 Mac OS X 操作系统的默认 Shell。
 * ksh：Korn Shell 的缩写。一般在收费的 Unix 版本上比较多见。
 * csh：C Shell 的缩写。 此 Shell 的语法有点类似 C 语言。
 * tcsh： Tenex C Shell 的缩写。csh 的优化版本。
 * zsh： Z Shell 的缩写。比较新近的一个 Shell，集 bash，ksh 和 tcsh 各家之大成。
 
 ***zsh优点***    
   * 完全兼容bash,之前的使用习惯可以继续使用 
   * 更强的的tab补全
	* 更智能的切换目录
	* 命令选项补齐
	* 命令参数补全
	* 可以定义丰富多彩的主题
	* 可以集成各种类型的插件
	
#### zsh
> 默认的 shell 是每个用户帐号的一个参数。Linux中典型的默认 shell是/bin/bash，不过也可以用其他的shell.

[zsh安装](https://github.com/robbyrussell/oh-my-zsh/wiki/Installing-ZSH),mac已经预装了zsh	
[oh my zsh安装](http://ohmyz.sh/)

`cat /etc/shells`     --查看系统有几种shell  
`echo $SHELL`			  -查看当前使用的shell   
`chsh`               --更换shell,change shell
