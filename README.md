```shell
# 系统环境 安装 uv pipreqs
pip install uv pipreqs
# 项目目录 初始化uv
uv init
# uv 创建 虚拟环境 指定使用的python版本
uv venv --python 3.9.9
# pipreqs 查找需要用到的依赖（不太好用，会有各种奇怪的依赖问题，不如手写） 
pipreqs ./ --encoding=utf-8 --force --savepath=requirements.txt
# uv安装 所需要的环境
uv pip install -r requirements.txt -i https://mirrors.aliyun.com/pypi/simple/

# 卸载所有 uv 临时环境中的包
uv pip freeze | xargs uv pip uninstall
# uv 清理缓存
uv clear
# uv 查看已经安装的列表
uv pip list

# 重构 pyproject.toml
rm -f requirements-locked.txt && \
uv pip compile requirements.txt -o requirements-locked.txt && \
rm -f pyproject.toml && \
uv init && \
.venv/bin/python ./convert_reqs_to_toml.py && \
rm -f requirements-locked.txt


```
2025.11.07
