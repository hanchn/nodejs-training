## 0. 课程导览与学习路线

* [Node.js 适合做什么、不适合做什么（IO 密集 vs CPU 密集）](./docs/0/01.md)
* [“写得跑” vs “跑得稳” vs “跑得省”三个阶段](./docs/0/02.md)
* [学习路径建议](./docs/0/03.md)

  * 入门：语言/模块/异步
  * 进阶：事件循环/性能/网络/工程化
  * 实战：Web 服务/SSR/BFF/任务系统
  * 生产：监控/灰度/安全/容灾/成本

---

## 1. Node.js 基础与现代 JS 必备

### 1.1 JavaScript 语言基础（服务端视角）

* [作用域与闭包、原型链、this、class、模块化语义](./docs/1.1/01.md)
* [Promise / async-await 的本质](./docs/1.1/02.md)
* [常见坑：循环引用、浅拷贝深拷贝、浮点数、BigInt](./docs/1.1/03.md)
* [Node.js 深拷贝该怎么做](./docs/1.1/04.md)

### 1.2 Node 运行时概念

* [Node 架构：V8 + libuv + C++ bindings](./docs/1.2/04.md)
* [CommonJS vs ESM：加载顺序、循环依赖、互操作策略](./docs/1.2/05.md)
* [全局对象与运行上下文：global、process、Buffer、URL](./docs/1.2/06.md)

### 1.3 核心内置模块速通（只讲“为什么”）

* [fs / path / os / crypto / stream / child_process / worker_threads](./docs/1.3/07.md)
* [util / events / timers / perf_hooks](./docs/1.3/08.md)
* [http/https/2、net、dns、tls](./docs/1.3/09.md)

---

## 2. 异步模型与事件循环（Node 深度核心）

### 2.1 事件循环分层

* [timers / pending callbacks / idle-prepare / poll / check / close callbacks](./docs/2.1/01.md)
* [setTimeout vs setImmediate vs process.nextTick 的执行差异](./docs/2.1/02.md)
* [microtask（Promise）队列与 nextTick 队列优先级](./docs/2.1/03.md)

### 2.2 I/O 与并发模型

* [libuv 线程池：默认大小、适用场景（fs/crypto/dns）](./docs/2.2/01.md)
* [IO 密集为何表现好、CPU 密集为何会“拖死”](./docs/2.2/02.md)
* [背压（Backpressure）与“假并发”的真相](./docs/2.2/03.md)

### 2.3 常见线上问题定位

* [“接口偶发卡死”/“吞吐掉下来”/“CPU 飙高”](./docs/2.3/01.md)
* [阻塞源：同步代码、JSON 大对象、正则灾难、日志写入、模板渲染](./docs/2.3/02.md)

### 2.4 Stream 与高性能 I/O

* [Stream 四种类型与管道模型](./docs/2.4/01.md)
* [背压传播、highWaterMark 的意义](./docs/2.4/02.md)
* [实战：用 Stream 解决大文件问题](./docs/2.4/03.md)

### 3.1 Stream 四种类型与管道模型

* [Readable/Writable/Duplex/Transform 四种类型](./docs/3.1/01.md)
* [pipe 机制、背压传播、highWaterMark 的意义](./docs/3.1/02.md)

### 3.2 实战：用 Stream 解决大文件问题

* [大文件上传/下载、断点续传思路](./docs/3.2/01.md)
* [日志流式处理：gzip、rotate、采样、脱敏](./docs/3.2/02.md)

### 3.3 常见坑与最佳实践

* [内存暴涨：一次性读文件/拼接大字符串](./docs/3.3/01.md)
* [错误处理：pipeline、finish/close、unhandled error](./docs/3.3/02.md)

---

## 4. 网络编程与协议（从应用到内核边）

### 4.1 HTTP 基础与 Keep-Alive

* [连接复用、队头阻塞、TIME_WAIT](./docs/4.1/01.md)
* [反向代理与 Node 的关系](./docs/4.1/02.md)

### 4.2 HTTP/2 与 TLS

* [多路复用、Header 压缩、服务端推送（以及为什么很少用）](./docs/4.2/01.md)
* [TLS 握手、证书链、OCSP Stapling（概念 + 排查点）](./docs/4.2/02.md)

### 4.3 WebSocket / SSE / gRPC（选型与坑）

* [长连接场景：实时通知/IM/埋点上报](./docs/4.3/01.md)
* [断线重连、心跳、扩容与粘性会话](./docs/4.3/02.md)

---

## 5. Web 服务框架与 BFF/SSR 实战

### 5.1 框架选型（Express/Koa/Fastify/Nest）

* [中间件模型差异：洋葱模型 vs 线性](./docs/5.1/01.md)
* [性能、插件生态、类型系统、团队协作成本](./docs/5.1/02.md)

### 5.2 生产级 API 设计

* [路由规范、版本化、幂等、错误码体系](./docs/5.2/01.md)
* [输入校验（schema）、输出裁剪、分页与排序](./docs/5.2/02.md)
* [文件上传、跨域、缓存策略（即使你“不允许缓存”，也要懂）](./docs/5.2/03.md)

### 5.3 SSR / BFF 关键点

