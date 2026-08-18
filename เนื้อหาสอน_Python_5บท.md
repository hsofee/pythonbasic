# เนื้อหาสอนวิชา Python สำหรับวัยทำงาน (ระดับพื้นฐาน)
### หลักสูตร 5 บท เน้นเรียนเพื่อใช้งานจริง

> **แนวทางการสอน:** เนื้อหาแต่ละบทออกแบบให้ใช้เวลาสอนประมาณ 2-3 ชั่วโมง มีตัวอย่างโค้ดที่ใช้ได้จริงในชีวิตประจำวัน/งาน และมีแบบฝึกหัดท้ายบทเพื่อให้ผู้เรียนลงมือปฏิบัติ

---

## สารบัญ
1. บทที่ 1: เริ่มต้นกับ Python และตัวแปร
2. บทที่ 2: เงื่อนไขและการวนซ้ำ
3. บทที่ 3: ฟังก์ชัน (Functions)
4. บทที่ 4: โครงสร้างข้อมูล (List, Tuple, Dictionary, Set)
5. บทที่ 5: การจัดการไฟล์และข้อผิดพลาดเบื้องต้น

---

# บทที่ 1: เริ่มต้นกับ Python และตัวแปร

## วัตถุประสงค์การเรียนรู้
เมื่อจบบทเรียนนี้ ผู้เรียนจะสามารถ:
- เข้าใจว่า Python คืออะไร และเหมาะกับงานประเภทไหน
- เขียนโปรแกรม Python พื้นฐานและรันได้
- ใช้ตัวแปรและชนิดข้อมูลพื้นฐานได้อย่างถูกต้อง
- รับข้อมูลจากผู้ใช้และแสดงผลลัพธ์ได้

## 1.1 Python คืออะไร
Python เป็นภาษาโปรแกรมที่อ่านง่าย เขียนง่าย นิยมใช้ในงานหลากหลาย เช่น วิเคราะห์ข้อมูล, ทำงานอัตโนมัติ (automation), เว็บแอปพลิเคชัน, และ AI/Machine Learning เหมาะมากสำหรับผู้เริ่มต้น เพราะไวยากรณ์ใกล้เคียงภาษาอังกฤษทั่วไป

**ตัวอย่างการใช้งานจริงในที่ทำงาน:**
- เขียนสคริปต์ดึงข้อมูลจากไฟล์ Excel มาสรุปอัตโนมัติ
- ทำระบบคำนวณง่ายๆ เช่น คำนวณเงินเดือน, ภาษี
- เขียนบอทส่งอีเมลอัตโนมัติ

## 1.2 การรันโปรแกรม Python ครั้งแรก
```python
print("สวัสดี Python!")
```
คำสั่ง `print()` ใช้แสดงผลลัพธ์ออกทางหน้าจอ

## 1.3 คอมเมนต์ (Comment)
```python
# นี่คือคอมเมนต์ 1 บรรทัด ไม่ถูกรันเป็นโค้ด
print("บรรทัดนี้ทำงาน")  # คอมเมนต์ต่อท้ายบรรทัดก็ได้
```

## 1.4 ตัวแปร (Variables)
ตัวแปรใช้สำหรับเก็บค่าข้อมูลไว้ใช้งานภายหลัง

```python
name = "สมชาย"
age = 35
salary = 25000.50
is_employee = True

print(name, age, salary, is_employee)
```

**กฎการตั้งชื่อตัวแปร**
- ห้ามขึ้นต้นด้วยตัวเลข
- ห้ามมีช่องว่าง (ใช้ `_` แทน)
- ตัวพิมพ์เล็ก-ใหญ่มีความหมายต่างกัน (`Name` ≠ `name`)
- ควรตั้งชื่อให้สื่อความหมาย เช่น `total_price` ดีกว่า `x`

## 1.5 ชนิดข้อมูลพื้นฐาน (Data Types)

