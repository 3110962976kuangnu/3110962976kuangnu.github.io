```python
import pandas as pd
import matplotlib.pyplot as plt

# 假设 A 和 B 是你的大数据集
A = pd.Series(your_large_array_A)
B = pd.Series(your_large_array_B)

# 创建 DataFrame
df = pd.DataFrame({'A': A, 'B': B})

# 绘制折线图
df.plot(x='A', y='B')
plt.show()
``` 