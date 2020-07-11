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
