# paper-read-list

1. [ScopeNet](https://arxiv.org/abs/2005.04854)  (2020.7.9)

  算法将anchor引入到anchor-free算法以解决anchor-free算法对于位置定位不准确的问题。基于anchor-free的算法在回归时，回归长宽相对于整张图片的比值，对于大目标检测效果不好。

···
  Despite the simplicity, they achieve comparable or even better performances than anchor-based methods.
  However, these anchor-free methods rely on a single regression network for predicting a precise location
  in the unbounded space, which can be excessively challenging for the network.

  Since a single regression network may not be capable to effectively handle the unbounded prediction space,
  it is natural for us to consider restricting the range of the regression.
···

  算法结构图如下：
  <div style="color:#0000FF" align="center">
  <img src="/image/scopenet.png"/>
  </div>

  在定位目标坐标时，通过scope head中的bin classification预测目标四条边的目标长度，然后再借助于border regression对检测框进行精调。

2. [Dual Super-Resolution Learning for Semantic Segmentation](https://openaccess.thecvf.com/content_CVPR_2020/papers/Wang_Dual_Super-Resolution_Learning_for_Semantic_Segmentation_CVPR_2020_paper.pdf)  (2020.7.9)

将超分任务作为辅助任务引入到分割框架中，采用多任务的形式辅助训练，推断时无需超分任务。

3. [Learning Dynamic Routing for Semantic Segmentation](https://github.com/yanwei-li/DynamicRouting)  (2020.7.12)

基于数据驱动的多尺度特征融合方式（很明显，这种方式在训练过程中吃显存吃的很厉害）。

4. [Gliding vertex on the horizontal bounding box for multi-oriented object detection](https://github.com/MingtaoFu/gliding_vertex)  (2020.9.3)

文章基于遥感目标中的角点序列检测问题，通过改变框的表示方式，避免排序问题（By limiting the offset on the corresponding side of horizontal bounding box, we may facilitate offset learning and also avoid the confusion for sequential label points in directly regressing the four vertices of oriented objects.）。恩张采用Faster RCNN结构，只是在预测时增加了五个预测结构。

<div style="color:#0000FF" align="center">
<img src="/image/gliding_vertex.png"/>
</div>

论文针对每个目标，针对每个水平的bounding box增加了四个角点的偏移量<a href="https://www.codecogs.com/eqnedit.php?latex=\alpha_{1},\alpha_{2},\alpha_{3},\alpha_{4}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\alpha_{1},\alpha_{2},\alpha_{3},\alpha_{4}" title="\alpha_{1},\alpha_{2},\alpha_{3},\alpha_{4}" /></a>，另外预测r，当r小于某一阈值时，偏移量才起作用。

5. [PolarMask: Single Shot Instance Segmentation with Polar Representation](https://github.com/xieenze/PolarMask)  (2020.9.8)

在Anchor-Free框架FCOS的基础上，基于极坐标系建模轮廓，把实例分割问题转化为实例中心点分类（instance center classification）问题和密集距离回归（dense distance regression）问题。提出Polar CenterNess和Polar IoU Loss，用于优化实例中心点以及极坐标位置。在没有使用任何tricks的情况下，PolarMask在ResNext 101的配置下在coco-test-dev上取得了32.9 mAP。

6. [Cross-view Semantic Segmentation for Sensing Surroundings] (2020.11.9 周博磊组的论文)

跨视角分割任务，设计视角转化模块，将前视视角的feature map转化成top-to-down俯视视角，进而采用domain adaptation的思路进行训练。

7. [Geometry-Aware Symmetric Domain Adaptation for Monocular Depth Estimation]( https://github.com/sshan-zhao/GASDA)  (2020.9.8)

将domain adaptation 和深度估计相结合，设计Geometry Consistency Loss等五种Loss, 估计训练并非易事。
