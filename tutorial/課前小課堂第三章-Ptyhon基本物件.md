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

    Python version: 3.9.13
    



    Autosaving every 120 seconds
    

## List 列表
---
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
---
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
    ('apple', 'banana', 'orange', 'grap')
    

## Dictionary 字典
---
字典可以放入字串、整數、浮點數、布林值、列表、tuple和字典，只要通過 <font color=#FF0000>Key</font> 就能查到對應的 <font color=#FF0000>Value</font> <br>




### 建立字典
Key 必須是"字串"，後必須加上"引號"，value 可以放各種資料型態，不同的 Key 要以 ```,```分開


```python
# dictionary_name = {'key' : value, 'key_1' : [value, value1, value2]}
supermarket = {"section_1" : '蘋果', 'section_2' : ['牛肉', '豬肉', '羊肉'], 'Number_of _visitors' : 50 }
print(supermarket)
print(type(supermarket))
```

    {'section_1': '蘋果', 'section_2': ['牛肉', '豬肉', '羊肉'], 'Number_of _visitors': 50}
    <class 'dict'>
    

建立字典也可以使用```dict()```來建立字典，並且有三中方式<br>
1. ```dict(Key = Value)```
    - Key 要遵守 Python 的命名規則，= 後方就一樣可以放入各種資料型態的 Value ，最後一樣要用 ```,```分隔不同的 Key 
2. 將兩個值的**二維 List** 或**二維 Tuple** 轉換為字典
3. 雙字元的字串轉為字典



```python
#第一種
# dictionary_name = dict(Key = Value, Key_1 = [value, value1, value2])
supermarket_1 = dict(section_1 = '蘋果', section_2 = ['牛肉', '豬肉', '羊肉'], Number_of_visitors = 100)
print(type(supermarket_1))
print(supermarket_1, '\n-------------------')

#第二種 (以list為範例)
supermarket_list = [['section_1', '蘋果'], ['section_2', ['牛肉', '豬肉', '羊肉']], ['Number_of_visitors', 150]]
supermarket_2 = dict(supermarket_list)
print(type(supermarket_2))
print(supermarket_2, '\n-------------------')

#第三種 
a_list = ['ab','cd','ef','gh']
a_dict = dict(a_list)
print(type(a_dict))
print(a_dict)
```

    <class 'dict'>
    {'section_1': '蘋果', 'section_2': ['牛肉', '豬肉', '羊肉'], 'Number_of_visitors': 100} 
    -------------------
    <class 'dict'>
    {'section_1': '蘋果', 'section_2': ['牛肉', '豬肉', '羊肉'], 'Number_of_visitors': 150} 
    -------------------
    <class 'dict'>
    {'a': 'b', 'c': 'd', 'e': 'f', 'g': 'h'}
    

### 讀取字典中的值
決定好 Key 就可以讀取對應的 Value


```python
#超市為例，第一區賣蘋果，第二區賣三種肉
supermarket_1 = dict(section_1 = '蘋果', section_2 = ['牛肉', '豬肉', '羊肉'], Number_of_visitors = 100)
#今天想知道第二區在賣甚麼，可以透過supermarket_1['section_2']來得知
section2_info = supermarket_1['section_2']
print(section2_info)
print(type(section2_info), '\n-------------------')

#今天想知道第二區的第一格在賣甚麼，可以透過supermarket_1['section_2'][0]來得知
section2_info_first = supermarket_1['section_2'][0]
print(section2_info_first)
print(type(section2_info_first))
```

    ['牛肉', '豬肉', '羊肉']
    <class 'list'> 
    -------------------
    牛肉
    <class 'str'>
    

除了上述的方法可以讀取字典中的值，也可以透過 ```get(Key)``` 來取得 Key 對應的 Value <br>
使用原本的方法時，如果沒有對應的 Key 在字典中，這將會發生錯誤，但如果是用 ```get``` 這個方法，如果找不到 Key ，那將會回傳 ```None```


