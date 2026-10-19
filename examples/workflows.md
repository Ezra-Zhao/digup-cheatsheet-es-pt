# DigUp 典型用法示例 | Example Workflows

个人学习整理，配合主 README 使用。功能口径以官方 README 为准。

## 1. 找一段忘了文件名的录音内容

场景：几个月前一期播客/会议录音里聊过「睡眠」，文件名只是一串日期。

1. 首次运行 DigUp，索引时勾选放录音的那个文件夹，等首轮索引完成。
2. 任意应用里按 ⇧⌘Space（Windows/Linux 是 Ctrl+Shift+Space）唤出搜索面板。
3. 输入 `where they talk about sleep`，回车——直接跳到录音里聊这段的那一分钟。

English: Index the recordings folder once, then describe the moment ("where they talk about sleep") and land on the exact minute.

## 2. 跨语言找文件：母语提问、英文文档

场景：合同是英文的，但你习惯用西语/葡语思考和提问。

1. 索引放文档的文件夹。
2. 用母语描述要找的内容（如用西语问合同里关于宠物的条款）。
3. 模型把 100+ 语言放进同一空间，西语提问可以直接命中英文 PDF 并跳到对应页——不需要先把问题翻译成英文。

English: Ask in your own language; the shared embedding space matches it against files written in other languages.

## 3. 语义找 vs 精确找，分开用

| 场景 | 写法 | 走哪种匹配 |
|---|---|---|
| 找照片里有狗在海滩的那张 | a dog on the beach | 语义（画面内容） |
| 找报错截图 | payment declined error | 精确串 + 语义（Mac 连截图内文字都精确匹配） |
| 找编号 | 发票号、订单号原文照抄 | 精确串（文件名与文档正文） |
| 找代码里的函数 | code: retry a failed call with backoff | 代码搜索（需在设置里打开） |

English: Describe scenes for semantic search; copy exact strings (invoice numbers, error codes) for exact matching; prefix with "code:" for code search.

## 4. 新机器上手顺序

1. 只勾一个最乱的文件夹（如下载夹）先索引，验证命中质量。
2. 满意后再逐个加文件夹——每加一个它都会先估算首轮耗时。
3. 把唤出快捷键改成自己顺手的组合，日常找东西就不再开文件夹翻了。

English: Start with one messy folder, verify the hits, then expand folder by folder.
