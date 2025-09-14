使用Actions自动编译OpenWrt

介绍
 [本项目源于P3TERX](https://github.com/P3TERX/Actions-OpenWrt/generate)
- 点击 Use this template 按钮创建一个新仓库。
- 通过 Lean's OpenWrt 源代码生成  .config  文件。（可通过工作流文件中的环境变量进行修改。）
- 将  机型.config  文件推送到 GitHub 仓库。
- 在 Actions 页面选择 “Build OpenWrt” 选项。
- 点击 “Run workflow” 按钮。
- 构建完成后，点击 Actions 页面右上角的 “Artifacts” 按钮，即可下载二进制文件。

[![LICENSE](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square&label=LICENSE)](https://github.com/P3TERX/Actions-OpenWrt/blob/master/LICENSE)
![GitHub Stars](https://img.shields.io/github/stars/P3TERX/Actions-OpenWrt.svg?style=flat-square&label=Stars&logo=github)
![GitHub Forks](https://img.shields.io/github/forks/P3TERX/Actions-OpenWrt.svg?style=flat-square&label=Forks&logo=github)

用法:
将预先配置好的.config文件推送到仓库，如果只使用.config可以在工作流中的环境变量写成CONFIG_FILE: .config，如果需要多机型可以将配置文件重命名为:机型.config，同样在工作流中改为相同的名称，需要构建更改机型时只要将工作流中配置文件改为需要编译的机型配置同文件名即可。

提示:

鸣谢
许可证

麻省理工学院 © P3TERX
