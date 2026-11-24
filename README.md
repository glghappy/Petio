# Petio

Petio 是基于 [Folia](https://github.com/PaperMC/Folia) 的服务端。Petio 通过 paperweight 以 Folia 为上游，将自身补丁叠加在 Folia 之上，因此可以直接复用 Folia 的区域化多线程（regionised multithreading）实现。

## 上游

- 上游仓库：`PaperMC/Folia`
- 上游版本锁定在 [gradle.properties](gradle.properties) 的 `foliaRef`
- 同步上游：修改 `foliaRef` 后重新执行 `./gradlew applyAllPatches`

## 目录结构

| 目录 | 说明 |
| --- | --- |
| `petio-api/paper-patches` | 叠加在 Folia 打好补丁的 `paper-api` 之上的 API 补丁 |
| `petio-api/folia-patches` | 叠加在 `folia-api` 之上的 API 补丁 |
| `petio-server/paper-patches` | 叠加在 Folia 打好补丁的 `paper-server` 之上的服务端补丁 |
| `petio-server/folia-patches` | 叠加在 `folia-server` 之上的服务端补丁 |
| `petio-server/minecraft-patches` | 直接作用于 Minecraft 源码的补丁 |

`paper-api`、`paper-server`、`folia-api`、`folia-server` 以及各模块的 `build.gradle.kts` 均由 paperweight 生成，不入库。

## 构建

需要 JDK 25。

```bash
./gradlew applyAllPatches
./gradlew build
```

Windows 下使用 `gradlew.bat`。构建产物位于 `petio-server/build/libs/`。

## 许可证

Petio 继承上游 Paper/Folia 的 GPL-3.0 许可。`PATCHES-LICENSE` 描述了 API 与服务端补丁的许可，补丁位于各 `*-patches` 目录。
