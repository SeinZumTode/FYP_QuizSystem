# quiz-system

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

##### The configuration file of Tailwind CSS was generated using this
```
npx tailwindcss init -p
```

If you found any tailwind css postcss auto prefixer problem, try this:
```
npm uninstall tailwindcss postcss autoprefixer
npm install -D tailwindcss@npm:@tailwindcss/postcss7-compat @tailwindcss/postcss7-compat postcss@^7 autoprefixer@^9
```

# GitHub operation command

## 提交操作
```
首先
git commit -am "first commit message"

上面不行就用下面两个
git add HomeView.vue (git add -A) 
-A跟踪所有文件 韩老师说：跟踪就是只有处于被跟踪状态的文件才会记录新的改动 改动才能被提交
git commit -m "first message"

然后 把本地仓库推上去
git push origin
```



## 我一打开电脑就要做的事
```
首先
git checkout main

然后
git pull

然后回去mingyue 与主分支合并
git checkout mingyue
git merge main

注意：
只有本分支所有东西都commit clean了才能checkout移动到别的分支

去github上pr
pull request意思就是将自己的分支 请求合并到main分支
merge pull request（队友）同意将分支合并
```

## 不小心拉错地方了
```
先把改动暂存一下
git stash

然后checkout回到本来想拉的分支

接着
git stash pop把原本要拉的拉出来
```

### 切换分支
```
git checkout main
git checkout Mingyue
```
## 查询我在哪个分支
```
git branch
```

**解决conflict**
```
出问题以后到红色报错文档
- accept incoming change 接受队友改动
- accept current change 接受自己改动
- manual select chagnes
```
## -b -> 创建新分支 并切换到它
```
git checkout -b "Mingyue"
```