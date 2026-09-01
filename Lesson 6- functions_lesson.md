# Function (ฟังก์ชัน) ใน Python

Function คือชุดคำสั่งที่เราสร้างขึ้นเพื่อทำงานบางอย่าง และสามารถเรียกใช้ซ้ำได้โดยไม่ต้องเขียนโค้ดซ้ำ ช่วยให้โปรแกรมเป็นระเบียบ อ่านง่าย และแก้ไขได้สะดวก บทเรียนนี้รวบรวม Syntax ของ Function ตั้งแต่ระดับพื้นฐานไปจนถึงระดับที่ใช้ในงานวิเคราะห์ข้อมูลจริง พร้อมแบบฝึกหัดท้ายบท

---

## 1. โครงสร้างพื้นฐานของ Function

```python
def ชื่อฟังก์ชัน():
    คำสั่ง
```

เรียกใช้งานด้วย:
```python
ชื่อฟังก์ชัน()
```

**ตัวอย่าง**
```python
def hello():
    print("Hello Python")

hello()
```
ผลลัพธ์: `Hello Python`

---

## 2. Function ที่มี Parameter

Parameter คือค่าที่ส่งเข้าไปให้ Function ใช้งานภายใน

```python
def function_name(parameter):
    statement
```

```python
def greeting(name):
    print("Hello", name)

greeting("Somchai")
```
ผลลัพธ์: `Hello Somchai`

### 2.1 Function ที่มีหลาย Parameter

```python
def add(a, b):
    print(a + b)

add(10, 20)
```
ผลลัพธ์: `30`

---

## 3. Function ที่มี return

`return` เป็นรูปแบบที่สำคัญมาก เพราะสามารถนำผลลัพธ์ไปใช้ต่อในส่วนอื่นของโปรแกรมได้ ต่างจาก `print()` ที่แค่แสดงผลบนหน้าจอเท่านั้น

```python
def add(a, b):
    return a + b

result = add(10, 20)
print(result)
```
ผลลัพธ์: `30`

| รูปแบบ | พฤติกรรม |
|---|---|
| `print(a + b)` | แสดงผลอย่างเดียว นำค่าไปใช้ต่อไม่ได้ |
| `return a + b` | ส่งค่ากลับไปให้โปรแกรม นำไปเก็บในตัวแปรหรือใช้ต่อได้ |

> ในงานจริงมักเขียนแบบ `result = add(10, 20)` เพื่อเก็บค่าที่ return ไว้ใช้ต่อ

### 3.1 รูปแบบผสมของ Parameter และ Return

| รูปแบบ | ตัวอย่าง |
|---|---|
| ไม่มี Parameter, ไม่มี Return | `def hello(): print("Hi")` |
| มี Parameter, ไม่มี Return | `def show_score(score): print(score)` |
| ไม่มี Parameter, มี Return | `def get_score(): return 85` |
| มี Parameter และ Return | `def calc(a, b): return a + b` |

**ตัวอย่างที่ใช้บ่อยที่สุด — มีทั้ง Parameter และ Return**
```python
def calculate_score(score1, score2):
    total = score1 + score2
    return total

result = calculate_score(80, 90)
print(result)
```
ผลลัพธ์: `170`

---

## 4. Default Parameter

กำหนดค่าเริ่มต้นให้กับ Parameter ในกรณีที่ผู้เรียกไม่ได้ส่งค่ามา

```python
def function(parameter=default_value):
    statement
```

```python
def greeting(name="Guest"):
    print("Hello", name)

greeting()
greeting("Somchai")
```
ผลลัพธ์:
```
Hello Guest
Hello Somchai
```

---

## 5. การส่งค่าเข้า Function

### 5.1 Positional Arguments — ส่งค่าตามลำดับ

```python
def student(name, age):
    print(name)
    print(age)

student("Somchai", 20)   # "Somchai" -> name, 20 -> age
```

### 5.2 Keyword Arguments — ระบุชื่อ Parameter ตอนเรียก

```python
def student(name, age):
    print(name)
    print(age)

student(name="Somchai", age=20)
```
> ข้อดีคือไม่ต้องจำลำดับของ Parameter

### 5.3 *args — รับ Parameter ไม่จำกัดจำนวน

ใช้เมื่อไม่รู้ว่าจะส่ง Parameter เข้ามากี่ตัว

