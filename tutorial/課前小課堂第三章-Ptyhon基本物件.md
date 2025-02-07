## Python基本物件
這章節將進一步解釋以下四者
- list : [ ]
- tuple : ( )
- set : { }
- dict : { }


```python
#開始前記得先run這個cell
# -*- coding: utf-8 -*-
from platform import python_version

print("Python version: {}".format(python_version()))
%autosave 120
```

    Python version: 3.9.5
    



    Autosaving every 120 seconds
    

## List 列表
list 是一種可以儲存多個資料的容器，這些資料可以是任何型別，例如整數、字串、浮點數、布林值，甚至是其他列表


```python
# 一般的list
my_list = [1, 2, 3, 4, 5]

# list包含不同類型的資料
mixed_list = [1, "Hello", 3.14, True, [1,2,3]]
```

### 存取列表中的元素
列表中的每個元素都有一個編號，稱為「索引」（index)，Python 的索引 **<font color=#FF0000>從 0 開始</font>** (非常重要)<br>
- 正索引從 0 開始
- 負索引從 -1 開始


```python
# 今天我有三種水果在桌上，有兩個水果被放在另一個籃子中
fruits = ["apple", "banana", "cherry", ["watermelon", "orange"]]

# 取得桌上第一個水果會是apple
print(fruits[0])  

# 取得桌上第二個水果會是banana
print(fruits[1])  

# 取得桌上倒數第二個水果會是cherry
print(fruits[-2])

# 取得籃子中第一個水果會是watermelon
# 如果 list 中有 list ，那就就構成了「多維列表」
# 讀取元素時如果有第二層，就就在原先的中括號後面多一個中括號，這就能讀取第二層的元素
print(fruits[3][0])  
```

    apple
    banana
    cherry
    watermelon
    

### 取出列表範圍中的元素
1.```slice()``` 函式可以取出 list 中某個範圍的元素，也可以使在中括號裡加上冒號```:```來指定範圍<br>
    ```[頭:尾]``` 口絕 : 取頭不取尾<br>
2. 使用兩個冒號```[::]```，表示要**間隔幾個項目**取值


```python
# 1. slice
a = [0,1,2,3,4,5,6,7,8,9]
b = a[:3] # 取範圍0到2
c = a[3:] # 取範圍從3開始到最後
d = a[1:3] # 取第1到3之前(不含3)
e = a[-5:-2] # 取-5到-2(不含-2)
print(b)   
print(c)   
print(d)   
print(e)   
```

    [0, 1, 2]
    [3, 4, 5, 6, 7, 8, 9]
    [1, 2]
    [5, 6, 7]
    


