**疼痛检测的文献整理仓库**

# 背景
- **keyword**
	- pain detection/pain assessment

-------
# 综述
| 标题                                                                         | 内容                                                           |
| -------------------------------------------------------------------------- | ------------------------------------------------------------ |
| Automatic Detection of Pain from Facial Expressions: A Survey（2021-115-A刊） | 总结过去十年中面部表情检测的工作，收集整理了数据集、技术路线、特征分类、学习任务等，也讨论了当前的挑战，未来的研究路线。 |


## discrete pain

| 标题                                                                                                                                                                   | 特征提取                                                                                                              | 评估方法                      |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ------------------------- |
| Automated pain detection using facial expression in adult patients with a customized spatial temporal attention long short-term memory (STA-LSTM) network（2025-0-二区） | 【视觉】<br>数据来自从新加坡两家医院的200名成年患者中收集了2008段视频，裁剪为1s片段，通过调整视频帧的采样间隔平衡数据集，将面部3D归一化，减少了不同角度面部带来的实验误差，模型速度较慢，但是实现了更加准确的识别。 |                           |
| Enhanced deep learning framework for real-time pain assessment using multi-modal fusion of facial features and video streams（2025-0-C刊）                              | 【视觉】<br>MediaPipe Face Mesh toolkit找到面部关键点提取空间特征+VGG16提取深度特征，然后将两个源的特征向量连接、归一化                                    | 连接后的特征向量输入BiLSTM，训练预测疼痛等级 |
| Pain assessment from facial expression images utilizing Statistical Frei-Chen Mask (SFCM)-based features and DenseNet（2024-0）                                        | 【视觉】<br>“Chehra”人脸检测器裁剪面部区域；<br>Frei-Chen边缘检测器提取SFCM纹理特征<br>DenseNet提取深度特征；<br>将两个源的特征向量连接                        | 最终特征向量使用RBF-ELM分类器进行训练    |
|                                                                                                                                                                      |                                                                                                                   |                           |
# pain-no pain

| 标题                                                                                                           | 特征提取                                         | 评估方法                                                                                                    |
| ------------------------------------------------------------------------------------------------------------ | -------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [[Disclosing neonatal pain in real-time.pdf]]（2025-1）                                                        | 数据集已经过面部检测的预处理                               | 使用VGG-Face、N-CNN、ViT分别训练预测属于“疼痛”的概率。 <br>使用可解释方法Grad-CAM<br>(GC) and Integrated Gradients (IG)对预测过程进行解释 |
| [[Improving Pain Classification using Spatio-Temporal Deep Learning .pdf]](2025-2-arxiv)                     | ConvNeXt 架构提取每帧的空间特征<br>STGCN提取每帧的时空特征       | 特征向量输入LSTM，训练预测是否疼痛                                                                                     |
| Multimodal AI techniques for pain detection: integrating facial gesture and paralanguage analysis（2025-0-B会） | 【视觉+音频】<br>opencv库提取面部关键点；<br>librosa库提取音频特征 | 利用时间戳同步两数据<br>CNN分析面部特征；LSTM分析时序音频特征                                                                    |

# 公开数据库
总结仓库：[A list of pain recognition databases that are publicly available for research](https://github.com/philippwerner/pain-database-list?tab=readme-ov-file)

| 名称                                                                                                                                    | 数据来源                                      | 数据规模                                                     | 注释/标签                                                                                       |
| ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------- | -------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| UNBC-McMaster shoulder pain database([[Automatic pain monitoring using the UNBC-McMaster shoulder.pdf]])<br>**似乎已经无法申请？**<br>疼痛：肩关节疼痛 | 129名**成人**（63名男性，66名女性）                   | 200个图像序列（总帧：48398；疼痛帧：8369）                              | 【帧级别】12个AU及其强度（A-E），66个面部标志，PSPI评分<br>【序列级别】通过VAS、感觉量表、情感动机量表进行自我报告或通过观察员评定疼痛强度（OPI）进行观察员报告 |
| BioVid Heat Pain Database<br>[申请页面](https://www.nit.ovgu.de/nit/en/BioVid-p-1358.html)<br>疼痛：急性热痛<br>                                 | 【A】<br>87例**成人**（44例男性20-64岁，43例女性20-65岁） | 8700次实验（疼痛6960），包含正面无遮挡视频+皮肤电反应（GSR）+心电图（ECG）+肌电图（EMG）   | 【序列级别】基线（无疼痛）+4个疼痛刺激强度水平                                                                    |
|                                                                                                                                       | 【B】<br>18- 65岁86名**成人**（42名男性，44名女性）      | 8600次实验（疼痛6880），包含面部有遮挡视频+GSR+ECG+斜方肌、皱眉肌和颧肌的肌电图（EMG）    | 【序列级别】基线（无疼痛）+4个疼痛刺激强度水平                                                                    |
|                                                                                                                                       | 【C】<br>18- 65岁87名**成人**（44名男性，43名女性）      | 87个视频（A部分的长版本，每个主题一个视频）包含正面视频+GSR+ECG+EMG+疼痛刺激标签         | 【片段级别】疼痛刺激                                                                                  |
| 疼痛：表演的疼痛和基本情绪                                                                                                                         | 【D】<br>90名成人                              | 630个1分钟视频                                                | 【片段级别】快乐、悲伤、愤怒、厌恶、恐惧、疼痛、中性                                                                  |
| Infant COPE                                                                                                                           | 足跟采血：18-72小时26例**新生儿**（13例男性，13例女性）       | 204张面部图像（疼痛图像：60张）                                       | 【帧级别】疼痛、哭泣、脚跟摩擦、鼻空气刺激、休息                                                                    |
| FENP                                                                                                                                  | 2天-4周106名**新生儿**                          | 4种分类各2750张图像                                             | 【帧级别】剧痛、轻度疼痛、哭泣、平静                                                                          |
| MintPAIN<br>[申请页面](https://vap.aau.dk/mintpain-database/)                                                                             | 电刺激：20名**成人**                             | 3200个帧序列（`20*2`次实验，每次实验40次疼痛刺激生成80个文件夹）且包含RGB、深度、热成像三个模态 | 【序列级别】基线（无疼痛）+4个疼痛刺激强度水平                                                                    |

# think
- 不同个体之间对痛苦耐受程度不同，需要对不同个体的差异有适用性。
- 疼痛和其他负面情绪都会影响面部表情，但疼痛具有独特的模式，应当可以将其与其他进行区分。
- PD主要有两个方面进行创新：特征提取和评估方式。面部位置检测如今应该比较成熟，不好创新。