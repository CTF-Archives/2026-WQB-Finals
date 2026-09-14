题目附件前往 [Releases](https://github.com/CTF-Archives/2026-WQB-Finals/releases) 下载

# 第二届“湾区杯”网络安全大赛决赛-网络安全攻防赛(赛道一)

## AWDP-WEB

### InduCoreBot

攻击

> The service provides an AI customer support chat frontend. The backend calls an OpenAI-compatible Chat Completions API.

防御

> The project path is: /app/lib/ .
>
> Patch whitelist commands: ['mv', 'cp', 'rm'].
>
> After update.sh is executed, the environment will automatically restart the service. (The patching process for this challenge may take some time, so it’s also worth trying multiple times.)

### Flowise

攻击

> （本题下发后，请通过http访问相应的ip和port，例如 nc ip port ，改为http://ip:port/）

防御

> 修补路径为: ['/usr/local/lib/node_modules/flowise', '/var/lib/flowise', '/run/flowise', '/opt/flowise-challenge']
>
> 修补白名单命令: ['mv', 'cp', 'chmod', 'node']

### CarbonTrace

攻击

> CarbonTrace is a carbon asset and reward settlement platform designed for new-energy logistics fleets.
>
> The platform has recently introduced a new vehicle data submission workflow. Once submitted data is accepted by the system, the corresponding account receives reward points and may redeem them after meeting the required threshold.
>
> As an ordinary user, you have no access to the vehicle-side secret key material.
>
> Your objective is simple:
>
> Make your wallet balance reach the redemption threshold.

防御

> 修补路径为: ['/opt/carbontrace']
>
> 修补白名单命令: ['cp', 'mv', 'chmod', 'pkill', 'sleep']

### sky_uom

攻击

> 某市低空飞行综合监管平台"苍穹 UOM"完成 v2 升级：飞手注册、飞行申请、空域通报一应俱全。平台早期为存量机载固件保留了一套 v1 设备接入接口，而"管制空域机密通报"只在管理员签名导出通道中流转。请从公开入口出发取得机密通报内容。

防御

> 修补路径为: ['/app']
>
> 修补白名单命令: ['cp', 'mv', 'chmod', 'pkill', 'sleep']

### lingyun_atlas

攻击

> "凌云低空运力开放平台"是低空物流运力的调度中枢，向接入方开放运力查询与告警通知服务。告警通知支持自定义模板渲染，方便运维推送个性化告警。平台的节点注册信息保存在调度中枢的运行时上下文中，其中"节点接入密钥"等同于节点身份凭据。你能获得这个密钥吗？

防御

> 修补路径为: ['/app']
>
> 修补白名单命令: ['cp', 'mv', 'chmod', 'pkill', 'sleep']

## AWDP-PWN

### TideAnchor Echo

攻击

> TideAnchor Echo 是面向智慧港口集卡 T-Box 与无人机坪边缘节点的回执网关，负责接收电子提单分片，处理链路抖动，并在调度周期结束时完成封存和存证回执。回执可以暂停、恢复或替换重投；审计模块同时保留一条运维说明。选手需要在独立容器中还原比赛专用二进制方言，分析网关并取得唯一 flag。
>
> 服务监听容器内 TCP 9999 端口。附件提供 portlinkd、libreceipt_codec.so、匹配的运行时动态链接器/库、协议描述和合法客户端示例。

防御

> 修补路径为: ['/app']
>
> 修补白名单命令: ['mv', 'cp', 'chmod', 'sh', 'pkill', 'sleep']

### tboxgw

攻击

> FleetGuard 是某车联网平台的 T-Box 遥测接入网关守护进程，负责接收车载终端上报的注册、单条遥测、批量 CAN 总线记录与状态查询帧（自研二进制协议，含 CRC-16 校验）。攻击方需分析协议、定位内存安全漏洞并利用获取 flag；防守方无源码，需逆向二进制并以二进制补丁方式修复漏洞，且不得破坏任何正常业务功能。

防御

> 修补路径为: ['/app']
>
> 修补白名单命令: ['mv', 'cp', 'chmod', 'python3', 'pkill', 'sleep']

### RoadLedger

攻击

> RoadLedger 是部署在路侧单元（RSU）的车路协同微账本网关，负责处理车辆遥测回执与紧急车道通行凭证。近期，运维人员发现部分异常结算请求能够绕过既有的业务校验，但尚未定位具体原因。
>
> 服务以自定义 TCP 二进制协议对外提供接口。请分析其通信方式与处理逻辑，找出异常结算的成因，并取得系统中保存的 flag。

防御

> 修补路径为: ['/home/ctf']
>
> 修补白名单命令: ['cp', 'mv', 'chmod', 'pkill', 'sleep

### PortRoute

攻击

> PortRoute 是一款交通协调网关，专为智慧港口危险品集装箱运输中使用的 T-Box 终端而设计。
>
> 车载终端通过专有二进制协议与网关通信，用于上报运行数据并与当前运输任务进行交互。系统支持任务管理、设备配置和状态反馈等多项日常业务操作。
>
> 你的目标是分析该服务，了解其运行机制，并识别潜在的安全问题。

防御

> 修补路径为: ['/home/ctf', '/run/portroute']
>
> 修补白名单命令: ['cp', 'mv', 'chmod', 'pkill', 'sleep']

### SkyFence

攻击

> SkyFence 是部署在低空飞行监管节点中的空域策略管理服务，负责接收无人机任务终端提交的二进制指令，维护飞行任务、禁飞区策略及撤销后的审计记录。
>
> 近期，运维人员发现部分已结束任务的审计记录会在后续操作中出现异常变化，偶尔还会导致服务进程状态异常。现有日志只能确认问题与任务状态切换及审计数据处理有关，无法直接定位根因。
>
> 请分析服务使用的通信协议与任务状态流转，找出造成异常的安全问题，并取得系统中保存的目标信息。

防御

> 修补路径为: ['/home/ctf']
>
> 修补白名单命令: ['cp', 'mv', 'chmod', 'pkill', 'sleep']

# 第二届“湾区杯”网络安全大赛决赛-人工智能漏洞挖掘（赛道二）

## AI

### Backdoor | 59

> 一份文本情感分析机器学习模型被检出疑似植入隐藏后门。模型日常预测功能正常，攻击者将后门触发词伪装为普通特征写入词表与权重文件，常规测试很难发现。请对模型文件开展静态分析，找出隐藏后门标识及其对应权重，权重保留两位小数。
> 提交格式：flag{后门标识:权重}，例如：flag{backdoor:3.14}

Backdoor_735b4ad17666100afee9e814a8bc49c6.zip

### evalModel | 94

> 一份来路不明的图像分类模型被部署上线。经检测，文件内部暗藏玄机。请深入分析该模型文件，找到隐藏的 flag。

evalModel_742bfb8ed1bd76970bc849e10fb33bde.zip

### RAG | 18

> 某公司内部 AI 知识助手近期频繁 "答非所问"，安全团队怀疑知识库被投毒，攻击者将注入载荷藏进看似无害的文档，一旦被检索命中便劫持助手输出。请分析不可信文档，找到攻击者在多个文档中注入的编码混淆指令。

RAG_12282413415310902a35f12f49c1c74b.zip

### 记忆不会消失 | 58

> 某公司怀疑旧版智能助手曾接触过包含凭据、恢复码和内部服务信息的资料。虽然原始训练集已经移除，模型可能仍然保留部分历史痕迹。现在提供一个离线模型、一批查询语句以及一组可能的模型回答。请对这些材料进行取证，找出与模型历史行为最相关的记录，并恢复隐藏信息。

记忆不会消失_ab9a3c0c00f2788d796a0e13c312e96d.zip

### BeforeVerify | 21

> 模型仓库为兼容旧版推理框架接收签名归档，并声称只有通过验签的模型才会被接纳。请审计其加载流程。

BeforeVerify_fcff4208704472e1789193f164c150ce.zip

### model_privacy | 9

> 某公司 HR 模型对外开放了一个接口：
> POST /api/predict（输入 6 维特征数组，返回决策置信度）
> POST /api/verify（提交答案，校验通过返回 flag）
> 你已获得公司"公开"训练集 train.csv，以及 100 名目标高管（y=1） 的已知公开属性 x0..x4（见附件 challenge.txt），但每位高管的敏感属性 x5=code 未知（0..9999 整数）。
> 请通过模型接口恢复全部 100 名高管的 code，然后将 code 从小到大排序，每个 补足 4 位（如 7 → 0007），拼接成一个字符串后取其 MD5（32 位小写十六进制），用 POST /api/verify 提交该 MD5 以获取 flag。

model_privacy_a892d3020364dfda25a7dd82c4e23cdd.zip

### CanaryWeights | 0

> We fine-tuned a small ops-manual LM. Security claims "no secrets in the repo". The ops portal is still in production.
> Attachment: model + inference code + public manual excerpts. Get a valid portal credential and read the flag.
> Portal: POST /portal/login {"account":"...","password":"..."}
> Rate-limited. Secrets are not stored as plaintext in the weight files.

CanaryWeights_274fdaa4564ad6a577bdd7c8dfcc7b6f.zip

### CascadingGuard | 3

> CascadingGuard is an internal assistant behind a 3-layer safety stack (input classifier + aligned system policy + output DLP).
> Talk to POST /v1/chat. Completions that look like secrets are redacted. Recover the production flag.
> The service is offline and uses greedy decoding on CPU.

CascadingGuard_f773c30f622a4dab265153ecf3675a85.zip

### DenseReward | 0

> NeuroForge Hub indexes internal runbooks with a dense retriever and releases artifacts only by model id. A reward model gates redemption.
> The public corpus is attached, the encoder is attached. Keyword filters are on. Get the flag from POST /redeem.
> POST /search {"query":"...","k":3}
> GET /models/download?id=... (header X-Hub-Scope required)
> POST /redeem {"text":"..."}

DenseReward_9eb58c7d383ab64b7e78590e2700c107.zip

### JpegBound | 8

> White-box traffic-sign model is attached. Make orig.png classify as class `speed_limit_80` after the scoring pipeline.
> Constraints are enforced server-side (Linf <= 8/255, SSIM >= 0.90, 32x32 RGB PNG). One successful submission returns the flag.
> Local success does not imply remote success.

JpegBound_35bba498e7b0568fb39ebbbda3e8a6b3.zip


## 人机互竞

### GhostAdapter | 92

> 你获得了适配器仓库的只读测试权限。请调查一次迁移遗留问题，并取得私有适配器工件中的回执。

GhostAdapter_37a87e2c2665dbc74fb93e6a9f2d5c9a.zip

