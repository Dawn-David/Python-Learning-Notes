Pytorch指定GPU的方法
===

改变系统变量
---

1. 改变系统环境变量仅使目标显卡,编辑 .bashrc文件，添加系统变量

    ```python
    export CUDA_VISIBLE_DEVICES=0
    #这里是要使用的GPU编号
    ```

2. 在程序开头设置

    ```python
    os.environ["CUDA_VISIBLE_DEVICES"] = '0,1,2,3'
    ```

3. 在运行程序时指定

    ```shell
    # 运行程序时使用命令行,来设置该程序可见的gpu:
    CUDA_VISIBLE_DEVICES=0,1,2,3 python xxx.py
    ```

使用torch.cuda接口
---

```python
# 在生成网络对象之前执行
torch.cuda.set_device(0)
```

使用pytorch的并行GPU接口
---

```python
model = torch.nn.DataParallel(model, device_ids=[0])
```

初始化模型时
----

```python
model = Model.cuda(0)
```
