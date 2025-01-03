# github自动提交

利用github工作流，实现自动提交github项目，帮你点亮你的github

## github工作流代码
```bash
name: Sang
on:

  workflow_dispatch:

  push:
    branches:
      - main
  schedule:
    - cron: "0 0 * * *" # 每天的 0:00 执行

jobs:
  autogreen:
    runs-on: ubuntu-latest
    steps:
      - name: Clone repository
        uses: actions/checkout@v4

      - name: Setup random commit script
        run: |
          echo '#!/bin/bash' > random_commit.sh
          echo 'RANDOM_NUM=$((0 + RANDOM % 3))' >> random_commit.sh
          echo 'for i in $(seq 1 $RANDOM_NUM); do' >> random_commit.sh
          echo '  git commit --allow-empty -m "Sang Meow"' >> random_commit.sh
          echo 'done' >> random_commit.sh
          chmod +x random_commit.sh

      - name: Auto commit with random number
        run: |
          git config --local user.email "此处填写你的email" 
          git config --local user.name "此处填写你的用户名"
          git remote set-url origin https://${{ github.actor }}:${{ secrets.GITHUB_TOKEN }}@github.com/${{ github.repository }}
          git pull --rebase
          ./random_commit.sh
          git push
```

## 使用方法
1. 创建个公开仓库，随便填一点屎
2. 配置操作权限![4b77e3c90aadc4e545d58c7446d63936](https://github.com/user-attachments/assets/423feb69-9ac7-49d6-adec-ee8b3d031c55)
3. 配置读取和写入权限![4b77e3c90aadc4e545d58c7446d63936](https://github.com/user-attachments/assets/6c7ec8c2-b982-47e3-adab-c7b57ce46eca)
4. 把**github工作流代码**导入到github Actions中，提交
5. 测试是否成功