```python
#超市為例，第一區賣蘋果，第二區賣三種肉
supermarket_1 = dict(section_1 = '蘋果', section_2 = ['牛肉', '雞肉', '羊肉'], Number_of_visitors = 150)
#今天想知道第二區在賣甚麼，可以透過supermarket_1.get('section_2')來得知
section2_info = supermarket_1.get('section_2')
print(section2_info)
print(type(section2_info), '\n-------------------')

#今天想知道第三區在賣甚麼，邏輯推理上可能可以使用supermarket_1.get('section_3')，但 supermarket_1 中 section_3 其實不存在，所以將會回傳 None
section2_info = supermarket_1.get('section_3')
print(section2_info)
print(type(section2_info), '\n-------------------')
```

    ['牛肉', '雞肉', '羊肉']
    <class 'list'> 
    -------------------
    None
    <class 'NoneType'> 
    -------------------
    

### 修改字典中的值
方法有兩種，這兩者當遇到不存在於字典中的 ```Key``` 時，他們都會將新的 ```Key``` 和 ```Value``` 加入到字典當中<br>
1. 中括號 [```Key```] = ```Value```
2. setdefault(```Key```, ```Value```)



```python
#方法一
#超市為例，第一區賣蘋果，第二區賣三種肉
supermarket_1 = dict(section_1 = '蘋果', section_2 = ['牛肉', '雞肉', '羊肉'], Number_of_visitors = 150)
#當今天超市新增第一區改賣鳳梨
supermarket_1['section_1'] = '鳳梨'
print(supermarket_1['section_1'])
print(type(supermarket_1['section_1']), '\n-------------------')

#當今天超市新增第二區多賣豬肉
supermarket_1['section_2'].append('豬肉')
#supermarket_1['section_2']就是個list，所以直接使用append()來修改原本的list
print(supermarket_1['section_2'])
print(type(supermarket_1['section_2']), '\n-------------------')

#當今天超市新增第三區要賣蔬菜
supermarket_1['section_3'] = ['高麗菜','菠菜','茼蒿']
print(supermarket_1['section_3'])
print(type(supermarket_1['section_3']))
```

    鳳梨
    <class 'str'> 
    -------------------
    ['牛肉', '雞肉', '羊肉', '豬肉']
    <class 'list'> 
    -------------------
    ['高麗菜', '菠菜', '茼蒿']
    <class 'list'>
    


```python
#方法二
#超市為例，第一區賣蘋果，第二區賣三種肉
supermarket_1 = dict(section_1 = '蘋果', section_2 = ['牛肉', '雞肉', '羊肉'], Number_of_visitors = 150)
#當今天超市新增第一區改賣鳳梨
section1_info = supermarket_1.setdefault('section_1', '鳳梨') 
print(section1_info)
print(type(section1_info), '\n-------------------')

#當今天超市新增第三區要賣蔬菜
supermarket_1.setdefault('section_3', ['高麗菜','菠菜','茼蒿'])
section3_info = supermarket_1.get('section_3')
print(section3_info)
print(type(section3_info))
```

    蘋果
    <class 'str'> 
    -------------------
    ['高麗菜', '菠菜', '茼蒿']
    <class 'list'>
    

### 刪除字典中的值
1. ```del```
    - del[```Key```] 是刪除特定 Key 的 Value
    - del dictionary_name 是刪除整個字典
2. ```pop```
    - ```pop(Key)```是取得並移出
    - ```( )``` 需要需要有 ```Key```不然會報錯
3. ```clear```
    - ```dictionary_name.clear()``` 一次性將字典中所有項目清空刪除    


```python
#方法一
#超市為例，第一區賣蘋果，第二區賣三種肉
supermarket = dict(section_1 = '蘋果', section_2 = ['牛肉', '雞肉', '羊肉'], Number_of_visitors = 150)
del supermarket['Number_of_visitors']
print(supermarket)

del supermarket
print(supermarket)
#出錯是因為 supermarket已經被我們從記憶體刪除了，所以無法再將他print出來，從而顯示 NameError: name 'supermarket' is not defined
```

    {'section_1': '蘋果', 'section_2': ['牛肉', '雞肉', '羊肉']}
    


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    Cell In[57], line 8
          5 print(supermarket)
          7 del supermarket
    ----> 8 print(supermarket)
          9 #出錯是因為 supermarket已經被我們從記憶體刪除了，所以無法再將他print出來，從而顯示 NameError: name 'supermarket' is not defined
    

    NameError: name 'supermarket' is not defined



```python
#方法二
#超市為例，第一區賣蘋果，第二區賣三種肉
supermarket = dict(section_1 = '蘋果', section_2 = ['牛肉', '雞肉', '羊肉'], Number_of_visitors = 150)
List_of_Number_of_visitors = supermarket.pop('Number_of_visitors')
print(supermarket)
print(List_of_Number_of_visitors)
```

    {'section_1': '蘋果', 'section_2': ['牛肉', '雞肉', '羊肉']}
    150
    