```python
# 2. 表示間隔幾個項目取值
a = [0,1,2,3,4,5,6,7,8,9]
b = a[::3] # 每隔三項目取值
c = a[3::2] # 從第三個項目開始，每隔兩項目取值
d = a[::-1] # 反轉串列
e = a[::-2] # 反轉串列，每隔兩個項目取值
print(b)   
print(c)   
print(d)   
print(e)   
```

    [0, 3, 6, 9]
    [3, 5, 7, 9]
    [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
    [9, 7, 5, 3, 1]
    

### 更改列表中的元素
1. **修改**指定索引中的值
2. **新增**元素到列表中
3. **刪除**列表中我不要的元素
4. **slice 範圍修改**索引中的值


```python
# 1. 修改
# 今天我有三種水果
fruits = ["apple", "banana", "cherry"]

# 但第二個其實不是香蕉，而是橘子
# 那就修改 list 中第"1"個值為橘子 
fruits[1] = "orange"
print(fruits)  # 輸出：['apple', 'orange', 'cherry']
```

    ['apple', 'orange', 'cherry']
    


```python
# 2. 新增
# 今天我有三種水果
fruits = ["apple", "banana", "cherry"]

#我阿嬤又給我一顆橘子
#可以使用 append() 在列表末尾新增元素
fruits.append("orange")
print(fruits) # 輸出：['apple', 'banana', 'cherry', 'orange']

#也可以使用 insert() 將新元素新增在指定位置
fruits.insert(1, "watermelon")
print(fruits) # 輸出：['apple', 'watermelon', 'banana', 'cherry', 'orange']
```

    ['apple', 'banana', 'cherry', 'orange']
    ['apple', 'watermelon', 'banana', 'cherry', 'orange']
    


```python
# 3. 刪除
# 今天我有五種水果
fruits = ['apple', 'watermelon', 'banana', 'cherry', 'orange']

#假如今天我把cherry吃掉了
#可以使用 remove() 刪除指定的值
fruits.remove("cherry")
print(fruits)  # 輸出： ['apple', 'watermelon', 'banana', 'orange']

#假如今天我把 list 中第"1"個水果吃掉了
#可以使用 pop() 刪除指定索引的值
fruits.pop(1)
print(fruits) # 輸出： ['apple', 'banana', 'orange']

#也可以用 del 刪除指定索引的值
del fruits[0]
print(fruits) # 輸出： ['banana', 'orange']

#可以用 clear() 清空整個list
fruits.clear()
print(fruits)
```

    ['apple', 'watermelon', 'banana', 'orange']
    ['apple', 'banana', 'orange']
    ['banana', 'orange']
    []
    


```python
# 3. slice 範圍修改
# 今天我有五種水果
fruits = ['apple', 'watermelon', 'banana', 'cherry', 'orange'] 
# 我有拿了 watermelon, banana, cherry 三樣東西和姊姊換了三顆 strawberry
fruits[1:4] = ['strawberry', 'strawberry', 'strawberry']
print(fruits) # 輸出： ['apple', 'strawberry', 'strawberry', 'strawberry', 'orange']

# 指定更換的項目的數量，不一定要和原本的一樣多 ( 可以比較少，也可以比較多 )，更換後會將範圍的內容，完全換成新的內容
# 我有拿了三顆 strawberry(index 1,2,3 ) 和姊姊換了2顆 strawberry 和2顆 banana
fruits[1:4] = ['strawberry', 'strawberry', 'banana', 'banana']
print(fruits)

# 更換的內容不一定要是串列，只要是可以「迭代」的內容都可以，字串或之後會提的元組都可以
a = ['a','b','c','d','e']
a[1:4] = 'hello'
print(a)
```

    ['apple', 'strawberry', 'strawberry', 'strawberry', 'orange']
    ['apple', 'strawberry', 'strawberry', 'banana', 'banana', 'orange']
    ['a', 'h', 'e', 'l', 'l', 'o', 'e']
    

### 檢查元素是否在列表中
使用```in```來搜尋關鍵字是否有在列表中<br>
- 如果關鍵字<font color=#0000FF>存在</font>於 list 中，回傳 **TRUE**<br>
- 如果關鍵字<font color=#0000FF>不存在</font>於 list 中，回傳 **FALSE**


```python
fruits = ["apple", "banana", "cherry"]

#尋找 apple 是否有在 list 中
print("apple" in fruits)  # 輸出：True

#尋找 watermelon 是否有在 list 中
print("watermelon" in fruits) # 輸出：False
```

    True
    False
    

### 列表排序
- 使用```sort()``` 進行排序（這會改變原列表）<br>
- 使用```sorted()``` 進行排序（不改變原列表）


```python
#使用 sort() 來做排序，使用後 list 的排序也會被更動
numbers = [3, 1, 4, 1, 5]
numbers.sort()
print(numbers)  # 輸出：[1, 1, 3, 4, 5]
```

    [1, 1, 3, 4, 5]
    


```python
#使用 sorted() 來做排序，使用後 list 的排序不會被更動，第二個輸出可以證明這點
numbers = [3, 1, 4, 1, 5]
sorted_numbers = sorted(numbers)
print(sorted_numbers)  # 輸出：[1, 1, 3, 4, 5]
print(numbers)         # 輸出：[3, 1, 4, 1, 5]
```

    [1, 1, 3, 4, 5]
    [3, 1, 4, 1, 5]
    

### 遍歷列表
使用```for```可以逐一訪問列表中的元素


```python
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    print(fruit)
# 輸出：
# apple
# banana
# cherry
```

    apple
    banana
    cherry
    

### 合併列表
兩個 ```list```  合併在一起，有兩種方法<br>
- 使用 ```+``` 在 + 號右方的串列，會加在左方串列的後方
- 使用 ```extend()``` 一個串列的後方，合併另外一個串列的內容


```python
# 使用 + 來合併
# 我有三種水果，我阿嬤有兩種水果
me = ["apple", "banana", "cherry"]
grandma = ["watermelon", "orange"]
#我們兩個合併在一起就是我們家所有的水果
home = me + grandma
print(home) # 輸出：['apple', 'banana', 'cherry', 'watermelon', 'orange']
```

    ['apple', 'banana', 'cherry', 'watermelon', 'orange']
    


```python
# 使用 extend() 來合併
# 我有三種水果，我阿嬤有兩種水果
me = ["apple", "banana", "cherry"]
grandma = ["watermelon", "orange"]
#我給阿嬤我所有的水果，我的水果被合併到阿嬤的list中
grandma.extend(me)
print(grandma)
print(me)

#需注意的extend會改變list，但不會回傳list的值
#所以當寫成跟上面 home = me + grandma 會得到 None 的結果
home = grandma.extend(me)
print(home)
```

    ['watermelon', 'orange', 'apple', 'banana', 'cherry']
    ['apple', 'banana', 'cherry']
    None
    

## Tuple 元組
元組是用來存放多個資料的有序集合，與列表一樣可以存放不同型別的資料，但元組的內容一旦建立就<font color=#FF0000>無法改變</font><br>
元組使用小括號 ```()``` 定義，裡面的元素用逗號 ```,``` 分隔<br>

|    特性    |      tuple       |      list       |
|:--------:|:----------------:|:---------------:|
|   可修改性   |       不可變        |       可變        |
|    語法    | 	使用小括號 ```()```  | 使用方括號 ```[]```  |
|   使用場景   |   適合保存不需要改變的資料   |   適合需要頻繁修改的資料   | 

單一元素的元組必須加上逗號``` ,```，否則會被視為普通的資料類型<br>
tuple使用方法和list大致相同，下方就不贅述tuple使用方式


```python
# 建立一個元組
my_tuple = (1, 2, 3)

# 元組可以包含不同類型的資料
mixed_tuple = (1, "Hello", 3.14, True, [1,2,3])

#單一元素的元組必須加上逗號 ,，否則會被視為普通的資料類型
single_element_tuple = (42,)  # 注意逗號
not_a_tuple = (42)  # 這只是整數
print(type(single_element_tuple))  # <class 'tuple'>
print(type(not_a_tuple))  # <class 'int'>

# 使用 tuple() 函數轉換成元組
my_list = [1, 2, 3]
my_tuple = tuple(my_list)
print(my_tuple)  # 輸出：(1, 2, 3)

# 強制修改tuple
# 使用串列 list 存取 tuple 資料，修改資料後，再轉換為新的 tuple
a = ('apple','banana','orange')
b = list(a)
b.append('grap')
a = tuple(b)
print(a) 
```

    <class 'tuple'>
    <class 'int'>
    (1, 2, 3)
    

## Dictionary 字典


```python

```