| ชนิดข้อมูล | ความหมาย | ตัวอย่าง |
|---|---|---|
| `int` | จำนวนเต็ม | `10`, `-5` |
| `float` | จำนวนทศนิยม | `3.14`, `25000.5` |
| `str` | ข้อความ | `"สวัสดี"` |
| `bool` | ค่าความจริง | `True`, `False` |

ตรวจสอบชนิดข้อมูลด้วย `type()`
```python
print(type(age))      # <class 'int'>
print(type(salary))    # <class 'float'>
```

## 1.6 การแปลงชนิดข้อมูล (Type Casting)
```python
age_text = "35"
age_number = int(age_text)   # แปลงข้อความเป็นจำนวนเต็ม
print(age_number + 1)         # 36
```

## 1.7 การรับข้อมูลจากผู้ใช้ (input)
```python
name = input("กรุณากรอกชื่อของคุณ: ")
print("สวัสดีคุณ", name)
```
> **ข้อควรระวัง:** `input()` จะได้ค่าเป็น `str` เสมอ หากต้องการนำไปคำนวณ ต้องแปลงชนิดข้อมูลก่อน เช่น `int(input(...))`

## 1.8 ตัวอย่างโปรแกรมใช้งานจริง: คำนวณดัชนีมวลกาย (BMI)
```python
weight = float(input("น้ำหนัก (กก.): "))
height = float(input("ส่วนสูง (เมตร): "))

bmi = weight / (height ** 2)
print("ค่า BMI ของคุณคือ:", round(bmi, 2))
```

## แบบฝึกหัดท้ายบทที่ 1
1. เขียนโปรแกรมรับชื่อและอายุจากผู้ใช้ แล้วแสดงข้อความ "คุณ [ชื่อ] อายุ [อายุ] ปี"
2. เขียนโปรแกรมคำนวณเงินเดือนสุทธิ โดยหักประกันสังคม 5% จากเงินเดือนที่กรอก
3. เขียนโปรแกรมแปลงอุณหภูมิจากองศาเซลเซียสเป็นฟาเรนไฮต์ (สูตร: F = C * 9/5 + 32)

---

# บทที่ 2: เงื่อนไขและการวนซ้ำ

## วัตถุประสงค์การเรียนรู้
เมื่อจบบทเรียนนี้ ผู้เรียนจะสามารถ:
- ใช้คำสั่งเงื่อนไข `if-elif-else` ตัดสินใจในโปรแกรมได้
- ใช้ตัวดำเนินการเปรียบเทียบและตรรกะ
- ใช้ลูป `for` และ `while` ทำงานซ้ำๆ ได้
- ควบคุมการวนซ้ำด้วย `break` และ `continue`

## 2.1 ตัวดำเนินการเปรียบเทียบ (Comparison Operators)

| ตัวดำเนินการ | ความหมาย |
|---|---|
| `==` | เท่ากับ |
| `!=` | ไม่เท่ากับ |
| `>` | มากกว่า |
| `<` | น้อยกว่า |
| `>=` | มากกว่าหรือเท่ากับ |
| `<=` | น้อยกว่าหรือเท่ากับ |

## 2.2 ตัวดำเนินการตรรกะ (Logical Operators)
```python
age = 25
has_id_card = True

if age >= 18 and has_id_card:
    print("สามารถทำธุรกรรมได้")
```
- `and` : จริงทั้งคู่ถึงจะจริง
- `or` : จริงอย่างใดอย่างหนึ่งก็จริง
- `not` : กลับค่าความจริง

## 2.3 คำสั่งเงื่อนไข if-elif-else
```python
score = 75

if score >= 80:
    grade = "A"
elif score >= 70:
    grade = "B"
elif score >= 60:
    grade = "C"
else:
    grade = "F"

print("เกรดที่ได้:", grade)
```

