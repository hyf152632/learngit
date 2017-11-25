使用 Emoji 当做标签，能非常好的对提交记录分门别类进行整理，你看

✨ Add 🔇 & 🔊 
✨ Add 🤖 & 🍏 
✨ Add 🚚

对于这类型记录，一看就知道添加了一些新 feature 进来了。

💄 Add colors for new gitmojis
💄 Add boom gitmoji styles 
💄 Update emojis order, add mising colors
对于这些记录，主要是样式方面的调整 💄💄💄。

🔧 Update yarn.lock & package.json  
🔧 Update .travis.yml
对于这些呢，是修改配置文件。

🐛 Update flexboxgrid
🐛 Import clipboard only when needed
这些，哪个猪队友又在写 Bug 啊！

⚡️ improve performance of card hover effect
这里进行了一次性能优化，速度像闪电一样快。

那么这些 Emoji 是怎么使用？答案是，在 Emoji 的名字前后个加上一个冒号 `:name_of_emoji:`因此，我们可以这样提交代码

git commit -m "🐞 fix a bug writtten by pig teammate"
他的效果是这样的：

🐛 fix a bug written by pig teammate

我们不仅可以在 git commit 时，在 README.md，在 git wiki 里面都可以直接使用 Emoji，是不是很有意思。

以上，funny it！

To use gitmojis from your command line install gitmoji-cli. A gitmoji interactive client for using emojis on commit messages.

npm i -g gitmoji-cli  
