# TileLang 仓库简介

TileLang 是一个面向高性能 GPU/CPU Kernel 开发的 Python DSL。它用接近 Python 的语法描述 tile-level 程序，并基于 TVM 相关编译基础设施将程序 lowering 到硬件相关实现。典型用途包括 GEMM、Dequant GEMM、FlashAttention、LinearAttention、MLA 等 AI 算子的开发、调优和代码生成。

## 主要目录

- `tilelang/`: Python 用户接口、JIT、语言原语、autotuner、后端流水线、布局/量化/分析工具等。
- `src/`: C++ 编译器扩展、IR/算子 lowering、运行时支持，以及 CUDA、ROCm/HIP、Metal、CPU、WebGPU 等后端代码生成和变换。
- `examples/`: 常见算子和端到端示例，例如 GEMM、FlashAttention、DeepSeek MLA、稀疏算子、动态 shape、layout 可视化等。
- `testing/`: Python 与 C++ 测试，按 backend、language、transform、runtime、autotune 等主题组织。
- `docs/`: 安装、快速上手、编程指南、算子说明和编译器内部文档。
- `benchmark/`: 性能测试脚本和不同算子的 benchmark 配置。
- `3rdparty/`: 随仓库引入的 TVM、CUTLASS、Composable Kernel 等第三方依赖。
- `cmake/`、`docker/`、`maint/`: 构建配置、容器环境和维护工具。
- `.agents/skills`: 此仓库相关的skills 

## 常用入口

- 总览与快速开始见 `README.md` 和 `docs/get_started/overview.md`。
- 安装与源码构建说明见 `docs/get_started/Installation.md`。
- 修改 Python DSL 或 JIT 逻辑时，重点关注 `tilelang/language/`、`tilelang/jit/`、`tilelang/engine/`。
- 修改编译 lowering、后端 codegen 或硬件特定优化时，重点关注 `src/` 下对应 backend 与 transform 目录。
- 修改示例或验证功能时，优先运行与改动范围对应的 `testing/` 测试；GPU 后端测试通常需要相应硬件、驱动和运行时依赖。

## 开发注意事项

当前依赖已经安装在名为 tilelang 的 conda 环境中，运行代码时需要在这个虚拟环境中运行

严禁污染全局环境