## 2.4 ตัวอย่างใช้งานจริง: ระบบคำนวณส่วนลดสมาชิก
```python
purchase_amount = float(input("ยอดซื้อสินค้า: "))
is_member = input("เป็นสมาชิกหรือไม่ (y/n): ")

if is_member == "y" and purchase_amount >= 1000:
    discount = purchase_amount * 0.15
elif is_member == "y":
    discount = purchase_amount * 0.05
else:
    discount = 0

total = purchase_amount - discount
print("ส่วนลดที่ได้รับ:", discount)
print("ยอดที่ต้องชำระ:", total)
```

## 2.5 ลูป for
ใช้เมื่อรู้จำนวนรอบที่แน่นอน หรือวนตามข้อมูลในกลุ่มข้อมูล
```python
for i in range(1, 6):
    print("รอบที่", i)
```
- `range(1, 6)` จะได้ค่า 1, 2, 3, 4, 5 (ไม่รวม 6)

```python
fruits = ["แอปเปิ้ล", "กล้วย", "ส้ม"]
for fruit in fruits:
    print("ผลไม้:", fruit)
```

## 2.6 ลูป while
ใช้เมื่อไม่รู้จำนวนรอบแน่ชัด แต่มีเงื่อนไขให้วนซ้ำจนกว่าจะเป็นเท็จ
```python
balance = 1000
month = 1

while balance > 0:
    balance -= 200
    print("เดือนที่", month, "เหลือเงิน:", balance)
    month += 1
```

## 2.7 break และ continue
```python
for number in range(1, 11):
    if number == 5:
        break        # หยุดลูปทันที
    print(number)
```
```python
for number in range(1, 11):
    if number % 2 == 0:
        continue     # ข้ามรอบนี้ไปรอบถัดไป
    print(number)     # แสดงเฉพาะเลขคี่
```

## 2.8 ตัวอย่างใช้งานจริง: ระบบเข้าสู่ระบบ (จำกัดจำนวนครั้ง)
```python
correct_password = "1234"
attempts = 0
max_attempts = 3

while attempts < max_attempts:
    password = input("กรอกรหัสผ่าน: ")
    if password == correct_password:
        print("เข้าสู่ระบบสำเร็จ")
        break
    else:
        attempts += 1
        print("รหัสผ่านผิด เหลืออีก", max_attempts - attempts, "ครั้ง")
else:
    print("กรอกผิดครบจำนวนครั้งที่กำหนด บัญชีถูกล็อก")
```

## แบบฝึกหัดท้ายบทที่ 2
1. เขียนโปรแกรมตรวจสอบว่าปีที่กรอกเป็นปีอธิกสุรทิน (leap year) หรือไม่
2. เขียนโปรแกรมพิมพ์ตารางสูตรคูณแม่ 2-12 โดยใช้ลูป
3. เขียนโปรแกรมคำนวณผลรวมของตัวเลข 1 ถึง N (รับค่า N จากผู้ใช้)
4. เขียนโปรแกรมเดาตัวเลข (1-100) โดยให้ผู้ใช้ทายจนกว่าจะถูก พร้อมบอกใบ้ว่า "มากไป" หรือ "น้อยไป"

---

# บทที่ 3: ฟังก์ชัน (Functions)

## วัตถุประสงค์การเรียนรู้
เมื่อจบบทเรียนนี้ ผู้เรียนจะสามารถ:
- สร้างและเรียกใช้ฟังก์ชันของตนเองได้
- ส่งค่าพารามิเตอร์และรับค่าคืนกลับ (return) ได้
- เข้าใจแนวคิดขอบเขตตัวแปร (scope) เบื้องต้น
- เห็นประโยชน์ของการแบ่งโค้ดเป็นฟังก์ชันเพื่อนำกลับมาใช้ซ้ำ

## 3.1 ทำไมต้องใช้ฟังก์ชัน
ฟังก์ชันช่วยให้แบ่งโค้ดเป็นส่วนย่อยๆ ที่นำกลับมาใช้ซ้ำได้ ลดความซ้ำซ้อน และทำให้โค้ดอ่านง่ายขึ้น

