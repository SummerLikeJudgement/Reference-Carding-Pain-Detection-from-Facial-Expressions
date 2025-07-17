**对于面部疼痛检测的文献整理仓库**

- 特征分类
#spatial-features #spatiotemporal-features
#geometric-features #textural-features
- 技术路线分类
#one-step #two-step
- 学习任务
#pain-nopain #discrete-pain #continuous-pain 

-------

# 文献整理
## 关键词
- automatic pain detection/automatic pain assessment
- facial expression analysis
- facial dynamics
## 综述
| 标题                                                                                                                         | 内容                                                           |
| -------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| Automatic Detection of Pain from Facial Expressions: A Survey([[Survey of PD through Facial Expression.pdf]])（2021-115-A刊） | 总结过去十年中面部表情检测的工作，收集整理了数据集、技术路线、特征分类、学习任务等，也讨论了当前的挑战，未来的研究路线。 |


## 具体文献
| 标题                                                                                                                                    | 特征提取                                                                                                      | 评估方法                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [[STA-LSTM.pdf]]                                                                                                                      | 数据来自从新加坡两家医院的200名成年患者中收集了2008段视频，裁剪为1s片段，通过调整视频帧的采样间隔平衡数据集，将面部3D归一化，减少了不同角度面部带来的实验误差，模型速度较慢，但是实现了更加准确的识别。 |                                                                                                         |
| [[Pain Recognition Using Artificial Neural Network.pdf]]（2006）                                                                        | 基于肤色进行人脸位置检测，后提取面部位置特征+边缘区域形状特征                                                                           | 使用传统3层神经网络进行训练                                                                                          |
| [[RVM learning for neonate pain intensity assessment using.pdf]]（2010-128）                                                            |                                                                                                           | 使用相关向量机(RVM)计算面部属于四个类别的后验概率，以概率评估疼痛强度                                                                   |
| [[PD with heteroscedastic conditional ordinal random fields.pdf]]（2013-84）                                                            |                                                                                                           | 允许CORF中顺序概率模型的方差根据输入变化，使其能适应每个受试者特有的疼痛表现力水平                                                             |
| [[Automatic Detection of Pain Intensity.pdf]]（2012-216）                                                                               | 结合主动外观模型(AAM)和仿生特征提取面部标准外观(CAPP)，缩放后用Log-Normal滤波器提取特征向量                                                  | 输入4个SVM独立训练分类4种疼痛强度                                                                                     |
| [[Multiview distance metric learning on facial feature descriptors for automatic pain intensity detection.pdf]]（2016-28-B刊）           | 对多种面部特征(Gabor特征、HOG、局部二值模式特征)应用多视图距离度量学习(MDML)产生特征向量                                                      | 输入SVM训练分类【有总结相关文献，提到了前面的许多文献】                                                                           |
| [[An Approach for Automatic Pain Detection through Facail Expression.pdf]]（2016-96）                                                   | 对人脸图像进行仿射变换（结合Delaunay三角剖分和Procrustes分析等），使用Gabor滤波提取人脸特征，PCA进行降维                                         | 输入SVM训练分类                                                                                               |
| [[PD using Spatiotemporal Oriented Energy of Facial Muscles.pdf]]（2015-48）                                                            | 数据集已提供面部标志点位，利用AAM对齐到固定框架，使用时空滤波器检测像素->区域释放能量的方向和强度                                                       | 获得每个区域的方向直方图后，结合时间域以检测疼痛及级别                                                                             |
| [[Spatiotemporal Analysis of RGB-D-T Facial Images for Multimodal Pain Level.pdf]]（2015-54）                                           | 找到RGB、深度、热成像的标志点位后，利用时空滤波器分别计算像素->区域释放能量                                                                  | 三种模态的疼痛指数加权计算疼痛水平，根据阈值判断疼痛等级                                                                            |
| [[Disclosing neonatal pain in real-time.pdf]]（2025-1）                                                                                 | 数据集已经过面部检测的预处理                                                                                            | 使用VGG-Face、N-CNN、ViT分别训练预测属于“疼痛”的概率。 <br>使用可解释方法Grad-CAM<br>(GC) and Integrated Gradients (IG)对预测过程进行解释 |
| [[multi-modal fusion of facial features and video streams.pdf]]（2025-0-C刊）                                                            | MediaPipe Face Mesh toolkit找到面部关键点提取空间特征+VGG16提取深度特征；<br>然后将两个源的特征向量连接、归一化                                | 连接后的特征向量输入BiLSTM，训练预测疼痛等级                                                                               |
| [[Improving Pain Classification using Spatio-Temporal Deep Learning .pdf]](2025-2-arxiv)                                              | ConvNeXt 架构提取每帧的空间特征<br>STGCN提取每帧的时空特征                                                                    | 特征向量输入LSTM，训练预测是否疼痛                                                                                     |
| [[Muiltimodal AI PD-integrating facial gesture and paralanguage analysis.pdf]]（2025-0-B会）                                             | 对图像、音频进行预处理；<br>opencv库提取面部关键点<br>librosa库提取音频特征                                                          | 利用时间戳同步两数据<br>CNN分析面部特征；LSTM分析时序音频特征                                                                    |
| [[Pain assessment from facial expression images utilizing Statistical Frei-Chen Mask (SFCM)-based features and DenseNet.pdf]]（2024-0） | “Chehra”人脸检测器裁剪面部区域；<br>Frei-Chen边缘检测器提取SFCM纹理特征<br>DenseNet提取深度特征；<br>将两个源的特征向量连接                        | 最终特征向量使用RBF-ELM分类器进行训练                                                                                  |

