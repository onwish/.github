## Hi there 👋

## GBS 本地开发设置

1. 访问 [gbs_deploy 的 local-dev 目录下 install.sh 脚本](https://github.com/onwish/gbs_deploy/blob/main/local-dev/install.sh) ,复制脚本文件.
   <img width="746" height="321" alt="image" src="https://github.com/user-attachments/assets/4ca935e7-ad21-43ff-85dc-8c0decc26bf5" />
   
2. 进入你的工作目录，比如 `/Users/sam/work`，创建 `install.sh` 文件，粘贴复制的脚本.
   
3. 运行刚创建的 `bash install.sh` 脚本。过程中会问你是否要 创建 **工作区目录 conviction-space** 及 **克隆所有仓库**，选择 `Y`；之后安装过程中，会询问是否要安装 **Python虚拟环境**，选择`Y` 会在工作区目录下创建 `venv` 并安装所有依赖。
   <img width="832" height="399" alt="image" src="https://github.com/user-attachments/assets/d17f4157-12db-4971-8a93-20bc2ca45f72" />

   <img width="804" height="238" alt="image" src="https://github.com/user-attachments/assets/647ad976-f402-4941-bad1-8aa6cef85541" />

   <img width="989" height="122" alt="image" src="https://github.com/user-attachments/assets/4a3617e8-f702-4422-a8f0-c77a7d25f69b" />
   
4. 完成后，检查 `/Users/sam/work/`**conviction-space**`/` 目录（这是就是工作区目录），里面结构如下. 且会软连接 `debug.py`（从 gbs_runtime) 和 `requirements.txt` (从 gbs_deploy) 到工作区目录。图中 `agent` 和 `gbs` 是我创建的软连接，指向原项目的 agent 和 gbs 目录，后面会删除.
  
   <img width="453" height="245" alt="image" src="https://github.com/user-attachments/assets/8bcbcb54-0afd-419b-8db0-1b08270ed463" />


5. 用 vscode 打开工作区目录下的 `gbs.code-workspace` 文件，会配置好 vscode.
   <img width="443" height="263" alt="image" src="https://github.com/user-attachments/assets/dcc98cef-2b81-49dc-bea9-fb945dcd7043" />


6. 将 `export PYTHONPATH=/Users/samuel/work/conviction-space:$PYTHONPATH` 加入到 `.bashrc` (bash) 或者 `.zshrc` (zshell) 末尾。

7. 在工作区目录(`~/work/conviction-space`) 下创建 `.env` 文件，文件内容如下（也可以复制原仓库的`.env`然后修改，注意最开始几个路径有变化）：
   ```
   DEBUG_MODE=true
   OUTPUTS_ROOT=/Users/samuel/work/conviction-space/outputs
   STRATEGY_ROOT=/Users/samuel/work/conviction-space/gbs_strategy_zoo
   
   # Execution Mode Configuration
   # Options: backtest | paper | live
   EXECUTION_MODE=backtest
   
   DB_TYPE=postgresql
   DB_USER=postgres
   DB_PORT=5432
   DB_PASSWORD=
   DB_HOST=
   DB_DATABASE=algotrading

   DATASVC_DB_DATABASE=datasvc
   
   # Data API Keys
   FMP_API_KEY=
   WRDS_USER=
   WRDS_PASSWORD=
   FACTSET_USERNAME=
   FACTSET_API_KEY=
   FACTSET_BASE_URL=https://api.factset.com
   SUPABASE_SERVICE_ROLE_KEY=
   FRED_API_KEY=
   
   # override all llm models.
   # LLM_MODEL=gpt-4o-mini
   
   LLM_CACHE=true
   
   # litellm used keys.
   OPENAI_API_KEY=
   ANTHROPIC_API_KEY=
   
   AWS_ACCESS_KEY_ID=
   AWS_SECRET_ACCESS_KEY=
   AWS_DEFAULT_REGION=us-east-1
   LITELLM_INFERENCE_PROFILE_ARN='arn:aws:bedrock:us-east-1:471112791150:inference-profile/us.anthropic.claude-sonnet-4-20250514-v1:0'
   
   
   ############### App Running ###############
   GBS_STORAGE_BACKEND=file          # 使用文件存储
   
   AXIOMA_DB_USER=postgres
   AXIOMA_DB_PASSWORD=
   AXIOMA_DB_HOST=
   AXIOMA_DB_PORT=5432
   AXIOMA_DB_NAME=axioma_test
   
   # Optional: Database connection pool settings
   DB_POOL_SIZE=5
   DB_MAX_OVERFLOW=10
   
   # GPS Application Database Configuration(For 业务场景)
   
   GBSAPP_DB_TYPE=postgresql
   GBSAPP_DB_USER=postgres
   GBSAPP_DB_PORT=5432
   GBSAPP_DB_PASSWORD=
   GBSAPP_DB_HOST=
   GBSAPP_DB_NAME=gbs_app
   
   GBS_REDIS_HOST=localhost
   GBS_REDIS_PORT=6379
   GBS_REDIS_PASSWORD=
   
   AWS_DEFAULT_REGION=us-east-1
   AWS_S3_ACCESS_KEY=
   AWS_S3_SECRET_ACCESS_KEY=
   AWS_S3_GBS_AGENT_LOGS_BUCKET=gbs-agent-logs
   
   ############### AWS Bedrock Anthropic ###############
   
   # 启用 Bedrock 集成
   CLAUDE_CODE_USE_BEDROCK=1
   AWS_REGION=us-east-1  # 或您首选的区域
   
   # 可选：覆盖小型/快速模型（Haiku）的区域
   ANTHROPIC_SMALL_FAST_MODEL_AWS_REGION=us-east-1
   ANTHROPIC_MODEL='us.anthropic.claude-sonnet-4-20250514-v1:0'
   ANTHROPIC_SMALL_FAST_MODEL='us.anthropic.claude-3-5-haiku-20241022-v1:0'
   
   AWS_BEARER_TOKEN_BEDROCK=
   
   ############### Other Settings ###############
   
   # Logging
   LOG_FORMATTER=colorful
   LOG_LEVEL=INFO
   LOG_COLOR_DEBUG=thin_white
   LOG_COLOR_INFO=white
   # LOG_SDK choices: python, logfire, loki
   LOG_SDK=python
   LOGFIRE_TOKEN=
   LOGFIRE_SERVICE_NAME=gbs
   LOGFIRE_SERVICE_VERSION=1.0.0
   LOGFIRE_ENVIRONMENT=
   
   ##############  personal env  ################
   
   http_proxy=http://127.0.0.1:1087
   https_proxy=http://127.0.0.1:1087

   ```
   
8. 运行：先进入工作区目录 `/Users/sam/work/conviction-space`；然后 `source venv/bin/active` 激活虚拟环境；运行 `python debug.py full` 全流程运行。