## 3.2 การสร้างฟังก์ชันพื้นฐาน
```python
def greet():
    print("สวัสดีตอนเช้า")

greet()  # เรียกใช้ฟังก์ชัน
```

## 3.3 ฟังก์ชันที่รับพารามิเตอร์
```python
def greet(name):
    print("สวัสดีคุณ", name)

greet("สมหญิง")
greet("สมชาย")
```

## 3.4 ฟังก์ชันที่คืนค่า (return)
```python
def calculate_discount(price, percent):
    discount = price * percent / 100
    return discount

result = calculate_discount(1000, 10)
print("ส่วนลดที่ได้:", result)
```

## 3.5 ค่าเริ่มต้นของพารามิเตอร์ (Default Parameters)
```python
def calculate_vat(price, vat_rate=7):
    return price * vat_rate / 100

print(calculate_vat(1000))       # ใช้ vat_rate เริ่มต้น 7%
print(calculate_vat(1000, 10))   # กำหนดเอง 10%
```

## 3.6 ขอบเขตตัวแปร (Scope) เบื้องต้น
```python
total = 100  # ตัวแปร global

def add_bonus():
    total = total + 50  # ตัวแปร local ชื่อซ้ำกับ global -> จะเกิด error
    return total

def add_bonus_correct(amount):
    return amount + 50

print(add_bonus_correct(total))
```
> หลักการง่ายๆ: ตัวแปรที่สร้างภายในฟังก์ชันจะมองไม่เห็นจากภายนอก และควรส่งค่าผ่านพารามิเตอร์แทนการอ้างตัวแปรนอกฟังก์ชันโดยตรง

## 3.7 ตัวอย่างใช้งานจริง: ระบบคำนวณค่าจ้างพนักงาน
```python
def calculate_wage(hours_worked, hourly_rate, overtime_hours=0):
    normal_pay = hours_worked * hourly_rate
    overtime_pay = overtime_hours * hourly_rate * 1.5
    return normal_pay + overtime_pay

wage = calculate_wage(hours_worked=40, hourly_rate=50, overtime_hours=5)
print("ค่าจ้างรวม:", wage, "บาท")
```

## 3.8 ฟังก์ชันซ้อนฟังก์ชัน (การเรียกใช้ฟังก์ชันอื่นในฟังก์ชัน)
```python
def calculate_subtotal(price, quantity):
    return price * quantity

def calculate_total_with_vat(price, quantity, vat_rate=7):
    subtotal = calculate_subtotal(price, quantity)
    vat = subtotal * vat_rate / 100
    return subtotal + vat

total = calculate_total_with_vat(150, 3)
print("ยอดรวมพร้อมภาษี:", total)
```

## แบบฝึกหัดท้ายบทที่ 3
1. เขียนฟังก์ชัน `is_even(number)` ที่คืนค่า True/False ว่าตัวเลขเป็นเลขคู่หรือไม่
2. เขียนฟังก์ชัน `calculate_bmi(weight, height)` ที่คืนค่าดัชนีมวลกาย
3. เขียนฟังก์ชัน `convert_currency(amount, rate)` แปลงเงินบาทเป็นสกุลเงินต่างประเทศ โดยกำหนด `rate` มีค่าเริ่มต้นเป็นอัตราแลกเปลี่ยน USD ปัจจุบัน (สมมติ 36.5)
4. เขียนฟังก์ชันคำนวณค่าคอมมิชชั่นพนักงานขาย โดยยอดขายต่ำกว่า 10,000 ได้ 3% ยอดขาย 10,000 ขึ้นไปได้ 5%

---

# บทที่ 4: โครงสร้างข้อมูล (List, Tuple, Dictionary, Set)

## วัตถุประสงค์การเรียนรู้
เมื่อจบบทเรียนนี้ ผู้เรียนจะสามารถ:
- ใช้งาน List เพื่อเก็บข้อมูลหลายค่าและจัดการข้อมูลได้
- เข้าใจความแตกต่างของ List, Tuple, Dictionary, Set และเลือกใช้ได้เหมาะสม
- ใช้คำสั่งพื้นฐานในการเพิ่ม ลบ แก้ไข ค้นหาข้อมูล