```python
def total(*numbers):
    result = 0
    for number in numbers:
        result += number
    return result

print(total(10, 20))
print(total(10, 20, 30))
print(total(10, 20, 30, 40))
```

### 5.4 **kwargs — รับ Parameter แบบ Key-Value

```python
def student(**data):
    print(data)

student(name="Somchai", age=20, major="Computer")
```
ผลลัพธ์: `{'name': 'Somchai', 'age': 20, 'major': 'Computer'}`

### 5.5 ใช้ *args และ **kwargs ร่วมกัน

```python
def test(*args, **kwargs):
    print(args)
    print(kwargs)

test(10, 20, 30, name="Somchai", age=20)
```

---

## 6. Lambda Function

Function ขนาดสั้นที่เขียนได้ในบรรทัดเดียว เหมาะกับงานง่าย ๆ ที่ใช้ครั้งเดียว

**Syntax**
```python
lambda parameter: expression
```

```python
square = lambda x: x * x
print(square(5))
```
ผลลัพธ์: `25`

เทียบกับการเขียนแบบปกติ:
```python
def square(x):
    return x * x
# เขียนสั้นได้เป็น
square = lambda x: x * x
```

**Lambda หลาย Parameter**
```python
add = lambda a, b: a + b
print(add(10, 20))
```
ผลลัพธ์: `30`

---

## 7. Recursive Function (Function เรียกตัวเอง)

```python
def function():
    if condition:
        return result
    return function()
```

**ตัวอย่าง Factorial**
```python
def factorial(n):
    if n == 1:
        return 1
    return n * factorial(n - 1)

print(factorial(5))
```
ผลลัพธ์: `120`

> ใช้กับปัญหาประเภทโครงสร้างซ้ำ เช่น Tree, Graph และปัญหาทางคณิตศาสตร์บางประเภท

---

## 8. Higher-Order Function (Function รับ Function เป็น Parameter)

```python
def calculate(a, b, operation):
    return operation(a, b)

def add(a, b):
    return a + b

result = calculate(10, 20, add)
print(result)
```
ผลลัพธ์: `30`

### 8.1 map() — ประมวลผลข้อมูลทีละตัว

```python
numbers = [1, 2, 3, 4, 5]
result = map(lambda x: x * 2, numbers)
print(list(result))
```
ผลลัพธ์: `[2, 4, 6, 8, 10]`

### 8.2 filter() — กรองข้อมูล

```python
numbers = [1, 2, 3, 4, 5, 6]
result = filter(lambda x: x % 2 == 0, numbers)
print(list(result))
```
ผลลัพธ์: `[2, 4, 6]`

### 8.3 reduce() — รวมข้อมูลทีละตัว (ต้อง import ก่อน)

```python
from functools import reduce

numbers = [1, 2, 3, 4, 5]
result = reduce(lambda a, b: a + b, numbers)
print(result)
```
ผลลัพธ์: `15`

---

## 9. Generator Function

ใช้ `yield` แทน `return` เหมาะกับข้อมูลจำนวนมาก เพราะไม่จำเป็นต้องเก็บข้อมูลทั้งหมดไว้ใน Memory พร้อมกัน

```python
def numbers():
    yield 1
    yield 2
    yield 3

for number in numbers():
    print(number)
```
ผลลัพธ์:
```
1
2
3
```

---

## 10. Async Function

Python รองรับ Asynchronous Function สำหรับงานที่ต้องรอ (เช่น Web API, Network, Database)

**Syntax**
```python
async def function_name():
    statement
```

```python
import asyncio

async def hello():
    print("Hello")

asyncio.run(hello())
```

---

## 11. Function ใน Class — Method

ถ้า Function อยู่ภายใน Class จะเรียกว่า **Method**

```python
class Student:
    def hello(self):
        print("Hello Student")

student = Student()
student.hello()
```

### 11.1 `__init__()` — Method พิเศษที่ทำงานเมื่อสร้าง Object

```python
class Student:
    def __init__(self, name):
        self.name = name

    def show(self):
        print(self.name)

student = Student("Somchai")
student.show()
```

---

## 12. Built-in Functions ที่ควรรู้

Python มี Function ที่เตรียมไว้ให้แล้ว ไม่ต้องสร้างเอง

