# A covariance correction step for Kalman filtering with an attitude
# 带姿态的卡尔曼滤波的协方差校正步骤

This paper derives a reset step which adjusts the covariance matrix when information is moved from the attituide deviation to the reference attitude.
(When combined with the extended or unscented Kalman filter prediction and measurement steps, the reset allows one to easily construct a Kalman filter for a system whose state includes an attitude.)
本文推导出一个重置步骤，当信息从姿态偏差移动到参考姿态时，该步骤会调整协方差矩阵

This reset step is derived by tracking mean and covariance through a linearization, similarly to an extended Kalman filter prediction step. The reset step is validated using Monte Carlo sampling.
此重置步骤是通过线性化跟踪均值和协方差得出的，类似于扩展的卡尔曼滤波器预测步骤。重置步骤使用蒙特卡洛采样进行验证。

To propose an alogorithm which allows estimation of the dynamic state of a system (where the state inlcudes an attitude), by making use of a reference attitude and an attitude error. When based on the extended Kalman filter, the result is an extension to and correction of the MEKF; and when based on the Unscented Kalman filter, it may be seen as a correction of the USQUE. The algorithm may be directly applied to systems with arbitrarily complicated dynamics, including, for example, angular velocity dynamics dependent on other states.
提出一种算法，利用参考姿态和姿态误差来估计系统的动态状态（其中状态包括姿态）。当基于扩展卡尔曼滤波器时，结果是对 MEKF 的扩展和校正；当基于无迹卡尔曼滤波器时，它可以看作是对 USQUE 的校正。该算法可以直接应用于具有任意复杂动态的系统，例如，包括依赖于其他状态的角速度动态。

The proposed algorithm uses these rewritten equations and is based on the extended Kalman filter, and introduces two additional steps to correct the attitude error statistics, so that the recursive estimation strategy then consists of four steps.
所提出的算法使用这些重写的方程，并基于扩展卡尔曼滤波器，并引入两个额外的步骤来校正姿态误差统计，使得递归估计策略由四个步骤组成。
1. A kalman prediction step, that uses the process equation (12) to propagate the estimate through the dynamics. During this step, the reference attitude is unchanged. 
1. 卡尔曼预测步骤，使用过程方程 (12) 通过动态传递估计值。在此步骤中，参考姿态保持不变。

2.A prediction reset step, where the reference attitude is changed such that the estimate of the post-reset attitude error equals zero, i.e. it is maximally far from its singularities.
2. 预测重置步骤，其中参考姿态被改变，使得重置后姿态误差的估计等于零，即它最大程度地远离其奇点。

3.A Kalman measurement update, that uses the measurement model(13) to correct the estimate with a given measurement. During this step, the reference attitude is again unchanged.
3. 卡尔曼测量更新，使用测量模型 (13) 通过给定测量来校正估计。在此步骤期间，参考姿态再次保持不变。

4.A measurement reset step, where again the reference attitude is adapted such that the estimate of the post-reset attitude error is reset to zero.
4. 测量重置步骤，其中再次调整参考姿态，使得重置后姿态误差的估计重置为零。

## Attitude error reset

The reset step does not change the actual attitude in the estimate, but modifies the reference attitude R<sub>ref</sub> so that the post-reset estimate of the attitude random vatiable δ is zero, is maximally far away from its singularities. 
重置步骤不会改变估计中的实际姿态，但会修改参考姿态R<sub>ref</sub>，使得姿态随机变量 δ 的重置后估计为零，即最大程度地远离其奇点。

**Problem 1.** Let the pre-reset reference attitude be R<sub>ref,pre</sub>, and the pre-reset attitude error be δ<sub>pre</sub> with associated mean and covariance:
<div align="center">
  <img src = "https://raw.githubusercontent.com/Yuan-Mingkang/Notes/bef6eca5a5239e20a2f2b964c859303578fa5e53/images/QianJianTec1731054980514.svg" alt="(14)" />(14)
</div>
<div align="center">
  <img src = "https://github.com/Yuan-Mingkang/Notes/blob/main/images/QianJianTec1731056239359.svg" alt="(15)" />(15)
</div>


