# TextCNN

这是一个基于 TextCNN 的文本分类训练项目。代码使用的是 TensorFlow 1.x 风格 API，并依赖旧版 gensim 的词向量接口。

## 项目结构

| 文件 | 作用 |
|---|---|
| `train.py` | 训练入口 |
| `text_cnn.py` | TextCNN 模型定义 |
| `input_data.py` | 读取训练集、测试集和词向量 |
| `tool.py` | 相似度和矩阵处理工具 |
| `data/nlu_data/train_shuffle.txt` | 训练数据 |
| `data/nlu_data/test.txt` | 测试数据 |

## 运行前必须准备

项目需要一个词向量文件：

```text
data/nlu_data/wiki.en.vec
```

这个文件没有提交到仓库。没有它，`python train.py` 会在读取数据阶段失败。

当前仓库也没有 `requirements.txt`，所以依赖版本没有被锁定。建议后续补充依赖清单，避免不同机器上的 Python、TensorFlow、gensim 版本不一致。

## 最小运行方式

准备好依赖和 `wiki.en.vec` 后，在项目根目录运行：

```bash
python train.py
```

训练日志和模型检查点会写入本地输出目录，这些文件不应该提交到 Git。

## 已知问题

| 问题 | 影响 |
|---|---|
| 当前代码使用 TensorFlow 1.x API | 不能直接按 TensorFlow 2.x 项目运行 |
| 当前代码使用旧版 gensim API | 新版 gensim 中 `vocab`、`syn0` 等接口可能不可用 |
| 本机 Python 3.14 不适合直接运行 | TensorFlow 1.x 不支持这个 Python 版本 |
| 缺少 `requirements.txt` | 需要手动确认依赖版本 |
| 缺少 `data/nlu_data/wiki.en.vec` | 没有词向量文件就不能训练 |
