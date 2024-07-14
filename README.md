# Mylearn_MR_Code

个人从零学习孟德尔随机化，日常记录

## day02

#### 1. 合理使用AI

##### prompt：

1. 请你帮我总结以上内容，以论点的形式，总结主要内容。



#### 2. MR文献的解读

1. 代谢组与疾病间的因果关联

- 标题：Causal relationship between gut microbiota and cancers: a two-sample Mendelian randomisation study

- 研究背景：肠道微生物群已被认为是包括癌症在内的多种痪病的风险或预防因素，并且与结直肠癌的发病密切相关。然而，肠道微生物群与癌症之间的关联是否具有因果性，以及因果关联的方向仍然未知。

- 研究目的：通过进行**两样本孟德尔随机化**研究，探索**肠道微生物群**与**8种肿瘤**之间的因果关联。

- 可参考的研究方法写法

  - GWAS summary data for (exposure) ➡️  Extracted SNPs that associated with exposure(P <= 5 * 10-8)

  - GWAS summary data for (outcome) ➡️  Extracted SNPs that associated with exposure
  - ➡️ Hamonize effect size and alleles of SNPs on th exposure and outcome data
  - ➡️ Clumping process(R2 < 0.01, window size = 500kb)
  - ➡️ Remove potential pleiotropie SNPs by MR-PRESSO method
  - ➡️ MR analyses
  - ➡️ Sensitivity analyses and remove MR analyses

- 可参考的数据来源表格写法

  Supplemental table. Overview of the source of outcome data

| GWAS ID | Year | Trait | Consortium | Sample size | Case | Control | Number of SNPs | Population |
| :-----: | :--: | :---: | :--------: | :---------: | :--: | :-----: | :------------: | :--------: |
| ieu-xx  |      |       |            |             |      |         |                |            |
| ebi-xx  |      |       |            |             |      |         |                |            |
| ukb-xx  |      |       |            |             |      |         |                |            |

- 可参考的研究方法
  - **只包含一种Iv的特征**：使用Wald比比值检验来估计所识别的IV与每种癌症之间的关联。
  - **包含多个IVs的特征**：逆方差加权(IVW)检验、加权模式、MR-egger回归、加权中位数估计(WME)和MR-presso。
  - **多重检验**：在每个特征水平建立了多重检验显著性阈值，定义为p＜0.05/n(其中n为相应分类水平上独立细菌分类群的有效数量)。
  - 进行**敏感性分析**以评估结果的稳健性。进行留一分析以确定因果信号是否由单个SNP驱动。
  - **异质性分析**：使用Cochran's Q检验异质性检验。如果Q大于工具变量数减1，则证明存在异质性和无效工具，或者p值<0.05显著的Q statistic表明存在异质性
  - **反向MR分析**：使用与癌症相关的SNP作为Iv进行反向MR分析（癌症作为暴露，确定的因果细菌属作为结局）。MR Steiger方向性检验来检验暴露是否对结果有方向性因果关系。
- 研究结果
  - SNP的选择结果
  - 肠道菌群对8种癌症发展的因果影响
  - 肠道菌群和癌症之间的潜在因果关系
  - 敏感性分析
  - 肠道微生物群与癌症风险之间的双向因果效应

2. 两种疾病间的因果关联

- 标题：Causal influences of neuropsychiatric disorders onAlzheimer's disease
- 研究背景：神经退行性疾病和神经精神疾病之间的遗传关系可能存在复杂的纠缠模式，涉及多效基因和多种共调控或交叉通路。
- 研究目的：为了对神经退行性阿尔茨海默病和神经精神疾病的共同遗传学提供新的见解，对代表大脑疾病谱系两端的常见庆病一一神经精神疾病和阿尔茨海默病的遗传成分进行MR研究。

3. MR筛选药物靶点

- 标题：Systematic druggable genome-wide Mendelianrandomisation identifies therapeutic targets fotAlzheimer's disease

- 研究背景：目前只有少数药物可用于AD，并且不能治愈或延缓AD的进展。许多已鉴定的SNP位于非编码区或基因间区，GWAS无法清晰直接地提供有关致病基因和药物靶点的线索。
- 研究目的：进行系统的可药物全基因组MR分析以确定AD的治疗靶点。



## day01

### 1. MR研究升级套路

- MR + 
  - 原始研究数据 + MR
  - MR + Meta
  - MR + 公开数据库
  - MR + 生信分析
- 双向MR
- 多变量MR （Multivariable Mendelian Randomiza）
  - 还是一个暴露一个结局，对于暴露数据库，采用不同的数据库，然后再做一个Meta分析。
  - 还是一个暴露一个结局，增加不同调整变量，也做Meta分析。
- 中介分析MR（Two - Step）
  - 
- 非线性MR
- 肠道菌群MR
  - 肠道菌群与疾病关联密切
  - 深受混杂因素影响
    - 个人饮食
    - 行为习惯
    - 药物
    - 等等
  - 肠道菌群SNP数据来源：https://mibiogen.gcc.rug.nl/
- 药物靶点MR
  - 药物靶点MR + 药物副反应
- 线粒体基因MR + mtDNA拷贝数
- pQTL - MR
  - 蛋白质数量性状位点( ProteinQuantitative Trait Loci, pQTL) 是指与蛋白质表达水平相关的遗传变异位点。这些位点的发现也可以为研究蛋白质与疾病之间的关联提供基础，有助于揭示潜在的治疗靶点和生物学机制。可探索双疾病共同致病因素与药物干预靶点。
- 批量暴露 + MR



### 2. MR文章写作投稿注意事项

#### 关于写作

- introduction（why？）
  - 突出问题和矛盾
  - 强调MR的优势
- methods（how？)
  - 详细描述MR的过程
  - 数据库来源介绍要清晰，如果涉及授权要说明
  - MR文章的样本量估计
- results（what？）
  - 文字描述简洁清晰
  - 图文并茂，巧妙配合附表
  - 敏感性分析说明结果的稳健性
- discussion / conclusion（？）
  - 再次强调研究意义、临床意义
  - 其他的观察性流行病学研究发现了什么
  - 机制研究已经发现了什么
  - 优势、局限性

#### 关于投稿

1. 调研杂志是否接收MR
2. 考虑审稿周期： MR文章复现难度低，被人抢先一步风险高
3. 数据可及性申明：可以将数据作为附表上传
4. 对标杂志社的一般要求：包括摘要格式、段落标题等

### 