```python
#方法三
#超市為例，第一區賣蘋果，第二區賣三種肉
supermarket = dict(section_1 = '蘋果', section_2 = ['牛肉', '雞肉', '羊肉'], Number_of_visitors = 150)
supermarket.clear()
print(supermarket)
```

    {}
    

### 合併字典
1. ```**``` dictionary_name，再透過 ```{ }```來組合，就可以將複數個字典合併在一起，變成一個<font color=#FF0000>新字典</font>， 當 ```Key``` 名稱重複，後面出現的將會覆蓋掉前面的
2. ```update()```，將b字典合併到a字典，當 ```Key``` 名稱重複，一樣後面(b)出現的將會覆蓋掉前面的(a)


```python
#方法一
#以兩間超市為例，將a與b合併為c
supermarket_a = dict(section_1 = '蘋果', section_2 = ['牛肉', '雞肉', '羊肉'], section_3 = ['樂事', '多力多滋', '奇多'], Number_of_visitors = 150)
supermarket_b = dict(section_1 = '鳳梨', section_2 = ['牛肉', '羊肉'], Number_of_visitors = 10)
supermarket_c = {**supermarket_a, **supermarket_b}
#supermarket_b這將會覆蓋掉與supermarket_a相同Key的Value
print(supermarket_c)
```

    {'section_1': '鳳梨', 'section_2': ['牛肉', '羊肉'], 'section_3': ['樂事', '多力多滋', '奇多'], 'Number_of_visitors': 10}
    


```python
#方法二
#以兩間超市為例
supermarket_a = dict(section_1 = '蘋果', section_2 = ['牛肉', '雞肉', '羊肉'], section_3 = ['樂事', '多力多滋', '奇多'], Number_of_visitors = 150)
supermarket_b = dict(section_1 = '鳳梨', section_2 = ['牛肉', '羊肉'], Number_of_visitors = 10)
supermarket_a.update(supermarket_b)
print(supermarket_a)
```

    {'section_1': '鳳梨', 'section_2': ['牛肉', '羊肉'], 'section_3': ['樂事', '多力多滋', '奇多'], 'Number_of_visitors': 10}
    

### 取得字典中的所有的 ```Key``` 或所有的 ```Value```
可以利用 ```.keys()``` 和 ```.values()``` 來達成


```python
#以超市為例
supermarket = dict(section_1 = '蘋果', section_2 = ['牛肉', '雞肉', '羊肉'], section_3 = ['樂事', '多力多滋', '奇多'])
#取得Key
#在這裡代表就是可以知道所有的Section名稱
supermarket_sections = supermarket.keys()
print(supermarket_sections, f', 型別: {type(supermarket_sections)}')
#可以轉為list或tuple來去做運用
print(list(supermarket_sections), '\n-------------------')

#取得Value
#在這裡代表就是可以知道所有的貨架上的所有品項
supermarket_items = supermarket.values()
print(supermarket_items, f', 型別: {type(supermarket_items)}')
#可以轉為list或tuple來去做運用
print(list(supermarket_items))
```

    dict_keys(['section_1', 'section_2', 'section_3']) , 型別: <class 'dict_keys'>
    ['section_1', 'section_2', 'section_3'] 
    -------------------
    dict_values(['蘋果', ['牛肉', '雞肉', '羊肉'], ['樂事', '多力多滋', '奇多']]) , 型別: <class 'dict_values'>
    ['蘋果', ['牛肉', '雞肉', '羊肉'], ['樂事', '多力多滋', '奇多']]
    

### in檢查字典中的 ```Key```
存在就回傳 ```True``` ，不存在回傳 ```False```


```python
#以超市為例
supermarket = dict(section_1 = '蘋果', section_2 = ['牛肉', '雞肉', '羊肉'], section_3 = ['樂事', '多力多滋', '奇多'])
print('Section_1 是否再 supermarket 中存在 :', 'section_1' in supermarket)
print('Section_4 是否再 supermarket 中存在 :', 'section_4' in supermarket)
```

    Section_1 是否再 supermarket 中存在 : True
    Section_4 是否再 supermarket 中存在 : False
    

