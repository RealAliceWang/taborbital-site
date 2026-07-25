# 页签空间站官网

给 Chrome 应用商店用的公开页面，包含首页和隐私政策。用 GitHub Pages 托管，免费且不需要备案。

- `index.html` —— 产品首页，可作为商店后台的「官方网站」
- `privacy-policy.html` —— 隐私政策，必须填进商店后台的「隐私」标签页

## 首次发布

这个目录已经初始化成独立的 git 仓库，只包含站点文件，不含扩展源码。

1. 在 <https://github.com/new> 建一个**公开（Public）**仓库，名字用 `taborbital-site`，
   不要勾选任何初始化选项（不要加 README、.gitignore 或 license）。

2. 回到终端，在本目录执行（把 `你的用户名` 换成实际的 GitHub 用户名）：

   ```bash
   git remote add origin https://github.com/你的用户名/taborbital-site.git
   git push -u origin main
   ```

   首次推送会要求登录。GitHub 从 2021 年起不再接受账号密码，
   密码那一栏要填 **Personal Access Token**：
   打开 <https://github.com/settings/tokens> → Generate new token (classic) →
   勾选 `repo` → 生成后复制粘贴。这串 token 只显示一次，记得存好。

3. 进入仓库的 Settings → Pages，Source 选 **Deploy from a branch**，
   分支选 `main`、目录选 `/ (root)`，保存。

4. 等一两分钟，页面就会出现在：

   ```
   https://你的用户名.github.io/taborbital-site/
   https://你的用户名.github.io/taborbital-site/privacy-policy.html
   ```

   第二个地址就是商店后台要填的隐私政策链接。

## 之后更新

隐私政策的正本在扩展根目录的 `privacy-policy.html`。改完之后要同步过来再推送：

```bash
cd ..
cp privacy-policy.html site/privacy-policy.html
node tools/selfcheck.mjs        # 会检查两份是否一致
cd site
git add -A && git commit -m "docs: 更新隐私政策" && git push
```

自检里有一项专门比对这两个文件，不一致会直接报错。商店上线的政策和扩展内的政策对不上，
是会被投诉下架的。
