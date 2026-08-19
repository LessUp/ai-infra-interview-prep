# 🔬 Open MPI 学习指南

> **上游：** [open-mpi/ompi](https://github.com/open-mpi/ompi)
> **你的 Fork：** [LessUp/ompi](https://github.com/LessUp/ompi)
> **语言：** C
> **建议学习时间：** 按需
> **面试重要性：** ⭐⭐

---

## 📌 这个仓库是什么？

Open MPI 是高性能计算中最广泛使用的 MPI（消息传递接口）实现，用于分布式计算中的进程间通信。

## 🎯 为什么对 AI Infra 重要？

1. **理解分布式通信** — 分布式训练中的 AllReduce 等操作底层依赖 MPI
2. **理解 NCCL 的前身** — NCCL 借鉴了 MPI 的很多概念
3. **HPC 背景** — 你已有的 HPC 知识可以迁移

## 🔑 精髓：核心概念

- **集合通信** — AllReduce, AllGather, ReduceScatter, Broadcast
- **点对点通信** — Send/Recv
- **通信拓扑** — Ring, Tree, Recursive Halving

## 📖 推荐学习路径

按需查阅，不需要深入学习（AI Infra 中更常用 NCCL）。

## 🔗 相关仓库
- [cuda-samples](./cuda-samples.md) — 多 GPU 示例
