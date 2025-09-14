**Simplified Chinese**
使用Actions自动编译OpenWrt

[![LICENSE](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square&label=LICENSE)](https://github.com/P3TERX/Actions-OpenWrt/blob/master/LICENSE)
![GitHub Stars](https://img.shields.io/github/stars/P3TERX/Actions-OpenWrt.svg?style=flat-square&label=Stars&logo=github)
![GitHub Forks](https://img.shields.io/github/forks/P3TERX/Actions-OpenWrt.svg?style=flat-square&label=Forks&logo=github)

A template for building OpenWrt with GitHub Actions

用法:
将预先配置好的.config文件推送到仓库，如果只使用.config可以在工作流中的环境变量写成CONFIG_FILE: .config，如果需要多机型可以将配置文件重命名为:机型.config，同样在工作流中改为相同的名称，需要构建更改机型时只要将工作流中配置文件改为需要编译的机型配置同文件名即可。

提示:

鸣谢
许可证

麻省理工学院 © P3TERX
