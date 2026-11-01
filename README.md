# 其他路由器通用面板 · OpenWrt ODI

保留F50风格的OpenWrt通用流量面板，并逐步接入ODI设备观测、指纹和可解释身份候选。单机可用，不要求客户端安装软件，不依赖云端。

## 当前包含

- [panel/](panel/README.md)：通用面板0.3.3源码，流量曲线、今日上传/下载、本月/总累计、设备统计、负载温度、档案/MAC历史、会话与删除功能。
- [odi/](odi/README.md)：独立观测服务、DHCP事件元数据、umdns缓存与只读影子候选引擎；不自动合并、不迁移免密/拉黑权限。
- [完整方案](docs/PLAN-V2.md)、[当前进度与下一步](docs/PROGRESS.md)：明确已实现、待适配和未验收范围。

## 使用与验证范围

这是两个可组合的源码组件，尚无一键整合安装器。先按panel/preflight.sh识别实际接口和依赖，通用面板构建与安装见panel/README.md；ODI仍为试运行模块，按odi/README.md审阅后单独部署。

现有预编译目标为aarch64，接口名称必须探测，不照搬AX6S。F50观测/影子版通过初步验证，通用面板新版AX6S实机升级以及ODI跨硬件适配未完成。ODI默认档案路径为/etc/router-traffic/profiles.json，可用ODI_REGISTRY_PATH切换本机适配器。

实际互联网流量沿用经验证的只读后端，不以无线bytes代替出口流量，不并行叠加nlbwmon。纯AP可能没有完整网关计数；NAT下游仅按可见整体统计。

第一版只公开源码，不携带私人MAC、名称、流量、配置、密钥、日志、系统备份或编译二进制。旧项目保持独立，本仓库不自动更新已安装路由器。

## 来源与许可

从[F50-OpenWrt-Dashboard](https://github.com/hanxi-p/F50-OpenWrt-Dashboard)选择性复制通用面板和ODI模块，保留SOURCE.json及MIT许可；字体保留其OFL与来源。独立复制的源文件摘要和适配差异见[PROVENANCE.json](PROVENANCE.json)。
