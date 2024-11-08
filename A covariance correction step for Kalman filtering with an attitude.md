# A covariance correction step for Kalman filtering with an attitude
# 带姿态的卡尔曼滤波的协方差校正步骤

This paper derives a reset step which adjusts the covariance matrix when information is moved from the attituide deviation to the reference attitude.
(When combined with the extended or unscented Kalman filter prediction and measurement steps, the reset allows one to easily construct a Kalman filter for a system whose state includes an attitude.)
本文推导出一个重置步骤，当信息从姿态偏差移动到参考姿态时，该步骤会调整协方差矩阵

This reset step is derived by tracking mean and covariance through a linearization, similarly to an extended Kalman filter prediction step. The reset step is validated using Monte Carlo sampling.
此重置步骤是通过线性化跟踪均值和协方差得出的，类似于扩展的卡尔曼滤波器预测步骤。重置步骤使用蒙特卡洛采样进行验证。

To propose an alogorithm which allows estimation of the dynamic state of a system (where the state inlcudes an attitude), by making use of a reference attitude and an attitude error. When based on the extended Kalman filter, the result is an extension to and correction of the MEKF; and when based on the Unscented Kalman filter, it may be seen as a correction of the USQUE. The algorithm may be directly applied to systems with arbitrarily complicated dynamics, including, for example, angular velocity dynamics dependent on other states.
提出一种算法，利用参考姿态和姿态误差来估计系统的动态状态（其中状态包括姿态）。当基于扩展卡尔曼滤波器时，结果是对 MEKF 的扩展和校正；当基于无迹卡尔曼滤波器时，它可以看作是对 USQUE 的校正。该算法可以直接应用于具有任意复杂动态的系统，例如，包括依赖于其他状态的角速度动态。