### 複製字典
1. ```copy()``` ，當 a 被 b 複製，複製後當 a 的 ```Value```是 list 且發生異動， b 也會受到影響，適合**不會有異動的**資料使用
2. ```deepcopy()``` ， 當 a 被 b 複製，複製後當 a 發生異動， b **不會**受到影響
|    方法    |      影響不可變對象 (int, str)       |      影響可變對象 (list, dict)       |
|:--------:|:----------------:|:---------------:|
|   copy()   |       不受影響        |       會受影響        |
|    deepcopy()    | 	不受影響  | 不受影響  |



```python
#方法一
supermarket = dict(section_1 = '蘋果', section_2 = ['牛肉', '雞肉', '羊肉'], section_3 = ['樂事', '多力多滋', '奇多'])
#要開一間一模一樣的超市分店
supermarket_copy = supermarket.copy()
print(supermarket)
print(supermarket_copy, '\n-------------------')

#當改變的是list時，list是共用記憶體，所以當原本的改變了，copy的也會受到影響(大概理解就好，詳細原理不贅述)
supermarket['section_2'].append('豬肉')
print(supermarket)
print(supermarket_copy)
```

    {'section_1': '蘋果', 'section_2': ['牛肉', '雞肉', '羊肉'], 'section_3': ['樂事', '多力多滋', '奇多']}
    {'section_1': '蘋果', 'section_2': ['牛肉', '雞肉', '羊肉'], 'section_3': ['樂事', '多力多滋', '奇多']} 
    -------------------
    {'section_1': '蘋果', 'section_2': ['牛肉', '雞肉', '羊肉', '豬肉'], 'section_3': ['樂事', '多力多滋', '奇多']}
    {'section_1': '蘋果', 'section_2': ['牛肉', '雞肉', '羊肉', '豬肉'], 'section_3': ['樂事', '多力多滋', '奇多']}
    


```python
#方法二
supermarket = dict(section_1 = '蘋果', section_2 = ['牛肉', '雞肉', '羊肉'], section_3 = ['樂事', '多力多滋', '奇多'])

import copy
supermarket_copy = copy.deepcopy(supermarket)
print(supermarket)
print(supermarket_copy, '\n-------------------')

#當改變的是list時，這邊使用的deep copy，複製出來的supermarket完全獨立，所以當原本的改變了，deep copy的不會受到影響
supermarket['section_2'].append('豬肉')
print(supermarket)
print(supermarket_copy)
```

    {'section_1': '蘋果', 'section_2': ['牛肉', '雞肉', '羊肉'], 'section_3': ['樂事', '多力多滋', '奇多']}
    {'section_1': '蘋果', 'section_2': ['牛肉', '雞肉', '羊肉'], 'section_3': ['樂事', '多力多滋', '奇多']} 
    -------------------
    {'section_1': '蘋果', 'section_2': ['牛肉', '雞肉', '羊肉', '豬肉'], 'section_3': ['樂事', '多力多滋', '奇多']}
    {'section_1': '蘋果', 'section_2': ['牛肉', '雞肉', '羊肉'], 'section_3': ['樂事', '多力多滋', '奇多']}
    

### Set 集合
集合是由數字、字串和布林值組成，在一個集合之中可以存在不同類型的資料，而建立集合有兩種方式</br>
1. ```set()```
2. ```{value}``` 如果不放值會被宣告為字典


```python
#方法一
a = set() #宣告一個空集合
b = set([1,1,2,3])
c = set({'section_0': 'apple', 'section_1': [4, 5, 6], 'number': 10})
d = set('BAC')

print(type(a))
print(b)    #只會留下不重複的部分
print(c)    #只會保留key的部分
print(d)    #會將每個字元分開
```

    <class 'set'>
    {1, 2, 3}
    {'number', 'section_1', 'section_0'}
    {'B', 'C', 'A'}
    


```python
#方法二
a = {1, 2, 'B', True, False}    
print(a)    # True為1，這與集合中的數字1重複，所以True沒有被保留下來，False被留下是因為False等同於0

```

### 新增與刪除集合中的值
- 新增
    1. ```.add(Value)```
- 刪除
    1. ```remove(Value)```
    2. ```discard(Value)```    


```python
#新增
a = {1, 2, 'B', True, False}    
a.add(3)
print(a)
```

    {False, 1, 2, 3, 'B'}
    


```python
#刪除
#方法一
a = {1, 2, 'B', True, False}    
a.remove(1)
print(a)
```

    {'B', 2, False}
    


