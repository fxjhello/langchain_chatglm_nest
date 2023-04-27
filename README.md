# 基于nest.js-langchain的本地知识的 LLM 应用

## 介绍

本项目旨在实现支持js开发本地知识AI中后台。其中的模型部分采用Python封装，并使用Fastapi暴露出接口。对模型部署和Python等不熟悉的开发人员，只需安装依赖并启动即可，将模型部分当作黑盒使用。中后台使用Langchain.js+nest.js框架，如需对业务逻辑做出更改，只需要在这部分开发，实现纯ts/js开发业务逻辑。

⛓️ 本项目实现原理如下图来自(https://github.com/imClumsyPanda/langchain-ChatGLM/tree/master)所示，过程包括加载文件 -> 读取文本 -> 文本分割 -> 文本向量化 -> 问句向量化 -> 在文本向量中匹配出与问句向量最相似的`top k`个 -> 匹配出的文本作为上下文和问题一起添加到`prompt`中 -> 提交给`LLM`生成回答。

![实现原理图](img/langchain+chatglm.png)

## 变更日志

2023.4.27 项目正式发布v1.0.0

## 硬件需求

- ChatGLM-6B 模型硬件需求
  
    | **量化等级**   | **最低 GPU 显存**（推理） | **最低 GPU 显存**（高效参数微调） |
    | -------------- | ------------------------- | --------------------------------- |
    | FP16（无量化） | 13 GB                     | 14 GB                             |
    | INT8           | 8 GB                     | 9 GB                             |
    | INT4           | 6 GB                      | 7 GB                              |

- Embedding 模型硬件需求

    本项目选用的 Embedding 模型 [GanymedeNil/text2vec-large-chinese](https://huggingface.co/GanymedeNil/text2vec-large-chinese/tree/main) 约占用显存 3GB，也可修改为在 CPU 中运行。


## 开发部署

### 软件需求

Node18,Python 3

### 如果本地已有模型：从本地加载模型

请参考 [THUDM/ChatGLM-6B#从本地加载模型](https://github.com/THUDM/ChatGLM-6B#从本地加载模型)

### 安装依赖并启动


## 鸣谢
本项目的原理图，实现思路，以及Embedding 模型py封装，均来自(https://github.com/imClumsyPanda/langchain-ChatGLM/tree/master)

## 路线图

- [ ] Langchain 应用
  - [x] 支持多种文档格式（已支持 pdf、docx、txt 文件格式）
  - [ ] 搜索引擎与本地网页接入
  - [ ] 结构化数据接入（如 csv、Excel、SQL 等）
  - [ ] 知识图谱/图数据库接入
  - [ ] 更多功能 实现
- [ ] 增加更多 LLM 模型支持
  - [x] [THUDM/chatglm-6b](https://huggingface.co/THUDM/chatglm-6b)
- [ ] 增加更多 Embedding 模型支持
  - [x] [GanymedeNil/text2vec-large-chinese](https://huggingface.co/GanymedeNil/text2vec-large-chinese)
- [ ] 前端
  - [ ] 增加前端展示界面

## 项目交流群
![二维码](img/qr_code_8.png)

🎉 langchain-nest.js 项目交流群，如果你也对本项目感兴趣，欢迎加入群聊参与讨论交流。
