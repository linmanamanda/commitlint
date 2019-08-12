> [Conventional Commits规范](https://link.juejin.im/?target=https%3A%2F%2Fconventionalcommits.org%2F%23conventional-commits-100-beta2) 

## 规定的格式

```poe
<type>[optional scope]: <description>
[optional body]
[optional footer]
```
### type
用于表明我们这次commit的改动类型，开源社区目前总结出了以下 11 种类型
- build：主要目的是修改项目构建系统(例如 glup，webpack，rollup 的配置等)的提交
- ci：主要目的是修改项目继续集成流程(例如 Travis，Jenkins，GitLab CI，Circle等)的提交
- docs：文档更新
- feat：新增功能
- fix：bug 修复
- perf：性能优化
- refactor：重构代码(既没有新增功能，也没有修复 bug)
- style：不影响程序逻辑的代码修改(修改空白字符，补全缺失的分号等)
- test：新增测试用例或是更新现有测试
- revert：回滚某个更早之前的提交
- chore：不属于以上类型的其他类型

### optional scope
用于标识此次提交主要涉及到代码中哪个模块（最好在项目中规定好模块列表，保持一致性）

### description
一句话描述此次提交的主要内容

### optional body 和 optional footer
通常不会用到

## commitlint
### 安装依赖包
安装`commitlint`、Conventional Commits 规范对应的`@commitlint/config-conventional`包和`git commit`时进行commitlint检查的 git hook 工具`husky`
```
npm install --save-dev @commitlint/cli @commitlint/config-conventional
npm install --save-dev husky
```
### commitlint.config.js
```js
module.exports = {
	extends: ['@commitlint/config-conventional']
}
```
### npm script
```json
{
	// ...
	"husky": {
    "hooks": {
      "commit-msg": "commitlint -E HUSKY_GIT_PARAMS"
    }
  },
	// ...
}
```
## 效果
不符合规范时的`commitlint`提示
符合时正常提交`commit`