```python
#刪除
#方法二
a = {1, 2, 'B', True, False}    
a.discard(1)
a.discard(3) #3不存在在集合之中，如果使用remove會出錯，但使用discard就不會報錯
print(a)
```

    {'B', 2, False}
    

### 取得長度與檢察是否存在
- ```len()```取得長度
- ```in```判斷是否再集合之中


```python
a = {'a','b','c','d',1,2,3}
#檢查長度
print('set a 的長度為 :', len(a), '\n-----------')

#檢查是否存在
print('1 是否存在於 set a 中 :', 1 in a)
print('777 是否存在於 set a 中 :', 777 in a, '\n-----------')
#檢查是否不存在
print('1 是否不存在於 set a 中 :', 1 not in a)
print('777 是否不存在於 set a 中 :', 777 not in a)
```

    set a 的長度為 : 7 
    -----------
    1 是否存在於 set a 中 : True
    777 是否存在於 set a 中 : False 
    -----------
    1 是否不存在於 set a 中 : False
    777 是否存在於 set a 中 : True
    

### 交集、聯集、差集、對稱差集
|    集合    |      方法      |      運算子       |     情況     |
|:--------:|:----------------:|:---------------:|:----------:|
|  交集  |       a.intersection(b)       |       a&b       | A與B集合的共有項目 |
|    聯集    | 	a.union(b)  | a｜b  |A與B集合的所有項目 |
|    差集    | 	a.difference(b)  | a-b  |A 集合扣掉 A B 集合的共有項目 |
|    對稱差集    | 	a.symmetric_difference(b)  | a^b  |A與B集合的獨有項目 |



```python
a = {1,2,3,4,5}
b = {3,4,5,6,7}

# a交集b
print(a.intersection(b))   
print(a&b, '\n-----------')                 

# a聯集b
print(a.union(b))          
print(a|b, '\n-----------')                 

# a差集b
print(a.difference(b))     
print(a-b, '\n-----------') 

# a對稱差集b
print(a.symmetric_difference(b))  
print(a^b)   
```

    {3, 4, 5}
    {3, 4, 5} 
    -----------
    {1, 2, 3, 4, 5, 6, 7}
    {1, 2, 3, 4, 5, 6, 7} 
    -----------
    {1, 2}
    {1, 2} 
    -----------
    {1, 2, 6, 7}
    {1, 2, 6, 7}
    

### 子集合與超集合
- 子集合 (sebset) ： 若 A 集合的所有項目是 B 集合的部分集合, 則稱 A 為 B 的子集合
- 超集合 (superset) ： 若 A 集合的所有項目是 B 集合的部分集合, 則稱 B 為 A 的超集合
|    集合      |     說明     |
|:--------:|:----------:|
|    超集合      |     A 完全包含 B，A 和 B 所包含的元素可能完全相同     |
|    真超集合      |     A 完全包含 B，且具有 B 沒有的的元素     |
|    子集合      |     B 完全被 A 包含，A 和 B 所包含的元素可能完全相同     |
|    真子集合      |     B 完全被 A 包含，且 A 具有 B 沒有的的元素     |

可以使用```>, < ,=```來判斷，也可以使用```b.issubset(a)```檢測 b 是否為 a 的子集合，還有```a.issuperset(b)```檢測 a 是否為 b 的超集合


```python
a = {1,2,3,4,5,6,7}
b = {3,4,5,6,7}
c = {1,2,3,4,5,6,7}
d = {6,7,8,9}

print(a<=a)   # True 自己是自己的子集合
print(b<=a)   # True b 是 a 的子集合
print(b<a)    # True b 也是 a 的真子集合 ( 因爲沒有等於，完全包含 )
print(c<=a)   # True c 是 a 的子集合
print(a<=c)   # True a 也是 c 的子集合
print(d<a)    # False d 和 a 沒有子集合或超集合關係
```

    True
    True
    True
    True
    True
    False
    


```python
a = {1,2,3,4,5,6,7}
b = {3,4,5,6,7}
c = {1,2,3,4,5,6,7}
d = {6,7,8,9}

print(b.issubset(a))     # True b 是 a 的子集合
print(a.issuperset(b))   # True a 是 b 的超集合
print(c.issubset(a))     # True c 是 a 的子集合
print(d.issubset(a))     # Fasle d 不是 a 的子集合
```
