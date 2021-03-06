---
title: 节点和负载均衡
description: 使用您选择的提供商为您的 RKE 安装提供 3 个节点和一个负载均衡器端点。
keywords:
  - rancher 2.0中文文档
  - rancher 2.x 中文文档
  - rancher中文
  - rancher 2.0中文
  - rancher2
  - rancher教程
  - rancher中国
  - rancher 2.0
  - rancher2.0 中文教程
  - 安装指南
  - 资料、参考和高级选项
  - Rancher高可用Helm2安装
  - 配置基础设施
  - 节点和负载均衡
---

使用您选择的提供商为您的 RKE 安装提供 3 个节点和一个负载均衡器端点。

> **注意事项:** 这些节点必须位于相同的区域/数据中心。您可以将这些服务器放在单独的可用区中。

## 节点要求

在 [节点需求](/docs/installation/requirements/_index) 中查看运行 Rancher 的节点支持的操作系统和硬件/软件/网络需求。

在 [RKE 需求](https://rancher.com/docs/rke/latest/en/os/) 中查看 RKE 的操作系统需求。

## 负载均衡

RKE 将在每个节点上配置一个 Ingress controller pod。Ingress controller pods 被绑定到主机网络的 TCP/80 和 TCP/443 端口上，并且是到 Rancher Server 的 HTTPS 流量的入口点。

将负载均衡器配置为基本的 4 层 TCP 转发器。确切的配置将取决于您的环境。

> **重要:**
> 安装后，请勿使用此负载均衡器（即`local`集群 Ingress）对 Rancher 以外的应用程序进行负载均衡。与其他应用程序共享此 Ingress 可能会在其他应用的 Ingress 配置重新加载后导致 Rancher 出现 websocket 错误。我们建议将`local`集群专用于 Rancher，而不应使用其他任何应用程序。

## 例子

- [Nginx](/docs/installation/options/helm2/create-nodes-lb/nginx/_index)
- [Amazon NLB](/docs/installation/options/helm2/create-nodes-lb/nlb/_index)

#### [下一步: 使用 RKE 安装 Kubernetes](/docs/installation/options/helm2/kubernetes-rke/_index)
