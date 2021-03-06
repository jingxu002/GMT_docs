命令行历史
==========

在使用多个命令绘制一张图时，这些命令可能使用了完全相同的标准选项参数，如果对于每个命令都需要把标准选项的参数写一遍，则太麻烦了，在这种情况下，GMT允许你省略标准选项的参数。例如::

    gmt psbasemap -JX10c/10c -R0/10/0/10 -B1 -K > text.ps
    gmt psxy station.dat -J -R -O >> text.ps

GMT每个命令在执行的时候，会将当前命令所使用的标准选项的参数保存到命令行历史文件 ``gmt.history`` 中，比如上面第一个命令指定了 ``-JX10c/10c -R0/10/0/10`` ，会生成如下内容::

    # GMT 5 Session common arguments shelf
    BEGIN GMT 5.1.2
    B   1
    J   X
    JX  X10c/10c
    R   0/10/0/10
    L   1
    END

在执行第二个命令时使用了 ``-J -R`` ，省略了具体的参数值，此时命令会读取 ``gmt.history`` 文件中需要的参数值。

抛开具体的细节不看，可以认为后面的命令继承了前面命令的标准选项参数，如果之后的命令显式指定了标准选项的参数，则后面命令中的参数会覆盖 ``gmt.history`` 中保存的值。

需要注意，如果在一个命令中通过管道或其他手段调用了多个GMT模块，GMT无法保证 ``gmt.history`` 文件是按照从左到右的顺序处理的。

.. important::

   命令历史这一特性看起来非常方便，但不建议依赖这一特性！建议将常用的标准选项的参数定义成变量使用。

.. source: http://gmt.soest.hawaii.edu/doc/5.3.1/GMT_Docs.html#command-line-history
