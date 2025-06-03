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
## 综述
| 标题                                                                                                                           | 内容                                                           |
| ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| Automatic Detection of Pain from Facial Expressions: A Survey-[[Survey of PD through Facial Expression【2021】.pdf]]（2019-115） | 总结过去十年中面部表情检测的工作，收集整理了数据集、技术路线、特征分类、学习任务等，也讨论了当前的挑战，未来的研究路线。 |

## 具体文献
| 标题                                                                                                                                                                             | 技术路线                                                                                                      |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------- |
| Automated pain detection using facial expression in adult patients with a customized spatial temporal attention long short-term memory (STA-LSTM) network-[[STA-LSTM.pdf]]     | 数据来自从新加坡两家医院的200名成年患者中收集了2008段视频，裁剪为1s片段，通过调整视频帧的采样间隔平衡数据集，将面部3D归一化，减少了不同角度面部带来的实验误差，模型速度较慢，但是实现了更加准确的识别。 |
| Pain Recognition Using Artificial Neural Network-[[Pain Recognition Using Artificial Neural Network【2006】.pdf]]（2006）                                                          | 基于肤色进行人脸位置检测，后提取面部位置特征+边缘区域形状特征，使用传统3层神经网络进行训练                                                            |
| Relevance Vector Machine Learning for Neonate Pain Intensity Assessment Using Digital Imaging-[[RVM learning for neonate pain intensity assessment using【2010】.pdf]]（2010-128） | 使用相关向量机(RVM)计算面部表情属于类别的后验概率，以概率评估疼痛强度                                                                     |
| Painful monitoring: Automatic pain monitoring using the UNBC-McMaster shoulder pain expression archive database-[[UNBC-McMaster shoulder pain database【2012】.pdf]]（2012-196）   | 整理了UNBC-McMaster肩痛数据集，其中介绍了该数据集的细节                                                                        |
| [[PD with heteroscedastic conditional ordinal random fields【2013】.pdf]]（2013-84）                                                                                               | 允许CORF中顺序概率模型的方差根据输入变化，使其能适应每个受试者特有的疼痛表现力水平                                                               |
| [[Automatic Detection of Pain Intensity 【2012】.pdf]]（2012-216）                                                                                                                 | 结合主动外观模型(AAM)和仿生特征提取面部标准外观(CAPP)，缩放后用Log-Normal滤波器提取特征向量，输入4个SVM独立训练分类4种疼痛强度                              |
| [[Multiview distance metric learning on facial feature descriptors for automatic pain intensity detection【2016】.pdf]]（2016-28）                                                 | 对多种面部特征(Gabor特征、HOG、局部二值模式特征)应用多视图距离度量学习(MDML)产生特征向量，作为SVM的输入【总结相关文献，提到了前面的许多文献】                          |
# 公开数据库

| 名称                                                     | 疼痛               | 数据来源                                | 数据规模                               | 注释/标签                                                                                     |
| ------------------------------------------------------ | ---------------- | ----------------------------------- | ---------------------------------- | ----------------------------------------------------------------------------------------- |
| [[UNBC-McMaster shoulder pain database【2012】.pdf]]<br> | 肩关节疼痛（通过肩部活动度试验） | 129名**成人**（63名男性，66名女性）             | 200个图像序列（总帧：48398;疼痛帧：8369）        | 帧级别：12个AU及其强度（A-E），66个面部标志，PSPI评分<br>序列级别：通过VAS、感觉量表、情感动机量表进行自我报告或通过观察员评定疼痛强度（OPI）进行观察员报告 |
| BioVid Heat Pain Database                              | 热刺激              | 【A部分】18- 65岁87例**成人**（ 44例男性，43例女性） | 8700个视频（疼痛视频6960）                  | 序列级别：基线（无疼痛），4个疼痛刺激强度水平                                                                   |
|                                                        |                  | 【B部分】18- 65岁86名**成人**（42名男性，44名女性）  | 8600个视频（疼痛视频6880个;面部EMG电极导致面部部分闭塞） | 序列级别：基线（无疼痛），4个疼痛刺激强度水平                                                                   |
|                                                        |                  | 【C部分】18- 65岁87名**成人**（44名男性，43名女性）  | 87个视频（A部分的长版本，每个主题一个视频）            | 片段级别：疼痛刺激                                                                                 |
| Infant COPE                                            | 足跟采血             | 18-72小时26例**新生儿**（13例男性，13例女性;高加索人） | 204张面部图像（疼痛图像：60张）                 | 帧级别：疼痛、哭泣、脚跟摩擦、鼻空气刺激、休息                                                                   |
