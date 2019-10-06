### gradient
- gradient is a vector
- gradient是等高线的法线方向
###set the learning rate carefully
- 太小-迭代时间过长
- 太大-cannot find the minima
- if there are more than three parameters,you cannot
visualize this.
### adaptive learning rate (adagrad)
-  1/t decay: $\eta^t = \frac{\eta}{\sqrt{t+1}}$
- **vanilla gradient descent** | **adagrad**
- adagrad learning rate 之反差
- Larger gradient,lager step?|if there are more than two parameters,then no!
- best step is $\frac{|firstderivative|}{secondderivative}$|adagrad在不增加额外运算量的情况下用first derivative估算second derivative的大小
### stochastic gradient descent
- $L(\theta)$ 从考虑所有error之和改为仅仅考虑当前error
### feature scaling
- make diffrent features have the same scaling
- 等高线图为正圆形，update更容易效率更高
### gradient descent基于taylor series
eg:在等高线图上随机选取一点作为初始点，以其为圆心画圆，寻找满足是的loss function最小的点 $\theta=(\theta_1 ,\theta_2)$
$$L(\theta)=L(a,b)+\frac{\partial L(a,b)}{\partial \theta_1}(\theta_1-a)+\frac{\partial L(a,b)}{\partial \theta_2}(\theta_2-b)$$
设u= $\frac{\partial L(a,b)}{\partial \theta_1}$,v=$\frac{\partial L(a,b)}{\partial \theta_2}$,$\triangle \theta_1=(\theta_1-a)$,$\triangle \theta_2=(\theta_1-b)$,内积定义$a\cdot b=|a||b|cos(a,b)$。

$L(\theta)中L(a,b),u,v均为常数，故当(u,v)\cdot (\triangle \theta_1,\triangle \theta_2)最小时，可找到L(\theta)最小值。$

$要使内积最小，那么应使cos(a,b)=-1且|a|,|b|尽量大，也即a=-\eta b,其中\eta 为正常数，可以得到(\triangle \theta_1,\triangle \theta_2)=-\eta (u,v),化简可得(\theta_1,\theta_2)=(a,b)-\eta (u,v)$

上式即为gradient descent的原始公式，其中 $(u,v)=(\frac{\partial L(a,b)}{\partial \theta_1},\frac{\partial L(a,b)}{\partial \theta_2})$ 即为梯度。
