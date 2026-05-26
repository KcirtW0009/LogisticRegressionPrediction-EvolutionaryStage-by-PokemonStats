# LogisticRegressionPrediction-EvolutionaryStage-by-PokemonStats

基于宝可梦种族值的逻辑回归进化阶段预测模型

## 项目简介

本项目使用逻辑回归（Logistic Regression）算法，通过分析宝可梦的六项基础数值（HP、攻击、防御、特攻、特防、速度），预测该宝可梦所处的进化阶段。

## 功能特点

- 📊 **数据预处理**：解析宝可梦种族值、属性信息，过滤有效形态
- 🔗 **进化图构建**：基于BFS算法计算全局进化深度
- 🎯 **多分类预测**：支持四类进化阶段预测（不进化/基础/一阶/二阶）
- 📈 **模型评估**：提供准确率、混淆矩阵、分类报告等评估指标
- 🎮 **交互式界面**：支持手动输入、名称查询、随机抽取三种预测方式
- 📊 **可视化展示**：特征权重可视化、混淆矩阵热力图

## 技术栈

- **Python 3.11+**
- **核心库**：
  - pandas & numpy - 数据处理
  - scikit-learn - 机器学习建模
  - matplotlib & seaborn - 数据可视化
  - ipywidgets - 交互式组件
  - Jupyter Notebook - 开发环境

## 项目结构

```
├── LogisticRegression predicts Evolutionary stage based on Pokémon body.ipynb
├── Pokemon_Showdown_pokedex.csv          # 宝可梦数据集
├── README.md                              # 项目说明文档
├── LICENSE                               # 开源许可证
└── .gitignore                            # Git忽略配置
```

## 使用方法

### 环境要求

```bash
pip install pandas numpy scikit-learn matplotlib seaborn ipywidgets jupyter
```

### 运行步骤

1. 克隆项目到本地
2. 确保 `Pokemon_Showdown_pokedex.csv` 文件在同一目录下
3. 启动Jupyter Notebook：

```bash
jupyter notebook "LogisticRegression predicts Evolutionary stage based on Pokémon body.ipynb"
```

4. 按顺序执行所有代码单元格

### 预测功能

项目提供三种预测方式：

1. **手动输入**：直接输入HP、最高攻击、最高防御、速度值进行预测
2. **名称查询**：输入宝可梦英文名称，自动查询并预测
3. **随机抽取**：随机选择宝可梦进行预测验证

## 模型说明

### 特征工程

- **原始特征**：HP、攻击(Atk)、防御(Def)、特攻(Spa)、特防(Spd)、速度(Spe)
- **构造特征**：
  - `best_atk` = max(Atk, Spa) - 取物理和特殊攻击中较高的一项
  - `best_def` = max(Def, Spd) - 取物理和特殊防御中较高的一项
- **最终特征**：HP、best_atk、best_def、Spe

### 进化阶段定义

使用BFS广度优先搜索构建进化图，将宝可梦分为四个阶段：

| 阶段 | 说明 | 示例 |
|------|------|------|
| 不进化 | 无进化链 | 皮卡丘、传说宝可梦 |
| 基础 | 进化链起点 | 小火龙、妙蛙种子 |
| 一阶 | 第一次进化后 | 火恐龙、妙蛙草 |
| 二阶 | 第二次及以后进化 | 喷火龙、妙蛙花 |

### 模型参数

- **算法**：多项式逻辑回归 (Multinomial Logistic Regression)
- **求解器**：L-BFGS
- **正则化**：L2正则化
- **类别权重**：balanced（自动平衡样本不均衡）
- **数据标准化**：StandardScaler标准化处理
- **训练集比例**：75%
- **随机种子**：42（保证可复现性）

## 性能指标

模型在测试集上的表现：

- 准确率：约60-70%（取决于数据划分）
- 支持多类别概率输出
- 提供Top-2预测结果

## 数据来源

数据集来自 Pokemon Showdown Pokedex，包含：
- 全国图鉴编号
- 宝可梦名称及地区形态
- 六项基础数值（baseStats）
- 属性信息（types）
- 进化关系（prevo/evos）

## 许可证

本项目采用 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件

## 作者

**KcirtW0009**  
📧 KcirtW0009@outlook.com  
🔗 [GitHub Profile](https://github.com/KcirtW0009)

## 致谢

- [Pokemon Showdown](https://pokemonshowdown.com/) - 提供宝可梦数据
- [scikit-learn](https://scikit-learn.org/) - 机器学习框架
- [The Pokémon Company](https://www.pokemon.com/) - 宝可梦系列版权所有者

---

⭐ 如果这个项目对你有帮助，请给个 Star 支持一下！
