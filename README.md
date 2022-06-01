# README
我们的压缩文件里面包括了以下几个部分:\
(1) **Report.pdf**：我们小组的报告\
(2) **data**: ECFP.npy, Image.npy, label.npy, SMILES.npy 三种原始特征数据与标签\
(3) **datapre.py**：数据处理程序\
(4) **classification.py**:单个的分类训练及测试程序\
(5) **ensemble.py**:ensemble训练及测试程序\
(6) **best.py** 最优模型训练及测试\
(6) **requirements.py**: 部分环境的库安装\
(7) **model_300dim.pkl**：Mol2vec的预训练模型的参数

## 几点说明
我们的基础模型均在classification.py中实现，ensemble模型均在ensemble.py中实现，在其中包括了我们对于数据集的训练、验证、测试集的划分；datapre.py中包括了我们的Mol2vec预训练程序。

## 环境要求

需要安装的包为：\
python 3.7.13\
scikit-learn==1.0.2\
mol2vec==0.1 \
numpy==1.21.6\
pandas==1.3.5\
matplotlib==3.5.2\
rdkit==2020.09.1.0\
可以通过以下命令安装部分包：
```bash
pip install -r requirements.txt
```
rdkit库的安装如下
```bash
conda install -c rdkit rdkit
```
mol2vec 库的安装如下
```bash
pip install git+https://github.com/samoturk/mol2vec
```
### 安装环境时的注意事项
由于mol2vec库和rdkit库的安装有些包冲突，因此安装顺序很重要，其两者的安装顺序请自行调试（我们发现总有一种顺序可以）

## 整理数据的命令
```bash
python datapre.py
```
会得到以下几个新的数据：\
(1) Smilesfeatures.csv（dim:304)\
(2) mols.npy(dim:4)\
其余的数据处理均在classification.py和ensemble.py中实现。

## 训练最优模型及得到测试结果的命令
```bash
python best.py
```
会进行模型的训练并在最后输出预测的结果，即ROC曲线和AUC分数，为ensemble_best。
### 记得先进行整理数据的命令

## 训练其余模型及测试结果的命令
```bash
python classification.py
```
```bash 
python ensemble.py
```
## 关于结果查看
请在./results中查看\
对应的结果名称均已在报告中给出