| Function | ใช้ทำอะไร |
|---|---|
| `print()` | แสดงผล |
| `input()` | รับข้อมูล |
| `len()` | หาจำนวน |
| `type()` | ตรวจชนิดข้อมูล |
| `int() / float() / str() / bool()` | แปลงชนิดข้อมูล |
| `list() / tuple() / dict() / set()` | สร้าง/แปลงชนิดข้อมูลกลุ่ม |
| `range()` | สร้างช่วงตัวเลข |
| `sum() / max() / min()` | หาผลรวม / ค่าสูงสุด / ค่าต่ำสุด |
| `abs() / round()` | ค่าสัมบูรณ์ / ปัดเศษ |
| `sorted()` | เรียงข้อมูล |
| `enumerate()` | สร้างลำดับพร้อมข้อมูล |
| `zip()` | รวมข้อมูลหลายชุด |
| `map() / filter()` | ประมวลผล / กรองข้อมูล |
| `any() / all()` | ตรวจว่ามี/ทั้งหมดเป็น True หรือไม่ |

**ตัวอย่างที่ใช้บ่อย**
```python
scores = [80, 90, 75, 88]

print(sum(scores))      # 333
print(max(scores))      # 90
print(min(scores))      # 75
print(sorted(scores))   # [75, 80, 88, 90]
```

```python
names = ["A", "B", "C"]
scores = [80, 90, 75]

for name, score in zip(names, scores):
    print(name, score)
```
ผลลัพธ์:
```
A 80
B 90
C 75
```

---

## 13. Scope ของ Function (Local / Global Variable)

### 13.1 Local Variable — ตัวแปรที่สร้างภายใน Function

```python
def test():
    x = 10
    print(x)

test()
```
> `x` ใช้งานได้เฉพาะภายใน Function เท่านั้น

### 13.2 Global Variable — ตัวแปรที่สร้างภายนอก Function

```python
x = 10

def test():
    print(x)

test()
```
> Function สามารถ**อ่าน**ค่า `x` จากภายนอกได้

### 13.3 การใช้ global เพื่อแก้ไข Global Variable

```python
x = 10

def change():
    global x
    x = 20

change()
print(x)
```
ผลลัพธ์: `20`

> ⚠️ ควรใช้ `global` อย่างระมัดระวัง เพราะทำให้โปรแกรมขนาดใหญ่ดูแลรักษายากขึ้น

---

## 14. Docstring และ Type Hint

### 14.1 Docstring — คำอธิบาย Function

```python
def calculate_average(scores):
    """
    คำนวณค่าเฉลี่ยของคะแนน
    """
    return sum(scores) / len(scores)
```

### 14.2 Type Hint — ระบุชนิดข้อมูลที่คาดหวัง

```python
def add(a: int, b: int) -> int:
    return a + b
```
ความหมาย: `a` และ `b` เป็น `int`, ค่าที่ return เป็น `int`

```python
def average(scores: list) -> float:
    return sum(scores) / len(scores)
```

---

## 15. Function ที่มีหลาย Return

```python
def calculate(scores):
    total = sum(scores)
    average = total / len(scores)
    maximum = max(scores)
    return total, average, maximum

scores = [80, 90, 70]
total, average, maximum = calculate(scores)

print(total)
print(average)
print(maximum)
```

---

## 16. Function จาก Library (NumPy / Pandas)

เมื่อเริ่มทำ Data Science / Data Analysis จะใช้ Function จาก Library เป็นจำนวนมาก

**NumPy**
```python
import numpy as np

data = [10, 20, 30, 40, 50]

print(np.mean(data))
print(np.max(data))
print(np.min(data))
```

**Pandas**
```python
import pandas as pd

df = pd.read_excel("student.xlsx")

print(df["score"].mean())   # คะแนนเฉลี่ย
print(df["score"].max())    # คะแนนสูงสุด
print(df["score"].min())    # คะแนนต่ำสุด
```

Method ที่ใช้บ่อย: `df.head()`, `df.info()`, `df.describe()`, `df.sum()`, `df.count()`

---

## 17. Function กับ Method ต่างกันอย่างไร?

| ประเภท | ตัวอย่าง | ลักษณะ |
|---|---|---|
| Function | `len(data)` | เรียกใช้โดยตรง ไม่ผูกกับ Object |
| Method | `data.append(10)` / `df.head()` | เป็น Function ที่อยู่ผูกกับ Object |

---

