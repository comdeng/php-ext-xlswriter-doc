# Windows

## 方式一：下载 DLL

1. [GitHub Release](https://github.com/viest/php-ext-xlswriter/releases)
2. [PECL](https://pecl.php.net/package/xlswriter)

## 方式二：编译安装

### 搭建PHP编译环境

详见 [php.net](https://wiki.php.net/internals/windows/stepbystepbuild)

### 安装依赖

```bash
cd PHP_BUILD_PATH/deps

DownloadFile http://zlib.net/zlib-1.2.11.tar.gz

7z x zlib-1.2.11.tar.gz > NUL
7z x zlib-1.2.11.tar > NUL

cd zlib-1.2.11

cmake -G "Visual Studio 14 2015" -DCMAKE_BUILD_TYPE="Release" -DCMAKE_C_FLAGS_RELEASE="/MT"
cmake --build . --config "Release"
```

### 编译扩展

```bash
cd PHP_PATH/ext

git clone https://github.com/viest/php-ext-excel-export.git

cd php-ext-excel-export

git submodule update --init

phpize

configure.bat --with-xlswriter --with-extra-libs=PATH\zlib-1.2.11\Release --with-extra-includes=PATH\zlib-1.2.11

nmake
```

