## Introduction (one page for abstract +introduction)

- the background of sensing using  mmwave or other wirless signals (from border area to 3d human bandody)
  - the mmwave is gaining popularity in some areas( list the areas, e.g. autonomous driving, ....) due to 主要介绍毫米波雷达相较于其他传感器在感知领域的优点（距离，多普勒，穿透性，光照，隐私），列举现有的无线信号恢复人体的工作（Wi-Fi，RF，mmWave）
  - list works using mmwave, wifi, rf in different areas (one or two sentences) e.g. car imaging, action recognition, breath detection,location ....
- point out there is little/only limited work in the 3D human body reconstruction 
  - it's unclear how accurate mmwave can reconstruct human body from ... 1)毫米波雷达信号恢复的骨骼和mesh能达到多高的精度,  2)和深度信息相比，3) 雷达信号恢复的骨骼和mesh精度有多高，有哪些优越性统RGB图片效果较差的情况下（雨雾天、烟），毫米波信号恢复的骨骼和mesh能达到多少精度
  - why? noise data, hard to collect data ....
- to bridge the gap or overcome the limit, we introduce a large scale mmwave 3d recontruction data and how we answer the above three questions.
  -  introduce a large scale mmwave 3d reconstruction data 
    介绍为什么使用毫米波雷达采集人体数据（motivation）介绍现有的毫米波雷达的数据集，都是关于自动驾驶中检测车和行人的，只有一个数据集是动作分类，列举我们数据集相对于这些数据集的优点，包括采集对象的多样性，包含不同的身高、体型、性别；采集环境的多样性，包含室内、室外、各种天气等情况
  - how we answer the above three questions
    介绍通过雷达点云恢复pose和mesh的baseline，并且对比和rgb、rgbd、depth恢复的mesh在不同场景下（雨、烟、雾）和不同距离下的效果
- ~~*<u>介绍怎么采集，有哪些难点，包含校准，同步，室内室外不同情况如何采集等 （no need here, explain in the method part)</u>*~~
- summarize our contribution in short列一下贡献，包括：
  - 提出一个覆盖场景广、动作多样、对象多样的毫米波人体数据集
  - 回答毫米波雷达信号恢复的骨骼和mesh能达到多高的精度
  - 回答和深度信息相比，雷达信号恢复的骨骼和mesh精度有多高，有哪些优越性
  - 回答在传统RGB图片效果较差的情况下（雨雾天、烟），毫米波信号恢复的骨骼和mesh能达到多少精度

Select samples, including radar point cloud, skeleton(may be there is not need) and mesh,  from our datasets and compose them into one big figure and make it as the main figure in front of the introduction section (@xiangyu, try to make the data samples more beautiful, for example, change the line thickness and color of the skeleton, the shading of the mesh etc. )

## Related works(one page )

- 介绍使用无线信号恢复骨骼或mesh的文章，explain why they cannot answer three questions our mentioned, or can only partially answer (very important)
- ~~介绍目前常用的用于人体重建的数据集获得的方法，并分析它们的优缺点（这一部分可以不说明毫米波雷达）(no need to introduce in a separate paragraph )~~
- 介绍现有的关于毫米波雷达的数据集(introduce a few work about imaging, detection etc. but work related to action recognition, skeleton/mesh estimation is our focus)，并将我们的数据集与他们对比(check if we can summarize them in a table)，说明我们的数据集优势在哪里.(very important)
- 介绍现有的经典的rgb和rgbd恢复骨骼或mesh的文章

## Human Mesh Annotation 

##### 装置介绍   Annotation system

- 介绍毫米波雷达arbe (explain mechanism of mmwave radar in several sentences, more details in supplementary materials, or point  our a reference for readers to get more information about it)
- optitrack azure kinect (one or two sentences is enough, add refence or website links, mentioned their location accuracy reported in their document)
- 介绍整套系统 (put two pictures, one for the 3d printing holder for mmwave radar and kinect; one for the whole system, or draw a sketch for our configuration )
- two ways to get the annotations (optitrack and kinect)

##### Mesh annotation by model fitting

- ~~对原始数据进行处理与提取：mkv => 彩色，深度，点云，骨骼 (no need, put in supplementary material)~~

- 拟合：骨骼+点云 => mesh (important)

- ~~数据存储格式与包含信息 (no need,  put in supplementary material)~~

  **How accurate is our ground truth from kinect** (provide figures, table, very important)

##### 采集流程(important)  Time Synchronization and Coordinate Calibration

- 坐标变换：相机校准、雷达与人体追踪设备校准；(need to give a figure, or estimate how accurate is our calibration)
- 时间同步：如何调整各设备的时间偏移 (need to give a figure, or estimate how accurate is our synchronization)

Build a Complete and Concise Benchmark (may change the wording later)

- shape space (figure or table)
- pose space 采集内容：包含动作及分类，参与采集人群特征 (how to show the coverage of subject shapes and poses? PCA, tsne visualization? specify the figures we will put for this section)
- environment varations 环境控制：室内室外如何采集，包含哪些场景，如何控制烟雾、降雨等特殊环境 

two (plus half)  pages

## Analysis

- 实验数据的预处理（describe using symbols, try to follow the conventions in other papers, for example, J for all joints J={j}, j= 0....N) (one paragraph, 5-8 sentences)

- Methods, 

  1) describe all the methods(one sentence for one method. ) we used and 
  2) why we use them(their performance, some function suitable for radar point could etc.) . (one paragraph,5-8 sentences). 
  3) how we use them: p4T和PointLSTM对毫米波点云的处理方法，，对比模型的输入输出，(分析取不同帧数、不同球半径r_s、t_s等情况的网络效果, no need to go into details, i.e. analysis, just show the hyperparameters setting we have used）

-  Q1: 整体性能对比 毫米波雷达信号恢复的骨骼和mesh能达到多高的精度  ( how to analysis?  give more details here before writing. )

  - for example, to show the overall performance, show the CDF for the mean/max/median for all the joints, histograms for each joint; refer some hand pose, body pose reconstruction papers for metrics and ways to show the results.
  - 分析不同动作的数据的恢复效果
  - in difference scenarios

- Q2 and Q3: mmWave vs Depth and RGB (or Comparison for reconstructions from different sensors)

  - compare reconstruction results from radar point cloud and kinect point cloud. 描述相对于信息量更丰富的depth和rgbd恢复骨骼和mesh的，
    - 毫米波点云在远距离或有雨、烟、雾等干扰的情况下效果更优的实验，分析毫米波点云优于depth和rgbd的原因
  - compare reconstruction results from  radar point cloud and kinect point cloud+rgb 描述相对于传统的rgb恢复骨骼和mesh的网络，毫米波点云网络在不同浓度雨、烟、雾和不同光照下（晚上）的表现更优的实验，分析毫米波点云优于rgb的原因
  - compare reconstruction results from radar point cloud and kinect point cloud+rgb

  

Conclusion

summarize our contribution and finding

limitation of our dataset

总结基于点云重建人体mesh和骨骼点所存在的优势，同时描述毫米波信号的挑战，数据集对于未来点云重建人体发展的必要性和贡献