## 18. สรุปประเภท Function ที่ควรรู้

| ประเภท | ตัวอย่าง |
|---|---|
| 1. User-defined Function | `def add():` |
| 2. Function มี Parameter | `def add(a, b):` |
| 3. Function มี Return | `return result` |
| 4. Default Parameter | `def test(x=10):` |
| 5. *args | รับ Parameter หลายตัว |
| 6. **kwargs | รับ Key-Value หลายตัว |
| 7. Lambda | `lambda x: x*2` |
| 8. Recursive Function | Function เรียกตัวเอง |
| 9. Higher-Order Function | รับ Function เป็น Parameter |
| 10. Generator | `yield` |
| 11. Async Function | `async def` |
| 12. Method | Function ใน Class |
| 13. Built-in Function | `print()`, `len()`, `sum()` |
| 14. Library Function | `numpy.mean()` |
| 15. Custom Module Function | Function จากไฟล์ของเราเอง |

### ระดับความยากที่แนะนำให้จำตามลำดับ

```python
# ระดับ 1 — พื้นฐาน
def hello():
    print("Hello")

# ระดับ 2 — Parameter
def hello(name):
    print("Hello", name)

# ระดับ 3 — Return
def add(a, b):
    return a + b

# ระดับ 4 — Default
def hello(name="Guest"):
    print(name)

# ระดับ 5 — หลายค่า
def calculate(a, b):
    return a+b, a-b

# ระดับ 6 — *args
def total(*numbers):
    return sum(numbers)

# ระดับ 7 — Lambda
square = lambda x: x*x

# ระดับ 8 — Function + Loop
def calculate_total(scores):
    total = 0
    for score in scores:
        total += score
    return total
```

---

## แบบฝึกหัดท้ายบท

จงเขียนโปรแกรม Python โดยสร้าง Function ตามโจทย์ต่อไปนี้ พร้อมทดลองเรียกใช้งานจริง

**1)** เขียน Function ชื่อ `bmi_calculator` ที่รับ Parameter น้ำหนัก (kg) และส่วนสูง (m) แล้ว `return` ค่าดัชนีมวลกาย (BMI = น้ำหนัก / ส่วนสูง²) จากนั้นเรียกใช้และพิมพ์ผลลัพธ์
> คำใบ้: `def bmi_calculator(weight, height): return weight / (height ** 2)`

**2)** เขียน Function ชื่อ `average_score` ที่รับ Parameter เป็น list ของคะแนน และมีค่า Default เป็น list ว่าง `[]` หากไม่ส่งค่าเข้ามาให้พิมพ์ว่า "ไม่มีข้อมูลคะแนน" มิฉะนั้นให้ `return` ค่าเฉลี่ยของคะแนน
> คำใบ้: ใช้ `def average_score(scores=[]):` แล้วตรวจสอบด้วย `if len(scores) == 0:`

**3)** เขียน Function ชื่อ `sum_all` โดยใช้ `*args` เพื่อรับตัวเลขจำนวนเท่าใดก็ได้ แล้ว `return` ผลรวมทั้งหมด จากนั้นทดลองเรียกใช้กับจำนวนตัวเลข 3 ครั้งที่มีจำนวน argument ไม่เท่ากัน (เช่น 2 ตัว, 4 ตัว, 6 ตัว)
> คำใบ้: `def sum_all(*numbers): return sum(numbers)`

**4)** เขียน Function แบบ Recursive ชื่อ `count_down` ที่รับตัวเลข n แล้วพิมพ์ตัวเลขไล่ลงจาก n จนถึง 1 (เช่น n=5 จะพิมพ์ 5 4 3 2 1) โดยให้ Function เรียกตัวเองซ้ำจนกว่า n จะเท่ากับ 0
> คำใบ้: กำหนดเงื่อนไขหยุด (base case) เมื่อ `n == 0` แล้ว `return`

**5)** เขียน Function ชื่อ `filter_passed` ที่รับ list ของคะแนนนักศึกษา และใช้ `filter()` ร่วมกับ `lambda` เพื่อคัดกรองเฉพาะคะแนนที่ ≥ 50 แล้ว `return` ผลลัพธ์เป็น list จากนั้นพิมพ์จำนวนคนที่ผ่านด้วย `len()`
> คำใบ้: `def filter_passed(scores): return list(filter(lambda x: x >= 50, scores))`
