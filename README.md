## 注意事项
务必关闭**Turbo ACC 网络加速**中的**软件流量分载**与**硬件流量分载**，**否则**将**无法正常上网**

## 已知问题
- 不支持的映像([coolsnowwolf/lede#7413](https://github.com/coolsnowwolf/lede/issues/7413))

  - 解决方法：清除 **原配置** **/etc/config/** 下的 **system** , **network** , **dhcp** 后可在线更新
  
- WIFI不自启([coolsnowwolf/lede#8787](https://github.com/coolsnowwolf/lede/issues/8787))

  - 解决方法：添加**启动项**

**脚本**内容
```
#!/bin/sh /etc/rc.common
START=99
start() {
  ip link set ra0 up
  ip link set rai0 up

  brctl addif br-lan ra0
  brctl addif br-lan rai0
}
```
放到/etc/init.d/start_wifi 然后执行 `chmod 755 start_wifi && /etc/init.d/start_wifi enable`

## 感谢
[kenzok8/small-package](https://github.com/kenzok8/small-package)

[coolsnowwolf/lede#7413](https://github.com/coolsnowwolf/lede/issues/7413)

[coolsnowwolf/lede#8787](https://github.com/coolsnowwolf/lede/issues/8787)

[coolsnowwolf/lede#7796](https://github.com/coolsnowwolf/lede/pull/7796)

## 模板

**English** | [中文](https://p3terx.com/archives/build-openwrt-with-github-actions.html)

# Actions-OpenWrt

[![LICENSE](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square&label=LICENSE)](https://github.com/P3TERX/Actions-OpenWrt/blob/master/LICENSE)
![GitHub Stars](https://img.shields.io/github/stars/P3TERX/Actions-OpenWrt.svg?style=flat-square&label=Stars&logo=github)
![GitHub Forks](https://img.shields.io/github/forks/P3TERX/Actions-OpenWrt.svg?style=flat-square&label=Forks&logo=github)

A template for building OpenWrt with GitHub Actions

## Usage

- Click the [Use this template](https://github.com/P3TERX/Actions-OpenWrt/generate) button to create a new repository.
- Generate `.config` files using [Lean's OpenWrt](https://github.com/coolsnowwolf/lede) source code. ( You can change it through environment variables in the workflow file. )
- Push `.config` file to the GitHub repository.
- Select `Build OpenWrt` on the Actions page.
- Click the `Run workflow` button.
- When the build is complete, click the `Artifacts` button in the upper right corner of the Actions page to download the binaries.

## Tips

- It may take a long time to create a `.config` file and build the OpenWrt firmware. Thus, before create repository to build your own firmware, you may check out if others have already built it which meet your needs by simply [search `Actions-Openwrt` in GitHub](https://github.com/search?q=Actions-openwrt).
- Add some meta info of your built firmware (such as firmware architecture and installed packages) to your repository introduction, this will save others' time.

## Credits

- [Microsoft Azure](https://azure.microsoft.com)
- [GitHub Actions](https://github.com/features/actions)
- [OpenWrt](https://github.com/openwrt/openwrt)
- [Lean's OpenWrt](https://github.com/coolsnowwolf/lede)
- [tmate](https://github.com/tmate-io/tmate)
- [mxschmitt/action-tmate](https://github.com/mxschmitt/action-tmate)
- [csexton/debugger-action](https://github.com/csexton/debugger-action)
- [Cowtransfer](https://cowtransfer.com)
- [WeTransfer](https://wetransfer.com/)
- [Mikubill/transfer](https://github.com/Mikubill/transfer)
- [softprops/action-gh-release](https://github.com/softprops/action-gh-release)
- [ActionsRML/delete-workflow-runs](https://github.com/ActionsRML/delete-workflow-runs)
- [dev-drprasad/delete-older-releases](https://github.com/dev-drprasad/delete-older-releases)
- [peter-evans/repository-dispatch](https://github.com/peter-evans/repository-dispatch)

## License

[MIT](https://github.com/P3TERX/Actions-OpenWrt/blob/main/LICENSE) © [**P3TERX**](https://p3terx.com)