* [SSR 的 CPU 与 I/O 分配、模板渲染优化](./docs/5.3/01.md)
* [Layout 共享、页面拆服务的耦合治理](./docs/5.3/02.md)
* [限流/熔断/降级：SSR 与接口链路](./docs/5.3/03.md)

---

## 6. 性能优化与压测（你关心的 QPS/延迟）

### 6.1 性能指标体系

* [QPS、P50/P95/P99、吞吐、并发、错误率](./docs/6.1/01.md)
* [端到端：TTFB/LCP 与服务端链路的对应关系](./docs/6.1/02.md)

### 6.2 Profiling 与诊断工具

* [clinic.js / 0x / flamegraph](./docs/6.2/01.md)
* [Node Inspector、CPU profile、heap snapshot](./docs/6.2/02.md)
* [perf_hooks：自建埋点与耗时分段](./docs/6.2/03.md)

### 6.3 实战：从“跑得动”到“跑得稳”

* [热点函数与对象分配优化](./docs/6.3/01.md)
* [GC 行为与内存泄漏定位](./docs/6.3/02.md)
* [日志/序列化/模板渲染对吞吐的影响](./docs/6.3/03.md)

---

## 7. 进程模型与部署（从单机到集群）

### 7.1 Cluster 与多进程

* [cluster 原理、负载分发策略](./docs/7.1/01.md)
* [sticky session 问题与解决](./docs/7.1/02.md)
* [worker 异常退出的自愈](./docs/7.1/03.md)

### 7.2 Worker Threads 与 CPU 密集任务

* [适用场景：图片处理、压缩、复杂计算](./docs/7.2/01.md)
* [与 child_process 的差异（隔离、开销、通信）](./docs/7.2/02.md)

### 7.3 无状态化与水平扩展

* [会话管理（cookie/jwt/redis）](./docs/7.3/01.md)
* [配置中心与动态配置](./docs/7.3/02.md)
* [连接池与资源上限](./docs/7.3/03.md)

---

## 8. 数据与缓存（不“用缓存”也要懂缓存）

### 8.1 数据访问

* [MySQL：连接池、慢查询、事务与隔离级别](./docs/8.1/01.md)
* [Redis：结构设计、热点 Key、雪崩/穿透/击穿](./docs/8.1/02.md)
* [MQ：异步削峰、延迟队列、重试与幂等](./docs/8.1/03.md)

### 8.2 缓存的边界与替代方案

* [不能缓存价格 → 还能缓存什么：Layout、静态资源、部分聚合](./docs/8.2/01.md)
* [CDN / Edge / 服务端短 TTL / stale-while-revalidate 的工程实践](./docs/8.2/02.md)

---

## 9. 安全（生产环境必须过关）

* [常见漏洞：XSS/CSRF/SSRF/SQLi/路径穿越/原型污染](./docs/9.1/01.md)
* [依赖安全：npm audit、lockfile、供应链攻击防护](./docs/9.1/02.md)
* [CORS、Cookie SameSite、Helmet、rate limit](./docs/9.1/03.md)
* [日志脱敏、PII 合规（GDPR/CCPA 基本原则）](./docs/9.1/04.md)

---

## 10. 可观测性与稳定性工程（SRE 思维）

* [监控三件套：Metrics/Logs/Traces](./docs/10.1/01.md)   
* [OpenTelemetry 接入思路（链路追踪）](./docs/10.1/02.md)
* [告警策略：阈值/同比环比/漏斗异常](./docs/10.1/03.md)
* [事故复盘模板与稳定性指标（SLO/SLI）](./docs/10.1/04.md)

---

## 11. 工程化（团队协作与交付效率）

* [TypeScript 在 Node 的落地：tsconfig、构建、运行（ts-node/tsx）](./docs/11.1/01.md)
* [单测/集成测：Jest/Vitest、supertest、契约测试](./docs/11.1/02.md)
* [代码规范：eslint/prettier/husky/commitlint](./docs/11.1/03.md)
* [构建与发布：Docker、CI/CD、灰度/蓝绿、回滚策略](./docs/11.1/04.md)
* [配置管理：dotenv、KMS/Secrets、分环境策略](./docs/11.1/05.md)

---

## 12. 终局：做一个“生产级 Node 项目”作为毕业设计

你可以把课程最终落到一个完整项目：

* [功能：API + SSR/BFF + 任务系统 + Webhook 回调](./docs/12.1/01.md)
* [特性：限流/熔断/重试/幂等/监控/日志/链路追踪](./docs/12.1/02.md)
* [工具：压测脚本 + 自动化发布 + 回滚演练](./docs/12.1/03.md)
* [文档：架构图、SOP、故障演练与复盘](./docs/12.1/04.md)

---

## 附录

* [V8 深入：隐藏类、Inline Cache、deopt 触发点](./docs/12.2/01.md)
* [正则性能与 ReDoS 防护](./docs/12.2/02.md)
* [Node 与 Nginx/Envoy 的边界：谁该干什么](./docs/12.2/03.md)
* [大促/高峰流量：爬虫治理、Edge 分流、降级策略](./docs/12.2/04.md)
* [多服务拆分下的 layout 同步与版本治理](./docs/12.2/05.md)

---