## 4.1 List (ลิสต์)
List คือกลุ่มข้อมูลที่เรียงลำดับ แก้ไขได้ (mutable)
```python
fruits = ["แอปเปิ้ล", "กล้วย", "ส้ม"]

print(fruits[0])         # แอปเปิ้ล (index เริ่มที่ 0)
print(fruits[-1])        # ส้ม (index ท้ายสุด)

fruits.append("มะม่วง")   # เพิ่มท้ายลิสต์
fruits.remove("กล้วย")    # ลบข้อมูล
fruits[0] = "สับปะรด"     # แก้ไขค่า

print(fruits)
print(len(fruits))       # จำนวนสมาชิกในลิสต์
```

### การวนลูปใน List
```python
prices = [150, 200, 350, 500]
total = 0
for price in prices:
    total += price
print("ราคารวม:", total)
```

### การตัด List (Slicing)
```python
numbers = [10, 20, 30, 40, 50]
print(numbers[1:3])   # [20, 30]
print(numbers[:2])    # [10, 20]
print(numbers[2:])    # [30, 40, 50]
```

## 4.2 Tuple (ทูเพิล)
คล้าย List แต่ **แก้ไขค่าไม่ได้** หลังสร้างแล้ว เหมาะกับข้อมูลที่ไม่ต้องการให้เปลี่ยนแปลง
```python
coordinate = (13.7563, 100.5018)  # พิกัด กรุงเทพฯ
print(coordinate[0])  # ละติจูด
```

## 4.3 Dictionary (ดิกชันนารี)
เก็บข้อมูลแบบ key-value เหมาะกับข้อมูลที่มีชื่อเรียกเฉพาะ
```python
employee = {
    "name": "สมชาย ใจดี",
    "position": "โปรแกรมเมอร์",
    "salary": 30000
}

print(employee["name"])
employee["salary"] = 32000   # แก้ไขค่า
employee["email"] = "somchai@email.com"  # เพิ่มข้อมูลใหม่

for key, value in employee.items():
    print(key, ":", value)
```

## 4.4 Set (เซ็ต)
เก็บข้อมูลที่ไม่ซ้ำกัน ไม่เรียงลำดับ เหมาะกับการกรองข้อมูลซ้ำ
```python
tags = {"python", "excel", "python", "sql"}
print(tags)  # {'python', 'excel', 'sql'} -> ตัวซ้ำหายไปอัตโนมัติ

tags.add("power bi")
print(tags)
```

## 4.5 List Comprehension เบื้องต้น
วิธีย่อการสร้างลิสต์ใหม่จากลิสต์เดิม
```python
numbers = [1, 2, 3, 4, 5]
squares = [n ** 2 for n in numbers]
print(squares)  # [1, 4, 9, 16, 25]

even_numbers = [n for n in numbers if n % 2 == 0]
print(even_numbers)  # [2, 4]
```

## 4.6 ตัวอย่างใช้งานจริง: ระบบสรุปยอดขายพนักงาน
```python
sales_data = [
    {"name": "สมชาย", "sales": 15000},
    {"name": "สมหญิง", "sales": 22000},
    {"name": "สมศรี", "sales": 9000},
]

total_sales = 0
for employee in sales_data:
    total_sales += employee["sales"]
    if employee["sales"] >= 10000:
        commission = employee["sales"] * 0.05
    else:
        commission = employee["sales"] * 0.03
    print(employee["name"], "ได้คอมมิชชั่น:", commission)

print("ยอดขายรวมทั้งหมด:", total_sales)
```

