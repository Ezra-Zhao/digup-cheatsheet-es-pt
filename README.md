# DigUp 速查表 | DigUp Cheatsheet | Guía rápida de DigUp

> 一页看懂 DigUp：忘了文件名也能找文件。选好文件夹建本地索引，然后用一句话描述你要找的东西——「海滩上的狗」「播客里聊睡眠的那一分钟」「租房合同里关于宠物的那条」——照片、PDF、文档、录音、视频一次找出，并直接跳到对应页 / 对应分钟。全程本地运行，不上传、无账号。

- 上游项目：[ARahim3/DigUp](https://github.com/ARahim3/DigUp)（2026-10-19 实测 4,958 ★，MIT 协议，免费开源）
- 底座模型：Google DeepMind 2026 年 10 月开源的 EmbeddingGemma 2（多模态向量模型，740M 参数，Apache 2.0，支持 100+ 语言，笔记本可跑）
- 平台：macOS（正式版，Apple Silicon）/ Windows 10-11 64 位（beta）/ Linux（beta）
- 本页结构：中文主文 → English → Español → Português
- 本速查表为原创撰写（clean-room）：只参照上游公开文档的事实与操作，文字与编排均为重新创作。

---


Apoyo y más: [GitHub Sponsors](https://github.com/sponsors/Ezra-Zhao) · [Gumroad — plantillas y cuadernos que uso](https://ezraflow28.gumroad.com) · [Ko-fi](https://ko-fi.com/ezra777zhao)

## 核心概念

| 概念 | 一句话说明 |
|---|---|
| 多模态同一空间 | 文本、图片、音频、视频被编码进同一个向量空间：「海滩上的狗」这句话和那张照片在这个空间里是邻居，所以一句话能找出图 |
| 语义索引 | 先选文件夹建索引：它读照片、PDF、文档、录音、视频的内容并编码，之后只读新文件增量更新 |
| 按内容找 | 搜索时不靠文件名和元数据，靠「它展示了什么、说了什么」，命中后跳到 PDF 对应页 / 音视频对应分钟 |
| 跨语言找 | 模型懂 100+ 语言：用西语提问能找出英文文档，反过来也行，链条上哪种语言的文件都能被哪种语言的提问找到 |
| 全本地 | 索引和搜索都在你的电脑上算，不建账号、无遥测；只在首次下载模型和每天查更新时联网（更新检查不发任何文件信息，可关） |

## 能找到什么（官方示例）

| 你输入 | 它给你 |
|---|---|
| zebra in a video | 打开视频里斑马出现的那一刻 |
| where they talk about sleep | 跳到播客里聊睡眠的那一分钟 |
| the clause about pets in the lease | 显示租房合同里关于宠物的那一页 |
| a dog on the beach | 找出那张照片 |
| payment declined error | 找出含这个报错的截图（Mac 上连截图里的文字都能精确认） |
| code: retry a failed call with backoff | 在项目里找出做重试退避的那个函数（需打开代码搜索） |

## 两种查法对照

| 查法 | 适合 | 说明 |
|---|---|---|
| 语义找内容 | 忘了文件名、只记得「里面有什么/说过什么」 | 描述得越具体越准：对象 + 场景 + 关键细节，如「红衣服小孩在公园吹泡泡」 |
| 精确找字符串 | 发票号、报错码、人名这种一字不能差的 | 按原文匹配文件名和文档正文，一次搜索同时给语义和精确两种结果；注意：截图内文字精确匹配目前仅 Mac（靠苹果的文字识别，约 25 种语言），无空格分词的语言（中日泰）在精确匹配上有局限 |

## 安装

**Mac**（正式版）：从上游 Releases 下载 DMG 拖进应用程序，或 Homebrew：

```bash
brew install --cask arahim3/tap/digup
```

需要 Apple Silicon + macOS 14 以上。

**Windows**（beta）：从上游 beta 发布页下载 `DigUp_x.y.z_x64-setup.exe` 运行，仅装当前用户、不需要管理员；安装包暂未签名，Windows 会提示「不认识此应用」，选「更多信息 → 仍要运行」。需要 64 位 Windows 10 或 11。

**Linux**（beta）：Ubuntu / Debian / Mint 等下载 .deb 安装：

```bash
sudo apt install ./DigUp_x.y.z_amd64.deb
```

注意包名是 `dig-up`（Debian 里已有一个无关的 digup 包）；其他发行版用 AppImage（赋可执行权限直接跑）。适用 Ubuntu 22.04、Debian 12、Mint 21 及更新版本，64 位 Intel/AMD。

**首次运行**：模型要下载一次（865 MB：文本部分 310 MB + 图像与音频编码器 555 MB），下载期间就选好要搜的文件夹（整夹或只选部分子夹），它会按你的机器实测给出每个文件夹首轮索引预计耗时。

## 操作速查

| 操作 | Mac | Windows / Linux |
|---|---|---|
| 在任何应用里唤出搜索面板 | ⇧⌘Space | Ctrl+Shift+Space |
| 在结果里移动 | ↑ / ↓ | ↑ / ↓ |
| 打开命中文件（跳到页/分钟） | 回车 | 回车 |

快捷键可在设置里改。

## 隐私一行版

索引内容不出你的电脑：无账号、无遥测、不上传文件；联网只有两件事——首次下载模型、每天一次更新检查（不带任何文件信息，可在设置里关掉）。

## 平台差异（先说清，省得踩空）

- **截图内文字**：仅 Mac 能读截图里的文字做精确匹配；Windows / Linux 上截图按「画面内容」被语义找到，不按其中的文字串精确找。
- **老格式文档**：旧版 Word 的 .doc、RAW 照片、SVG 图片目前仅 Mac 能读。
- **其余搜索体验三端一致**：同一个模型、同一套结果质量逻辑。

## 常见坑 / 问答

- **和 Spotlight / Windows 搜索有什么区别？** 它们按文件名、文本和元数据找；DigUp 还按「画面里有什么、录音里说了什么」找，并带你跳到页或分钟。两者并存不冲突。
- **为什么下载 865 MB？** 基本全是模型：应用本体 Mac 上约 20 MB，Windows/Linux 约 40–140 MB（自带 PDF、视频、图片读取库所以大些）。
- **会拖慢电脑吗？** 只有第一轮索引重；之后只读新文件。模型进程算完即退出，搜索侧只在你在搜的时候加载。
- **语言到底支持到什么程度？** 模型官方口径 100+ 语言且可跨语言搜；但上游的测评只覆盖英语、孟加拉语、阿拉伯语（其测试文件所在语言），Google 也说明模型在各语言上强弱不均——西语/葡语语义搜索可用，精确找词受上文平台差异限制。
- **怎么彻底删除？** Mac：退出后删 DigUp.app 和 `~/Library/Application Support/DigUp`（模型与索引在这），Homebrew 装的用 `brew uninstall --cask --zap digup`。Windows：设置 → 应用里卸载并勾选删除应用数据。Linux：`sudo apt remove dig-up`（或删 AppImage），再删 `~/.local/share/digup` 等目录（全路径见上游 README 的 FAQ）。

## 进阶提示

- **先小范围试**：先只索引一个「最乱、最常找不到东西」的文件夹（下载夹或某个项目夹），验证命中质量再扩全盘，首轮索引时间也短。
- **提问像描述画面**：语义搜索吃「具体名词 + 场景」；找录音/视频里的内容时用「他们聊到 X 的地方」这种说法，比关键词堆叠准。
- **跨语言是隐藏卖点**：手头文件以英文为主、自己习惯西语/葡语提问时不用翻译，直接用母语描述就能搜到英文文件——这正是官方英文文档没强调、母语用户最该知道的一点。

---

## English (summary)

DigUp (by ARahim3, MIT, ~5k stars as of 2026-10-19) searches the files on your computer by what's in them, using Google DeepMind's EmbeddingGemma 2 — the multimodal embedding model released in October 2026 (740M parameters, Apache 2.0, 100+ languages) that puts text, images, audio and video into one shared space. Pick folders to index; DigUp reads the pictures, PDFs, documents, recordings and videos in them. Then describe what you're looking for in your own words: "zebra in a video" opens the clip at that moment, "where they talk about sleep" jumps to that podcast minute, "the clause about pets in the lease" shows the PDF page. Exact strings count too — invoice numbers, error codes and names are matched as written in filenames and document text, and on a Mac that includes the text inside screenshots. A search in one language can find files written in another.

Install: Mac — DMG from Releases or `brew install --cask arahim3/tap/digup` (Apple Silicon, macOS 14+). Windows — beta installer, unsigned for now (More info → Run anyway), 64-bit Windows 10/11. Linux — .deb (package name is `dig-up`) or AppImage, Ubuntu 22.04 / Debian 12 / Mint 21+. First run downloads the 865 MB model once while you pick folders. Hotkey: ⇧⌘Space on Mac, Ctrl+Shift+Space elsewhere.

Privacy: nothing you index leaves your computer — no account, no telemetry; it goes online only to download the model and for a daily update check that sends nothing about your files and can be turned off. Platform differences: screenshot text is read only on a Mac, and old .doc files, RAW photos and SVGs are Mac-only for now; the search itself is the same everywhere. Unlike Spotlight or Windows Search, which match names, text and metadata, DigUp also matches what a file shows or says — and takes you to the page or the minute.

---

## Español (guía rápida — traducción de estudio, pendiente de revisión por un hablante nativo)

DigUp (de ARahim3, licencia MIT, ~5 mil estrellas en octubre de 2026) busca los archivos de tu ordenador por su contenido, con EmbeddingGemma 2 de Google DeepMind: el modelo de embeddings multimodal publicado en octubre de 2026 (740 millones de parámetros, Apache 2.0, más de 100 idiomas) que coloca texto, imágenes, audio y vídeo en un mismo espacio. Eliges las carpetas a indexar y DigUp lee las fotos, PDF, documentos, grabaciones y vídeos que contienen. Después describes con tus palabras lo que buscas: «zebra in a video» abre el clip en el momento exacto, «where they talk about sleep» salta a ese minuto del pódcast, «the clause about pets in the lease» muestra la página del contrato. También cuentan las palabras exactas: números de factura, códigos de error y nombres se buscan tal cual en nombres de archivo y en el texto de los documentos, y en Mac incluso dentro de las capturas de pantalla. Y funciona entre idiomas: puedes preguntar en español y encontrar un documento escrito en inglés.

Instalación:

- **Mac**: DMG desde Releases o `brew install --cask arahim3/tap/digup`. Requiere Apple Silicon y macOS 14 o posterior.
- **Windows**: instalador beta (`DigUp_x.y.z_x64-setup.exe`); aún no está firmado, así que Windows avisará: elige «Más información» → «Ejecutar de todas formas». Windows 10 u 11 de 64 bits.
- **Linux**: paquete .deb (se llama `dig-up`) con `sudo apt install ./DigUp_x.y.z_amd64.deb`, o el AppImage. Ubuntu 22.04, Debian 12, Mint 21 o más nuevos.

En el primer arranque se descarga el modelo (865 MB, una sola vez) mientras eliges las carpetas; el propio programa estima cuánto tardará la primera indexación en tu máquina. Atajo global: ⇧⌘Space en Mac, Ctrl+Shift+Espacio en Windows y Linux.

Privacidad en una línea: nada de lo indexado sale de tu ordenador — sin cuentas y sin telemetría; solo se conecta para descargar el modelo y para una comprobación diaria de actualizaciones que no envía información sobre tus archivos y que puedes desactivar.

Diferencias por plataforma: el texto dentro de las capturas de pantalla solo se lee en Mac, y los .doc antiguos, las fotos RAW y los SVG también son por ahora solo de Mac; la búsqueda en sí es la misma en todas partes. ¿Lentitud? Solo la primera indexación pesa; después solo lee archivos nuevos. Frente a Spotlight o la búsqueda de Windows, que trabajan con nombres y metadatos, DigUp encuentra lo que un archivo muestra o dice, y te lleva a la página o al minuto.

---

## Português (guia rápido — tradução de estudo, aguardando revisão de um falante nativo)

O DigUp (de ARahim3, licença MIT, ~5 mil estrelas em outubro de 2026) busca os arquivos do seu computador pelo conteúdo deles, com o EmbeddingGemma 2 do Google DeepMind: o modelo de embeddings multimodal lançado em outubro de 2026 (740 milhões de parâmetros, Apache 2.0, mais de 100 idiomas) que coloca texto, imagens, áudio e vídeo num mesmo espaço. Você escolhe as pastas para indexar e o DigUp lê as fotos, PDFs, documentos, gravações e vídeos dentro delas. Depois você descreve com as suas palavras o que procura: «zebra in a video» abre o clipe naquele momento, «where they talk about sleep» pula para aquele minuto do podcast, «the clause about pets in the lease» mostra a página do contrato. Palavras exatas também contam: números de nota fiscal, códigos de erro e nomes são buscados como escritos, nos nomes de arquivo e no texto dos documentos — e no Mac, até dentro das capturas de tela. E funciona entre idiomas: você pode perguntar em português e encontrar um documento escrito em inglês.

Instalação:

- **Mac**: DMG nas Releases ou `brew install --cask arahim3/tap/digup`. Requer Apple Silicon e macOS 14 ou posterior.
- **Windows**: instalador beta (`DigUp_x.y.z_x64-setup.exe`); ainda não é assinado, então o Windows vai avisar: escolha «Mais informações» → «Executar mesmo assim». Windows 10 ou 11 de 64 bits.
- **Linux**: pacote .deb (chama-se `dig-up`) com `sudo apt install ./DigUp_x.y.z_amd64.deb`, ou o AppImage. Ubuntu 22.04, Debian 12, Mint 21 ou mais novos.

Na primeira execução, o modelo é baixado (865 MB, uma única vez) enquanto você escolhe as pastas; o próprio programa estima quanto a primeira indexação vai demorar na sua máquina. Atalho global: ⇧⌘Space no Mac, Ctrl+Shift+Espaço no Windows e no Linux.

Privacidade em uma linha: nada do que é indexado sai do seu computador — sem conta e sem telemetria; ele só se conecta para baixar o modelo e para uma verificação diária de atualizações que não envia informação sobre os seus arquivos e pode ser desligada.

Diferenças por plataforma: o texto dentro das capturas de tela só é lido no Mac, e os .doc antigos, fotos RAW e SVG também são, por enquanto, só do Mac; a busca em si é a mesma em todo lugar. Lentidão? Só a primeira indexação pesa; depois ele lê apenas arquivos novos. Diferente do Spotlight ou da busca do Windows, que trabalham com nomes e metadados, o DigUp encontra o que um arquivo mostra ou diz — e leva você até a página ou o minuto.
