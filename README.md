# Task5033 V48 冻结资产

用于 [axis-omnireset](https://github.com/MurphyZhao04/axis-omnireset) 的 Task5033 V48 冻结资产。该仓库提供资产下载，运行代码与依赖环境请使用配套代码仓库。

## 下载

- [Task5033 冻结资产包（76.96 MiB）](https://github.com/Curran-code/task5033-v48-assets/releases/download/v1.0.0/task5033-artifacts.tar.gz)
- [SHA256 校验文件](https://github.com/Curran-code/task5033-v48-assets/releases/download/v1.0.0/task5033-artifacts.tar.gz.sha256)
- [Release 说明](https://github.com/Curran-code/task5033-v48-assets/releases/tag/v1.0.0)

两个文件下载到同一目录后验证：

```bash
sha256sum -c task5033-artifacts.tar.gz.sha256
```

压缩包 SHA256：

```text
331a831778da4473b0fb7f74c8301a2a1734168b320655c7665793e96ea0896e
```

## 资产范围

包含配套冻结清单 `locks/artifacts.json` 中的 `task5033/` 和 `native_assets/`：任务场景、302 条示范归档及状态池、资格掩码、固定评估起点、原版 model328 和共用原生 Franka 机器人资产。1,206 个文件，未压缩合计 294,504,079 字节；全部逐项校验通过。

原版 model328 SHA256 为 `0c84df428c69f4c94f62df16652943207c05fc23907e5233280f1ab1a17aaf22`。

不包含重新训练的 iteration328/final 权重、训练输出、代码或 Python/Isaac 环境。

## 恢复

在配套 axis-omnireset 仓库根目录、具备匹配 CPU 环境后执行，替换本机路径：

```bash
export AXIS_OMNIRESET_ARTIFACTS=/your/data/axis-artifacts
.venv-cpu/bin/axis-omnireset prepare --task 5033 \
  --from /your/downloads/task5033-artifacts.tar.gz
.venv-cpu/bin/axis-omnireset doctor --task 5033 --environment cpu
```

`prepare` 根据配套仓库清单逐项验证文件大小与 SHA256。复现既有冻结任务无需连接 AXIS 数据库、S3 或远程资产服务。
