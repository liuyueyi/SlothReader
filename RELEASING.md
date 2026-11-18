# Sloth Reader 主站与版本发布

此目录是独立 Git 仓库，`origin` 指向 `https://github.com/liuyueyi/SlothReader.git`。它使用相对路径加载页面与素材，面向该仓库的 GitHub Pages 项目站点。首页链接到该仓库的 Releases；站点本身不生成或上传安装包和源码包。网站在自己的目录中独立提交和推送，不随 Android 仓库提交。

## 部署主站

1. 在本目录中检查 `git status` 与远程仓库内容，然后将网站文件提交并推送到目标仓库的发布分支。不要把 Android 项目的 `docs/CNAME` 一并复制，它属于原站点配置。
2. 在目标仓库的 **Settings → Pages** 中选择对应分支和目录作为发布源。这里假定使用项目站点 `https://liuyueyi.github.io/SlothReader/`；如果采用其他地址或自定义域名，更新 `index.html` 和 `terms.html` 中的 canonical、Open Graph 地址及结构化数据。
3. 检查首页、隐私政策、使用条款、图片及 Releases 链接。首次发布前应核实条款、隐私政策及商店链接适用于当前发行版本。

## 每个版本手动发布

1. 在应用源码仓库记录实际构建的完整 commit、分支及构建时的本地改动。不要用未经确认的工作区或另一个版本的源码冒充对应源码。
2. 根据实际安装包准备对应源码包：包括该版本应用源码、必要构建及安装脚本、构建说明、适用许可证与版权声明，以及应随源码提供的第三方组件源码。核对实际使用的 Gradle 依赖及原生依赖，固定版本和来源，检查是否需要一并提供；可再生的文件应说明如何生成。不要包含签名密钥、密码、本地配置或个人数据。
3. 特别核对 MuPDF：当前构建使用 `Builder/mupdf-1.28.3/`，该上游源码树不在 Git 中；应按实际构建使用的版本及其子模块准备、核对相关源码，并纳入对应源码交付。保留项目的 `Builder/jni/~mupdf-1.28.3/` 覆盖源及映射和生成资源说明，检查源码包是否能还原实际构建输入。详见应用仓库的 `Builder/MUPDF_GUIDE.md`。
4. 准备完整的适用许可证文本及第三方声明；应用仓库的 `LICENSE.txt` 是 GPL-3.0-or-later 的简短声明，并非 GPL 全文。按实际分发渠道和适用条款检查安装说明等义务，GPL 第 6 条的 Installation Information 要求有具体适用条件；不要公开签名私钥。
5. 在 `liuyueyi/SlothReader` 新建对应版本的 GitHub Release，手动上传同版本 APK 和完整源码包。建议命名 `SlothReader-vX.Y.Z-android.apk`、`SlothReader-vX.Y.Z-source.zip`，按实际架构或发行版增加后缀。源码包不应只依赖网站仓库 tag 自动生成的源码归档：它仅包含该仓库当时被跟踪的内容。
6. Release 描述写明版本、发布日期、应用源码仓库与完整 commit、源码包和 APK 的对应关系、适用许可证、构建说明及每个附件的 SHA-256。若不同 APK 的源码或构建配置不同，逐一说明。上传后重新下载并核对哈希与链接；每次分发均应保持相应源码可获取。

源码交付范围和第三方许可证以实际发行物及适用许可为准。以上清单帮助组织发布，不代替对完整依赖、分发方式和法律义务的审查。

参考：[GPL v3 条款](https://www.gnu.org/licenses/gpl-3.0.html)、[GitHub Release 管理](https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository)、[GitHub 自动源码归档](https://docs.github.com/en/repositories/working-with-files/using-files/downloading-source-code-archives)。
