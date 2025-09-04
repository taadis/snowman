## 在macOS上构建Snowman的完整步骤

1.安装必要的依赖项

```zsh
# 安装Homebrew（如果尚未安装）
/bin/zsh -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 安装CMake和构建工具
brew install cmake

# 安装ATLAS的替代品
brew install ATLAS
# 安装OpenBLAS（ATLAS的替代品）
#brew install openblas

# 安装PulseAudio（用于音频应用程序）
brew install pulseaudio

# 安装Google Test（用于测试，可选）
brew install googletest
```

## 3.配置和构建项目

```zsh
cd /Users/taadis/roujia/snowman
mkdir build
cd build

# 配置CMake（使用Release模式以获得更好的性能）
cmake .. -DCMAKE_BUILD_TYPE=Release

# 构建项目
cmake --build . --config Release -j$(sysctl -n hw.logicalcpu)
```

## 4.验证构建结果

```zsh
# 检查是否成功生成了库文件
ls -la libsnowman.a  # 静态库
# 或者如果启用了共享库
# ls -la libsnowman.dylib

# 检查应用程序是否构建成功
ls -la enroll cut detect-live enroll-live 2>/dev/null || echo "应用程序可能需要额外配置"
```

## 5.运行测试（可选）

```zsh
# 运行单元测试
./test/snowboy-test
```
