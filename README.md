# github自动提交

## 利用github工作流，实现自动提交github项目，帮你点亮你的github
- 每天定时自动运行，按照设置的时间（如每天凌晨 0:00）执行。
- 根据随机概率控制提交（0-6 的概率），如果需要提交，则随机生成 1-3 个空提交（empty commit），并将其推送到 GitHub 仓库。
- 通过定时提交保持仓库的活跃度，让贡献图（GitHub Contributions Graph）不断更新。

## 使用方法
1. 把我的仓库fork到你自己的github项目，随便取个名字
2. 配置操作权限![4b77e3c90aadc4e545d58c7446d63936](https://github.com/user-attachments/assets/423feb69-9ac7-49d6-adec-ee8b3d031c55)
3. 配置读取和写入权限![4b77e3c90aadc4e545d58c7446d63936](https://github.com/user-attachments/assets/6c7ec8c2-b982-47e3-adab-c7b57ce46eca)
4. 配置提交者用户名和邮箱(！！！非常重要),前往.github/workflows/main.yml配置 ![11](./public/QQ_1735964816192.png)
5. 提交一次修改，看看是否成功

> [!CAUTION] 
>提交者的**邮箱**和**账号**必须配置成自己的，不然无法成功统计comiit，别到时候给别人提交commit了