## แบบฝึกหัดท้ายบทที่ 4
1. สร้าง List รายชื่อสินค้า 5 รายการ แล้วเขียนโปรแกรมค้นหาว่ามีสินค้าที่ต้องการหรือไม่
2. สร้าง Dictionary เก็บข้อมูลสินค้า (ชื่อ, ราคา, จำนวนคงเหลือ) แล้วเขียนโปรแกรมคำนวณมูลค่าสินค้าคงคลังทั้งหมด
3. ใช้ Set หาว่าลูกค้า 2 กลุ่มซื้อสินค้าตัวไหนที่ซ้ำกันบ้าง (ใช้ operator `&`)
4. ใช้ List Comprehension แปลงรายชื่อสินค้าทั้งหมดให้เป็นตัวพิมพ์ใหญ่

---

# บทที่ 5: การจัดการไฟล์และข้อผิดพลาดเบื้องต้น

## วัตถุประสงค์การเรียนรู้
เมื่อจบบทเรียนนี้ ผู้เรียนจะสามารถ:
- อ่านและเขียนข้อมูลลงไฟล์ข้อความ (.txt) ได้
- อ่านและเขียนไฟล์ CSV เบื้องต้นได้
- ดักจับข้อผิดพลาด (exception) เพื่อป้องกันโปรแกรมหยุดทำงานกะทันหัน
- ประยุกต์ความรู้ทั้งหมดทำโปรเจกต์ขนาดเล็กแบบครบวงจร

## 5.1 การเขียนไฟล์ (Write)
```python
with open("data.txt", "w", encoding="utf-8") as file:
    file.write("รายการที่ 1: ซื้อวัตถุดิบ\n")
    file.write("รายการที่ 2: จ่ายค่าเช่า\n")
```
> การใช้ `with open(...) as file:` ช่วยให้ไฟล์ถูกปิดอัตโนมัติหลังใช้งานเสร็จ ไม่ต้องเขียน `file.close()` เอง

## 5.2 การอ่านไฟล์ (Read)
```python
with open("data.txt", "r", encoding="utf-8") as file:
    content = file.read()
    print(content)
```
```python
with open("data.txt", "r", encoding="utf-8") as file:
    for line in file:
        print(line.strip())
```

## 5.3 การเพิ่มข้อมูลต่อท้ายไฟล์ (Append)
```python
with open("data.txt", "a", encoding="utf-8") as file:
    file.write("รายการที่ 3: ค่าไฟฟ้า\n")
```

## 5.4 การทำงานกับไฟล์ CSV เบื้องต้น
```python
import csv

# เขียนไฟล์ CSV
with open("expenses.csv", "w", newline="", encoding="utf-8") as file:
    writer = csv.writer(file)
    writer.writerow(["รายการ", "จำนวนเงิน"])
    writer.writerow(["ค่าเช่า", 5000])
    writer.writerow(["ค่าไฟฟ้า", 800])

# อ่านไฟล์ CSV
with open("expenses.csv", "r", encoding="utf-8") as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)
```

## 5.5 การจัดการข้อผิดพลาด (try-except)
```python
try:
    number = int(input("กรอกตัวเลข: "))
    result = 100 / number
    print("ผลลัพธ์:", result)
except ValueError:
    print("กรุณากรอกเฉพาะตัวเลขเท่านั้น")
except ZeroDivisionError:
    print("ไม่สามารถหารด้วยศูนย์ได้")
```

## 5.6 try-except-else-finally
```python
try:
    with open("data.txt", "r", encoding="utf-8") as file:
        content = file.read()
except FileNotFoundError:
    print("ไม่พบไฟล์ที่ต้องการ")
else:
    print("อ่านไฟล์สำเร็จ")
finally:
    print("จบการทำงานของโปรแกรม")
```

## 5.7 โปรเจกต์ส่งท้าย: ระบบบันทึกรายรับ-รายจ่ายส่วนตัว
โปรเจกต์นี้รวมความรู้จากทั้ง 5 บท: ตัวแปร, เงื่อนไข, ลูป, ฟังก์ชัน, ลิสต์/ดิกชันนารี, และการจัดการไฟล์

