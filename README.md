# SGCC 窃电检测项目

本项目使用机器学习方法，基于国家电网公司（SGCC）数据集，对窃电行为进行检测与分类。

---

## 目录结构

```
SGCC/
├── .devcontainer/          # GitHub Codespaces 配置
│   └── devcontainer.json
├── codes/                  # Jupyter Notebook 代码
│   └── training_workflow_cn.ipynb
├── data/                   # 数据目录（不纳入版本控制，请自行添加）
├── requirements.txt        # Python 依赖
└── README.md
```

---

## 快速开始（GitHub Codespaces）

1. 点击本仓库页面右上角的 **Code** 按钮，选择 **Codespaces** → **Create codespace on ...** 创建云端开发环境。
2. Codespace 启动后会自动执行 `pip install -r requirements.txt` 安装所有依赖。
3. 在左侧资源管理器中打开 `codes/training_workflow_cn.ipynb`，即可直接在浏览器中运行 Notebook。

---

## 本地运行

```bash
# 1. 克隆仓库
git clone https://github.com/LuoXY1024/SGCC.git
cd SGCC

# 2. 创建并激活虚拟环境（可选）
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate

# 3. 安装依赖
pip install -r requirements.txt

# 4. 启动 Jupyter Lab
jupyter lab
```

打开浏览器访问 `http://localhost:8888`，进入 `codes/training_workflow_cn.ipynb` 运行即可。

---

## 数据准备

本项目不包含原始数据集（数据文件已被 `.gitignore` 排除）。请将以下文件放置到 `data/` 目录中：

| 文件名 | 说明 |
|--------|------|
| `data.csv` | 用户用电量时序数据（行：用户，列：日期） |
| `label.csv` | 用户标签（0：正常用户，1：窃电用户） |

数据集来源：[SGCC Dataset](https://github.com/henryRDlab/ElectricityTheftDetection)

---

## Notebook 内容概览

`codes/training_workflow_cn.ipynb` 包含以下步骤：

1. **数据加载** — 从 `../data/` 相对路径读取 CSV 文件
2. **数据探索** — 缺失值分析、类别分布、用电量统计
3. **特征工程** — 统计特征提取（均值、标准差、最大/最小值、差分等）
4. **数据集划分** — 训练集 / 验证集 / 测试集分层划分
5. **基线模型训练** — 随机森林 + XGBoost（含 SMOTE 过采样处理类别不平衡）
6. **模型评估** — 准确率、精确率、召回率、F1、ROC-AUC、PR-AUC

---

## 依赖说明

| 库 | 用途 |
|----|------|
| numpy / pandas | 数据处理 |
| matplotlib / seaborn | 数据可视化 |
| scikit-learn | 机器学习模型与评估 |
| xgboost | 梯度提升分类器 |
| imbalanced-learn | SMOTE 过采样 |
| jupyter / ipykernel | Notebook 环境 |
