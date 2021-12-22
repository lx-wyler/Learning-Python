# 1. PyTorch张量基础操作

> 1. 构造一个m×n矩阵，不初始化
>
>    ```x = torch.empty(m, n)```  # 
>
> 2. 构造一个随机初始化的矩阵
>
>    * ```x = torch.rand(m, n)```  # 好像是从0-1的均匀分布中随机抽样
>    * ```x = torch.randn(m, n)```  # 从标准正态分布中随机抽样
>
>    - ```x = torch.normal(means, std, out=None)```  # 返回一个张量，包含了从指定均值和标准差的离散正态分布中抽取的一组随机数
>
>    - ```x = linspace(start, end ,steps=100, out=None)```  # 返回一个1维张量，包含在区间start和end上均匀间隔的step个点，张量长度由steps决定
>
> 3. 构造一个矩阵全为0，且数据类型是long
>
>    ```x = torch.zeros(m, n, dtype=torch.long)```  # 
>
> 4. 构造一个张量，直接使用数据
>
>    - ```x = torch.tensor([5, 2])```  # 该例子里是构造一个1×2的矩阵
>
>    - ```x = torch.tensor([[3, 2], [4, 2]])```  # 该例子构造一个2×2的矩阵
>
> 5. 创建一个tensor基于已经存在的tensor
>
>    ```x = x.new_ones(m, n, dtype=torch.double)```  **# 后续需要细究**
>
>    ```x = torch.randn_like(x, dtype=torch.float)```  **# 同上**
>
> 6. 获得一个张量的维度信息
>
>    ```print(x.size())```
>
> 7. 张量的加法操作
>
>    - ```python
>      x = torch.rand(m, n)
>      y = torch.rand(m, n)
>      print(x + y)
>      ```
>
>    - ```print(torch.add(x, y))```
>
>    - ```python
>      result = torch.empty(m, n)
>      torch.add(x, y, out=result)
>      print(redult)
>      ```
>
>    - ```y.add_(x)```  # 将x加到y上，并且会改变y
>
>    - **有后缀"_"的都会使张量发生变化**
>
> 8. 可以使用标准的Numpy类似的引导操作
>
>    ```print(x[:, 1])```  # 打印x的第2列
>
> 9. 改变张量的大小
>
>    ```python
>    x = torch.randn(4, 4)
>    y = x.view(16)
>    z = x.view(-1, 8)  # -1表示从其他维度来推测
>    # 自己的理解：把原来的（x）数据按照新的维度来进行填充
>    ```
>
> 10. 如果有个元素tensor，使用.item()获得这个value
>
>     ```python
>     x = torch.randn(1)
>     print(x)
>     print(x.item())
>     ```

# 2. PyTorch自动微分

> 1. 创建一个张量，设置requires_grad=True来追踪与它相关的计算
>
>    ```x = torch.ones(m, n, requires_grad=True)```
>
>    **！！一个在运算过程中创建的张量会有和来源处张量相同的属性**
>
> 2. ```.requires_grad_(True/False)```会改变张量的```requires_grad```标记。默认是False
>
>    ```python
>    a = torch.randn(m, n)
>    a = ((a * 3) / (a - 1))  # 此时a.requires_grad为False
>    a.requires_grad_(True)  # 此时为True
>    b = (a * a).sum()  # b也为True
>    ```
>
> 3. 向后传播，举个栗子
>
>    ```python
>    import torch
>    
>    x = torch.ones(2, 2, requires_grad=True)  # x是一个全为1的2×2矩阵
>    y = x + 2  # y = x + 2
>    z = y * y * 3  # z = 3 (x + 2) ^ 2
>    out = z.mean()  # out = 1 / 4 * 3 (x + 2) ^ 2
>    out.backward()  # 这一步以后，就求了out对x的导数，存在x.grad中
>    print(x.grad)  # 每有一步.backward()，就会将结果累计在x.grad中，所以如果要用每一步的结果就必					须要将x.grad清空
>    ```
>
>    **只有标量才能执行```.backward()```!!!!**
>
> 4. 雅克比向量积的栗子
>
>    ```python
>    x = torch.randn(3, requires_grad=True)
>    y = x * 2
>    while y.data.norm() < 1000:
>        y = y * 2
>    # 上面这个while中，y.data.norm()表示y的L2范数，就是y中所有元素，每个平方，然后加起来再开方
>    print(y)
>    # 此时y不是标量，无法直接计算整个雅克比，但只想要雅克比向量积的话，只要简单的传递向量给backward作为参数即可
>    v = torch.tensor([0.1, 1.0, 0.0001], dtype=torch.float)
>    y.backward(v)
>    print(x.grad)
>    # 后面这一段没怎么看懂（2021年12月22日）
>    ```
>
> 5. 可以将代码放在with torch.no_grad()中来停止自动求导
>
>    ```python
>    print(x.requires_grad)
>    print((x ** 2).requires_grad)
>    with torch.no_grad():
>        print((x ** 2).requires_grad)
>    # 输出结果是T T F
>    ```