# 公开数据库
github总结仓库[A list of pain recognition databases that are publicly available for research](https://github.com/philippwerner/pain-database-list?tab=readme-ov-file)

| 名称                                                                                                                        | 数据来源                                           | 数据规模                                                           | 注释/标签                                                                                       |
| ------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------- | -------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| UNBC-McMaster shoulder pain database([[Automatic pain monitoring using the UNBC-McMaster shoulder.pdf]])<br>**似乎已经无法申请？** | 肩关节疼痛：129名**成人**（63名男性，66名女性）                  | 200个图像序列（总帧：48398；疼痛帧：8369）                                    | 【帧级别】12个AU及其强度（A-E），66个面部标志，PSPI评分<br>【序列级别】通过VAS、感觉量表、情感动机量表进行自我报告或通过观察员评定疼痛强度（OPI）进行观察员报告 |
| BioVid Heat Pain Database<br>[申请页面](https://www.nit.ovgu.de/nit/en/BioVid-p-1358.html)                                    | 【A】<br>急性热痛：87例**成人**（44例男性20-64岁，43例女性20-65岁） | 8700个视频（疼痛视频6960）包含正面视频、皮肤电反应（GSR）、心电图（ECG）、斜方肌EMG             | 【序列级别】基线（无疼痛）+4个疼痛刺激强度水平                                                                    |
|                                                                                                                           | 【B】<br>急性热痛：18- 65岁86名**成人**（42名男性，44名女性）      | 8600个视频（疼痛视频6880个;面部EMG电极导致面部部分闭塞）包含正面视频、GSR、ECG、斜方肌、皱眉肌和颧肌EMG | 【序列级别】基线（无疼痛）+4个疼痛刺激强度水平                                                                    |
|                                                                                                                           | 【C】<br>急性热痛：18- 65岁87名**成人**（44名男性，43名女性）      | 87个视频（A部分的长版本，每个主题一个视频）包含正面视频、GSR、ECG、斜方肌EMG、疼痛刺激标签            | 【片段级别】疼痛刺激                                                                                  |
|                                                                                                                           | 【D】<br>表演的疼痛和基本情绪：90名成人                        | 630个1分钟视频                                                      | 【片段级别】快乐、悲伤、愤怒、厌恶、恐惧、疼痛、中性                                                                  |
| Infant COPE                                                                                                               | 足跟采血：18-72小时26例**新生儿**（13例男性，13例女性;高加索人）       | 204张面部图像（疼痛图像：60张）                                             | 【帧级别】疼痛、哭泣、脚跟摩擦、鼻空气刺激、休息                                                                    |
| FENP([[A Database of Neonatal Facial Expression for Pain Analysis.pdf]])                                                  | 2天-4周106名**新生儿**                               | 4种分类各2750张图像                                                   | 【帧级别】剧痛、轻度疼痛、哭泣、平静                                                                          |
| MintPAIN([[Deep Multimodal Pain Recognition.pdf]])<br>[申请页面](https://vap.aau.dk/mintpain-database/)                       | 电刺激：20名**成人**                                  | 3200个帧序列（`20*2`次实验，每次实验40次疼痛刺激生成80个文件夹）且包含RGB、深度、热成像三个模态       | 【序列级别】基线（无疼痛）+4个疼痛刺激强度水平                                                                    |

# think
- 不同个体之间对痛苦耐受程度不同，需要对不同个体的差异有适用性。
- 疼痛和其他负面情绪都会影响面部表情，但疼痛具有独特的模式，应当可以将其与其他进行区分。
- PD主要有两个方面进行创新：特征提取和评估方式。面部位置检测如今应该比较成熟，不好创新。