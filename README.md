## 🚀 danmu_api 自动同步部署方案 - 永远保持最新版本！

### ✨ 核心优势：实时同步原作者更新
**本方案的最大价值不仅仅是部署，而是让你的弹幕 API 服务始终与原作者保持同步！**

🔄 **自动同步机制**：每天自动拉取原作者的最新代码更新  
⚡ **零配置成本**：功能已内置，只需启用即可，无需手动创建任何文件  
🛡️ **稳定可靠**：基于 GitHub Actions + Vercel 的成熟方案  
📈 **持续改进**：自动获得原作者的功能优化和 bug 修复  

### 💡 为什么选择这个方案？
- **传统部署方式**：需要手动关注原项目更新，手动合并代码，容易遗漏重要更新
- **我们的方案**：功能已内置，只需启用即可！原作者每次更新都会自动同步到你的服务

参考项目：[`huangxd-/danmu_api`](https://github.com/huangxd-/danmu_api)

---

### 📋 完整流程目录
- 前置准备
- 第一步：Fork 原作者项目
- 第二步：部署到 Vercel
- **第三步：配置自动同步（核心功能）**
- 第四步：优化配置（可选）
- 常见问题（FAQ）

---

### 前置准备
- 一个 GitHub 账号
- 一个 Vercel 账号（将使用 GitHub 登录）

---

### 第一步：Fork 原作者项目
1. 打开上游仓库：[`huangxd-/danmu_api`](https://github.com/huangxd-/danmu_api)

![Fork步骤1](images/step-01-fork.png)

2. 点击右上角的 Fork，将仓库 Fork 到你自己的账号下。

![Fork步骤2](images/step-02-fork.png)

> 参考：仓库主页包含 Vercel/Cloudflare/Docker 等多种部署方式；本指南仅覆盖 Vercel 流程。

---

### 第二步：部署到 Vercel
1. 打开 Vercel 登录页：[`https://vercel.com/login`](https://vercel.com/login)，使用 GitHub 账号登录。

![Vercel登录](images/step-03-vercel-login.png)

2. 在 Vercel 仪表盘选择 Add New Project（新增项目）。

![新增项目](images/step-04-vercel-new-project.png)

3. 导入你刚 Fork 的仓库（通常名为 `danmu_api`）。

![导入仓库](images/step-05-vercel-import.png)

4. 点击Deploy按钮即可完成部署。部署完成后将得到形如 `https://{your_project}.vercel.app` 的访问地址。

![部署按钮](images/step-06-vercel-deploy.png)

---

### 🎯 第三步：启用自动同步（核心功能！）
**好消息！** 自动同步功能现已内置在原项目中，你无需手动创建任何文件！通过 GitHub Actions 实现每天自动拉取上游 `huangxd-/danmu_api` 的最新更新，确保你的弹幕 API 服务始终保持最新状态。

**同步机制说明**：
- 📅 每天午夜自动检查原作者是否有新的代码更新
- 🔄 发现更新时自动合并到你的 Fork 仓库
- 🚀 合并完成后自动触发 Vercel 重新部署
- ✅ 整个过程完全自动化，无需人工干预

#### 启用步骤（超简单！）

1. 打开你 Fork 后的 GitHub 仓库，进入 `Actions`。

![进入Actions](images/step-07-action.png)
![进入Actions](images/step-08-action.png)
![进入Actions](images/step-09-action.png)

2. 点击 "I understand my workflows, go ahead and enable them"。

![启用工作流](images/step-10-action.png)

3. 启用后，你会看到一个名为 "Fork Sync" 的工作流已经存在！点击它。

4. 点击 "Run workflow" 手动运行一次来验证同步功能是否正常。

![运行工作流](images/step-14-action.png)

5. 若成功，每日将自动同步上游更新；同步后 Vercel 会基于你 Fork 的仓库自动重新部署。

#### 🎉 恭喜！自动同步已配置完成
从现在开始，你的弹幕 API 服务将享受以下优势：
- ✨ **自动获取新功能**：原作者添加新的弹幕源支持时，你的服务会自动更新
- 🐛 **自动修复 bug**：原作者修复的任何问题都会自动同步到你的服务
- 🚀 **性能优化自动应用**：原作者的性能改进会自动让你的服务受益
- 📱 **API 接口自动升级**：新的 API 功能和改进会自动部署到你的服务
- 🔧 **零维护成本**：无需关注原项目动态，无需手动更新代码

---

### 第四步：优化配置（可选）
#### 禁用原作者用于 Docker 的 Workflow
> 💡 **说明**：不做这一步可能会在邮箱中收到报错提示，但不影响弹幕 API 的正常运行
上游有用于自动构建 Docker Hub 镜像的工作流；若你不需要，可在你的 Fork 中禁用：
1. 打开 `Actions`。
2. 选择名为 “Build and Push Docker Image to Docker Hub” 的工作流。
3. 点击页面右上角 “···” 菜单，选择 “Disable workflow”。

![禁用原作者工作流](images/step-15-action.png)

---

### ❓ 常见问题（FAQ）

#### 关于自动同步功能
**Q: 同步频率是多少？可以调整吗？**  
A: 默认每天午夜执行一次。如需调整频率，可以修改仓库中 `.github/workflows/sync_fork.yml` 文件中的 `cron: "0 0 * * *"` 设置。

**Q: 如何知道同步是否成功？**  
A: 在你的 GitHub 仓库的 Actions 页面可以看到每次同步的执行状态。成功会显示绿色勾号。

**Q: 同步失败了怎么办？**  
A: 查看 Actions 日志，常见原因：上游变更、合并冲突或网络问题。可以点击 "Run workflow" 手动触发一次同步。

**Q: 会不会覆盖我自己的修改？**  
A: 如果你没有修改代码，不会有问题。如果你修改了代码且与上游冲突，需要手动解决冲突。

**Q: 原作者更新后多久我的服务会更新？**  
A: 同步检测到更新后，Vercel 通常在几分钟内完成重新部署。
---

### 参考
- 上游仓库：[`huangxd-/danmu_api`](https://github.com/huangxd-/danmu_api)
- Vercel 登录：[`https://vercel.com/login`](https://vercel.com/login)


