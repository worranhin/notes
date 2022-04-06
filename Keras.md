# Keras

Keras 是用 [[Python]] 写的高级神经网络 API，支持 [[TensorFlow]] 、[[CNTK]]、[[Theano]] 作为后端运行，同时它也是 TensorFlow 官方推荐的 API.



## layers

### Dense

- relu：将负值归零
- sigmoid：输出 0 ~ 1 的概率

## 二分类问题

- 带 relu 的 Dense
- 最后一层用 sigmoid 激活的 Dense
- rmsprop 优化器
- 注意过拟合问题