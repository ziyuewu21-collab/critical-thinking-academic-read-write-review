# Critical Thinking：学术阅读 / 写作 / 评审

[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc/4.0/)

[English](README.md) · **中文**

四个 Claude Code skill，把学术工作变成刻意练习，而不是外包出去。

四个 skill 共用一条设计原则：**苦力活自动化，肌肉留给自己练。** 搜文献、调格式、翻页码找出处，这些是该消灭的杂活；判断证据、搭建论证、写出句子，这些是该保住的能力 —— 所以这四个 skill 没有一个会替你交出成品。

## 流水线

```
literature-triage → reading-companion → writing-companion → research-reviewer
    (读什么)          (把它真正读懂)       (把它写出来)        (像考官一样打分)
```

| Skill | 它做什么 | 它拒绝做什么 |
|---|---|---|
| **literature-triage** | 按一个方向批量检索，把结果分成 core / skim / skip，每篇都给一条和你 RQ 挂钩的理由，并挑出文献之间的矛盾点 | 绝不替你宣布 research gap 是什么 —— 那个判断是你的 |
| **reading-companion** | 用 reviewer 的问题网格盘问你，每个问题都给出确切的页码/章节位置，把你的回答记成笔记 | 绝不替你总结论文，绝不在你读之前把原文段落贴出来 |
| **writing-companion** | 分阶段支持：free-writing → structuring → tightening，让思考和写作不再互相抢资源 | 绝不代写任何一段 |
| **research-reviewer** | 对你的草稿跑四轮考官视角检查，每条问题标注它会扣掉哪一档分 | 绝不改写你的文字 |

## 两个值得直接抄走的想法

**给坐标，不给内容。** `reading-companion` 会告诉你章节、页码、以及目标句子的开头几个词 —— 但绝不给你那句话本身。为了找对段落而通篇扫描是杂活；读那一段并且判断它，才是全部意义所在。把原文粘进对话框，结果就是你读了那句引文，而不是读了论文。

**朝最弱的主张走。** 四个 skill 反复逼你回答同一个问题：*这份研究实际测量了什么，它最少能让我说什么？* 过度声称是好论证丢分最常见的方式，而且从内部看不见。

## 需要什么

- **Claude Code** —— 这四个是 Claude Code skill，跑起来不需要别的东西。
- **Consensus MCP** —— 只有 `literature-triage` 需要。这个 skill 靠 Consensus 检索论文，并且明确禁止引用任何不是 Consensus 返回的文献，所以没连 Consensus 它跑不了。另外三个 skill 没有任何外部依赖，装上就能用。

## 安装

**最省事 —— 把下面这段粘给 Claude Code，它会帮你装好：**

```
把这个仓库里的四个 skill 装进我的 Claude Code skills 目录
（~/.claude/skills/ ，Windows 上是 %USERPROFILE%\.claude\skills\）：
https://github.com/ziyuewu21-collab/critical-thinking-academic-read-write-review
每个 skill 是一个文件夹、里面一个 SKILL.md —— 保持这个结构，文件夹名不要改。

然后打开每个 SKILL.md，把占位符替换成我的真实路径：
<ACADEMIC_ROOT> 和 <WORKSPACE_ROOT>。判断不了就问我。
最后建一个空文件 <ACADEMIC_ROOT>/feedback/feedback-lessons-log.md，
给 skill 留个写入的地方。
```

**或者手动装：**

```bash
git clone https://github.com/ziyuewu21-collab/critical-thinking-academic-read-write-review.git
cp -r critical-thinking-academic-read-write-review-/{literature-triage,reading-companion,writing-companion,research-reviewer} ~/.claude/skills/
```

然后自己替换占位符：

- `<ACADEMIC_ROOT>/` —— 你的笔记、feedback、产出物放在哪
- `<WORKSPACE_ROOT>/` —— 你的项目根目录

有两个文件 skill 会引用，需要你自己建：

- `<ACADEMIC_ROOT>/feedback/feedback-lessons-log.md` —— 你自己的批改记录。这份文件是让教练变得具体而不是泛泛而谈的关键；没有它 skill 照样能跑，但没法针对你个人的失败模式。
- `<ACADEMIC_ROOT>/WEAK-MODEL-MODE.md` —— 降级协议（可选，见下）。

## 在小模型上安全降级

这四个 skill 依赖实时判断，而弱模型判断很差 —— 而且它的失败方式不是少做，是**编一个听起来对、其实错的判断**。所以每个 skill 都带一段机械化护栏：可以逐字照做的规则、用「弱答案/强答案」样例代替模型自信度、以及一条指令 —— 判断不了的就挂起，不许硬编。

## 说明

这四个 skill 是针对一个人的具体弱点做的，用真实的批改反馈调过。协议本身可以通用，诊断部分不行 —— 换成你自己的。

## 许可

采用 [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/) 许可 —— © 2026 Ziyue Wu。

可自由使用、修改、转发。转载请署名 Ziyue Wu 并附上本仓库链接。**禁止商用** —— 不得转卖、不得打包进付费课程或付费产品，商用需事先取得书面许可。