```python
import csv

FILE_NAME = "budget.csv"

def add_transaction(description, amount, category):
    with open(FILE_NAME, "a", newline="", encoding="utf-8") as file:
        writer = csv.writer(file)
        writer.writerow([description, amount, category])

def show_summary():
    total = 0
    try:
        with open(FILE_NAME, "r", encoding="utf-8") as file:
            reader = csv.reader(file)
            for row in reader:
                description, amount, category = row
                total += float(amount)
                print(f"{description} | {amount} บาท | {category}")
    except FileNotFoundError:
        print("ยังไม่มีข้อมูลรายการ")
        return
    print("ยอดรวมสุทธิ:", total, "บาท")

def main():
    while True:
        print("\n1. เพิ่มรายการ")
        print("2. ดูสรุปทั้งหมด")
        print("3. ออกจากโปรแกรม")
        choice = input("เลือกเมนู: ")

        if choice == "1":
            description = input("รายการ: ")
            try:
                amount = float(input("จำนวนเงิน (รายจ่ายใส่ค่าติดลบ): "))
            except ValueError:
                print("กรุณากรอกตัวเลขเท่านั้น")
                continue
            category = input("หมวดหมู่: ")
            add_transaction(description, amount, category)
            print("บันทึกสำเร็จ")
        elif choice == "2":
            show_summary()
        elif choice == "3":
            print("ขอบคุณที่ใช้งาน")
            break
        else:
            print("กรุณาเลือกเมนูให้ถูกต้อง")

main()
```

## แบบฝึกหัดท้ายบทที่ 5
1. ปรับปรุงโปรเจกต์รายรับ-รายจ่าย ให้เพิ่มฟังก์ชันแสดงเฉพาะรายจ่ายในหมวดหมู่ที่ระบุ
2. เขียนโปรแกรมอ่านไฟล์ CSV รายชื่อสินค้าและราคา แล้วคำนวณราคาเฉลี่ยของสินค้าทั้งหมด
3. เพิ่มการดักจับข้อผิดพลาดในโปรเจกต์ ให้ครอบคลุมกรณีไฟล์ CSV มีรูปแบบข้อมูลผิดพลาด (เช่น จำนวนคอลัมน์ไม่ครบ)
4. **โปรเจกต์ปิดคอร์ส:** ให้ผู้เรียนออกแบบและเขียนโปรแกรมจัดการข้อมูลขนาดเล็กที่เกี่ยวข้องกับงานของตนเอง (เช่น ระบบเช็คสต๊อกสินค้า, ระบบบันทึกเวลาเข้า-ออกงาน) โดยต้องใช้ตัวแปร เงื่อนไข ลูป ฟังก์ชัน โครงสร้างข้อมูล และการอ่าน/เขียนไฟล์อย่างน้อยอย่างละ 1 จุด

---

## ภาพรวมการประเมินผลที่แนะนำ
| บทที่ | หัวข้อหลัก | รูปแบบการประเมิน |
|---|---|---|
| 1 | ตัวแปรและชนิดข้อมูล | แบบฝึกหัดในคลาส + การบ้าน |
| 2 | เงื่อนไขและลูป | แบบฝึกหัด + Quiz สั้น |
| 3 | ฟังก์ชัน | แบบฝึกหัด + รีวิวโค้ดเป็นกลุ่ม |
| 4 | โครงสร้างข้อมูล | แบบฝึกหัด + Case study |
| 5 | ไฟล์และ Error Handling | โปรเจกต์ปิดคอร์ส (Capstone) |

> **หมายเหตุสำหรับผู้สอน:** เนื่องจากกลุ่มเป้าหมายเป็นวัยทำงาน ควรเน้นตัวอย่างที่ใกล้เคียงกับงานจริงของผู้เรียนแต่ละกลุ่ม (เช่น งานบัญชี ใช้ตัวอย่างการเงิน, งาน HR ใช้ตัวอย่างข้อมูลพนักงาน) เพื่อให้เห็นประโยชน์การนำไปใช้ได้ทันที
