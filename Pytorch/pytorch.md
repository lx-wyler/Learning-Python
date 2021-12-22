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

# PyTorch自动微分



