# Novel Character Namer

一款中文 Codex Skill：根据小说设定集、正文、人物小传或简短方向，为角色设计贴合故事背景与人物弧光的名字。每轮默认给出 **10 个候选**，逐个说明命名依据、预期效果和需要留意的地方。

The skill derives character names from story evidence and explains the naming logic behind each candidate.

## 能做什么

- 从设定、正文和人物资料中提取时代、地域、身份、关系、性格、愿望、命运与命名限制。
- 区分材料里的事实与推测，沿用已经确定的姓氏、族谱、辈分字和语言习惯。
- 用不同思路生成名字，而不是只替换近义字；检查全名的读音、谐音、可读性和风格是否出戏。
- 默认提供 10 个完整姓名，标注主要命名方法并解释它与角色材料的联系。

## 六种命名方法

每种方法都从人物证据出发。示例用于展示思路，不是固定名字模板。

| 方法 | 适用思路 | 示例 |
|---|---|---|
| 寓意法 | 从人物珍视或追求的事物取意 | 心怀天下的贫寒英雄，可用“江天阔”承载胸襟与志向 |
| 性格暗示法 | 直接映出性情，或在有剧情依据时形成反差 | 火烈果决的将军，可考虑“霍烈” |
| 命运暗示法 | 在人物弧光已确定时，用双关或反讽埋轻微伏笔 | 机关算尽而败于算计的谋士，可用“计无咎”制造事后反讽 |
| 背景/时代法 | 符合年代、地域、文化、阶层与家族命名习惯 | 现代职员的日常姓名，与江湖人物的绰号式姓名应有不同语感 |
| 声音韵律法 | 连姓读出声，检查节奏、辨识度、谐音和拗口处 | 试读“陆闻舟”，再判断全名是否适合人物与对话场景 |
| 普通名字法 | 用平常感托住现实人物、群像或不需要名字预告的命运 | 普通农民可以叫“福贵”；名字不必承担象征任务 |

## 使用

在支持 Codex Skills 的环境中调用 `$novel-character-namer`，再提供人物材料或命名方向。例如：

```text
$novel-character-namer

根据下面的人物设定，为她起 10 个名字。她出身于沿海小城的普通家庭，表面温和，实际做事果断；名字要像现代人，不要用生僻字，也不要提前暗示她的结局。
```

输入可以是设定集、正文片段、人物卡、零散背景，或用户对人物的简短描述。若关键资料缺失，Skill 会采用相容的假设并注明；最终由作者决定是否采用名字。

## 安装

将仓库克隆到 Codex 的 Skills 目录。PowerShell 示例：

```powershell
$skillHome = if ($env:CODEX_HOME) { Join-Path $env:CODEX_HOME 'skills' } else { Join-Path $HOME '.codex\skills' }
New-Item -ItemType Directory -Force -Path $skillHome | Out-Null
$target = Join-Path $skillHome 'novel-character-namer'
git clone https://github.com/JIAzc-elk/novel-character-namer.git $target
```

安装后在 Codex 中调用 `$novel-character-namer`。若客户端尚未显示新 Skill，重新加载或重启客户端。

## 文件

- `SKILL.md`：完整命名推导流程、六法详解、校验规则与输出格式。

