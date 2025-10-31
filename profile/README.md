## Hi there 👋

## GBS 本地开发设置

1. 访问 [gbs_deploy 的 local-dev 目录下 install.sh 脚本](https://github.com/onwish/gbs_deploy/blob/main/local-dev/install.sh) ,复制脚本文件.
   
2. 进入你的工作目录，比如 `/Users/sam/work`，创建 `install.sh` 文件，粘贴复制的脚本.
   
3. 运行刚创建的 `install.sh` 脚本。过程中会问你是否要 创建 **工作区目录 conviction-space** 及 **克隆所有仓库**，选择 `Y`；之后安装过程中，会询问是否要安装 **Python虚拟环境**，选择`Y` 会在工作区目录下创建 `venv` 并安装所有依赖。
   
4. 完成后，检查 `/Users/sam/work/`**conviction-space**`/` 目录（这是就是工作区目录），里面结构如下. 且会软连接 `debug.py`（从 gbs_runtime) 和 `requirements.txt` (从 gbs_deploy) 到工作区目录。
   
5. 用 vscode 打开工作区目录下的 `gbs.code-workspace` 文件，会配置好 vscode.

6. 运行：先进入工作区目录 `/Users/sam/work/conviction-space`；然后 `source venv/bin/active` 激活虚拟环境；运行 `python debug.py full` 全流程运行。
