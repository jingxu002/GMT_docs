macOS 下安装 GMT
================

macOS 下 GMT 的安装方法有很多，可以直接使用安装包，也可以使用各种软件管理工具。

推荐使用 homebrew 方式安装。

使用 homebrew 安装
------------------

`Homebrew <http://brew.sh/>`_ 是 macOS 下的第三方软件包管理工具。

1.  安装 Homebrew::

       $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

2.  安装 GMT::

       $ brew update && brew upgrade
       $ brew tap homebrew/science
       $ brew install gmt

3.  测试安装是否成功::

       $ gmt --version
       5.3.1

4.  如果你想要同时安装 GMT4 和 GMT5::

       $ brew unlink gmt && brew install gmt4

5.  从 GMT5 切换至 GMT4::

       $ brew unlink gmt && brew link gmt4

    从 GMT4 切换至 GMT5::

       $ brew unlink gmt4 && brew link gmt5

.. warning::

   以下几种安装方法翻译自官方文档，我们未作验证。

使用 GMT 安装包
---------------

GMT 为 macOS 用户提供了 dmg 安装包。

1. 到社区主页的 `下载页面 <http://gmt-china.org/download/>`_ 下载最新版本的 dmg 安装包。

2. 双击 dmg 包以解压，将解压得到的 ``GMT-5.3.1.app`` 拖动到 Applications 目录即可。

3. GMT 默认会安装到 ``/Applications/GMT-5.3.1.app/`` 目录下，将如下语句::

       export PATH=${PATH}:/Applications/GMT-5.3.1.app/Contents/Resources/bin

   加入到 ``~/.bashrc`` 中即可。

4. 测试安装是否成功::

       $ gmt --version
       5.3.1

使用 macports 安装
------------------

::

    sudo port install gdal +curl +geos +hdf5 +netcdf +fftw3 +openmp
    sudo port install gmt5


使用fink安装
------------

::

    sudo fink install gmt5
