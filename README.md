# github自动提交

利用github工作流，实现自动提交github项目，帮你点亮你的github

# github工作流代码
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
          git config --local user.email "meow@gemdzqq.com" 
          git config --local user.name "Meow"
          git remote set-url origin https://${{ github.actor }}:${{ secrets.GITHUB_TOKEN }}@github.com/${{ github.repository }}
          git pull --rebase
          ./random_commit.sh
          git push
```
