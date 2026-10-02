# เอกสารประกอบการสอน: การสร้างฟอร์มด้วย Python Tkinter

Sep 29, 2026

## 1. บทนำ

Tkinter คือไลบรารีสร้างหน้าจอ GUI ที่ติดมากับ Python อยู่แล้ว ไม่ต้องติดตั้งเพิ่ม เหมาะกับการเริ่มต้นเรียนการสร้างฟอร์มรับข้อมูล เช่น ช่องกรอกข้อความ กล่องเลือก และปุ่มกด

**วัตถุประสงค์การเรียนรู้** เมื่อจบบทเรียน นักศึกษาสามารถ:

1. สร้างหน้าต่างโปรแกรมและจัดวางวิดเจ็ตด้วย `grid()` ได้
2. ใช้ Entry, Text, Checkbutton, Radiobutton, Combobox, Listbox และ Spinbox ได้
3. อ่านค่าจากฟอร์มเมื่อกดปุ่ม และแสดงผลด้วย messagebox ได้
4. ตรวจสอบความถูกต้องของข้อมูลก่อนบันทึกได้

**สิ่งที่ต้องเตรียม**

- Python 3.8 ขึ้นไป (ตรวจสอบด้วยคำสั่ง `python --version`)
- ทดสอบว่า Tkinter ใช้งานได้ด้วยคำสั่ง `python -m tkinter` ถ้ามีหน้าต่างเล็กๆ เด้งขึ้นมาแสดงว่าพร้อมใช้
- โปรแกรมแก้ไขโค้ด เช่น VS Code, Thonny หรือ IDLE

**เวลาเรียนโดยประมาณ:** 3 ชั่วโมง (บรรยาย 1 ชั่วโมง ปฏิบัติ 2 ชั่วโมง)

## 2. โครงสร้างโปรแกรมพื้นฐานและการจัดวาง

ทุกโปรแกรม Tkinter มี 3 ขั้นตอน: สร้างหน้าต่างหลัก, วางวิดเจ็ตลงในหน้าต่าง, แล้วเรียก `mainloop()` เพื่อให้โปรแกรมรอรับการกระทำจากผู้ใช้

```python
import tkinter as tk
from tkinter import ttk, messagebox

root = tk.Tk()               # 1. สร้างหน้าต่างหลัก
root.title("ฟอร์มแรกของฉัน")
root.geometry("400x300")     # กว้าง x สูง (พิกเซล)

lbl = tk.Label(root, text="สวัสดี Tkinter")
lbl.grid(row=0, column=0, padx=10, pady=10)   # 2. วางวิดเจ็ต

root.mainloop()              # 3. เริ่มรอรับเหตุการณ์
```

**การจัดวางด้วย grid()** มองหน้าต่างเป็นตารางแถวและคอลัมน์ เหมาะกับฟอร์มที่สุด เพราะป้ายชื่ออยู่คอลัมน์ซ้าย ช่องกรอกอยู่คอลัมน์ขวา

| พารามิเตอร์ | ความหมาย | ตัวอย่าง |
| --- | --- | --- |
| `row`, `column` | ตำแหน่งแถวและคอลัมน์ (เริ่มที่ 0) | `row=1, column=0` |
| `padx`, `pady` | ระยะห่างรอบวิดเจ็ต (พิกเซล) | `padx=5, pady=5` |
| `sticky` | ชิดด้านใด: `"w"` ซ้าย, `"e"` ขวา, `"ew"` ยืดเต็มความกว้าง | `sticky="w"` |
| `columnspan` | วิดเจ็ตกินพื้นที่หลายคอลัมน์ | `columnspan=2` |

**ข้อควรระวัง:** ห้ามใช้ `grid()` กับ `pack()` ปนกันในหน้าต่างหรือ Frame เดียวกัน โปรแกรมจะค้าง

**Variable ของ Tkinter** ใช้ผูกค่ากับวิดเจ็ต เพื่อให้อ่านหรือเปลี่ยนค่าได้ง่ายด้วย `.get()` และ `.set()`

| คลาส | เก็บค่าประเภท | ใช้บ่อยกับ |
| --- | --- | --- |
| `tk.StringVar()` | ข้อความ | Entry, Radiobutton, Combobox |
| `tk.IntVar()` | จำนวนเต็ม | Checkbutton, Radiobutton, Spinbox |
| `tk.BooleanVar()` | True / False | Checkbutton |
| `tk.DoubleVar()` | ทศนิยม | Scale, Spinbox |

## 3. Label และ Entry (Textbox)

Label ใช้แสดงข้อความบอกผู้ใช้ ส่วน Entry คือช่องกรอกข้อความบรรทัดเดียว เป็นวิดเจ็ตที่ใช้บ่อยที่สุดในฟอร์ม

```python
import tkinter as tk

root = tk.Tk()
root.title("ตัวอย่าง Entry")

# ป้ายชื่อ + ช่องกรอกชื่อ
tk.Label(root, text="ชื่อ:").grid(row=0, column=0, sticky="e", padx=5, pady=5)
name_var = tk.StringVar()
entry_name = tk.Entry(root, textvariable=name_var, width=25)
entry_name.grid(row=0, column=1, padx=5, pady=5)

# ช่องรหัสผ่าน ซ่อนตัวอักษรด้วย show="*"
tk.Label(root, text="รหัสผ่าน:").grid(row=1, column=0, sticky="e", padx=5, pady=5)
entry_pw = tk.Entry(root, show="*", width=25)
entry_pw.grid(row=1, column=1, padx=5, pady=5)

def show():
    print("ชื่อ:", name_var.get())       # อ่านค่าผ่าน StringVar
    print("รหัส:", entry_pw.get())       # อ่านค่าจาก Entry โดยตรง

tk.Button(root, text="แสดงค่า", command=show).grid(row=2, column=1, sticky="w")

entry_name.focus()   # ให้เคอร์เซอร์อยู่ที่ช่องชื่อตอนเปิดโปรแกรม
root.mainloop()
```

**คำสั่งที่ใช้บ่อยกับ Entry**

| คำสั่ง | ผลลัพธ์ |
| --- | --- |
| `entry.get()` | อ่านข้อความในช่อง (ได้ค่าเป็น string เสมอ) |
| `entry.delete(0, tk.END)` | ลบข้อความทั้งหมด |
| `entry.insert(0, "ข้อความ")` | ใส่ข้อความตั้งต้น |
| `entry.config(state="disabled")` | ปิดไม่ให้แก้ไข (`"normal"` เพื่อเปิดกลับ) |
| `entry.focus()` | ย้ายเคอร์เซอร์มาที่ช่องนี้ |

**จุดที่นักศึกษามักพลาด:** ค่าจาก `get()` เป็นข้อความเสมอ ถ้าต้องการคำนวณต้องแปลงก่อน เช่น `int(entry_age.get())` และควรครอบด้วย `try/except ValueError` เผื่อผู้ใช้กรอกตัวอักษร

## 4. Text (กล่องข้อความหลายบรรทัด)

ใช้ Text เมื่อต้องการให้ผู้ใช้พิมพ์ได้หลายบรรทัด เช่น ที่อยู่หรือความคิดเห็น ต่างจาก Entry ตรงที่การอ่านค่าต้องระบุตำแหน่งเริ่มและสิ้นสุด

```python
tk.Label(root, text="ที่อยู่:").grid(row=0, column=0, sticky="ne", padx=5, pady=5)
txt_addr = tk.Text(root, width=30, height=4)   # height = จำนวนบรรทัด
txt_addr.grid(row=0, column=1, padx=5, pady=5)

# อ่านค่า: ตั้งแต่บรรทัด 1 ตัวอักษรที่ 0 ถึงท้ายสุด (ตัด \n ท้ายออกด้วย strip)
address = txt_addr.get("1.0", tk.END).strip()

# ลบทั้งหมด / ใส่ข้อความ
txt_addr.delete("1.0", tk.END)
txt_addr.insert("1.0", "123 ถ.กาญจนวนิช")
```

**จำง่ายๆ:** ตำแหน่งใน Text เขียนเป็น `"บรรทัด.ตัวอักษร"` โดยบรรทัดเริ่มที่ 1 แต่ตัวอักษรเริ่มที่ 0 ดังนั้น `"1.0"` คือจุดเริ่มต้นของข้อความ

Text ไม่รองรับ `textvariable` จึงต้องใช้ `get()` กับ `insert()` โดยตรงเท่านั้น

## 5. Checkbutton (Checkbox)

Checkbutton ให้ผู้ใช้ติ๊กเลือกได้หลายข้อพร้อมกัน แต่ละกล่องต้องมีตัวแปรของตัวเอง 1 ตัว ค่าเริ่มต้นคือ 1 เมื่อติ๊ก และ 0 เมื่อไม่ติ๊ก

```python
tk.Label(root, text="งานอดิเรก:").grid(row=0, column=0, sticky="ne", padx=5)

hobbies = {
    "อ่านหนังสือ": tk.IntVar(),
    "เล่นกีฬา":    tk.IntVar(),
    "เขียนโปรแกรม": tk.IntVar(value=1),   # ติ๊กไว้ล่วงหน้า
}

for i, (name, var) in enumerate(hobbies.items()):
    tk.Checkbutton(root, text=name, variable=var).grid(row=i, column=1, sticky="w")

def show():
    selected = [name for name, var in hobbies.items() if var.get() == 1]
    print("เลือก:", ", ".join(selected) or "ไม่ได้เลือก")
```

**กล่องยอมรับเงื่อนไข** เป็นการใช้ Checkbutton แบบเดี่ยวที่พบบ่อย ใช้ `BooleanVar` จะอ่านง่ายกว่า

```python
agree_var = tk.BooleanVar()
tk.Checkbutton(root, text="ยอมรับเงื่อนไขการใช้งาน", variable=agree_var).grid(row=5, column=1, sticky="w")

if not agree_var.get():
    print("กรุณายอมรับเงื่อนไขก่อน")
```

**ตัวเลือกเพิ่มเติม:** `onvalue` และ `offvalue` กำหนดค่าเองได้ เช่น `onvalue="Y", offvalue="N"` คู่กับ `StringVar` และ `command=ฟังก์ชัน` เพื่อให้ทำงานทันทีที่ติ๊ก

## 6. Radiobutton (เลือกได้ข้อเดียว)

Radiobutton ใช้เมื่อผู้ใช้ต้องเลือกเพียงหนึ่งตัวเลือกจากกลุ่ม ปุ่มทุกตัวในกลุ่มต้องใช้ตัวแปร **ตัวเดียวกัน** แต่มี `value` ต่างกัน นี่คือจุดต่างสำคัญจาก Checkbutton

```python
tk.Label(root, text="เพศ:").grid(row=0, column=0, sticky="e", padx=5)

gender_var = tk.StringVar(value="ไม่ระบุ")   # ค่าเริ่มต้น
frame_gender = tk.Frame(root)
frame_gender.grid(row=0, column=1, sticky="w")

for g in ["ชาย", "หญิง", "ไม่ระบุ"]:
    tk.Radiobutton(frame_gender, text=g, variable=gender_var, value=g).pack(side="left")

print("เพศที่เลือก:", gender_var.get())
```

ตัวอย่างนี้ใช้ Frame รวมปุ่มไว้ในช่องเดียวของ grid แล้วใช้ `pack(side="left")` ภายใน Frame เพื่อให้ปุ่มเรียงแนวนอน ทำได้เพราะเป็นคนละ container กับ root

**เปรียบเทียบ Checkbutton กับ Radiobutton**

| หัวข้อ | Checkbutton | Radiobutton |
| --- | --- | --- |
| จำนวนที่เลือกได้ | หลายข้อ | ข้อเดียวในกลุ่ม |
| ตัวแปร | 1 ตัวต่อ 1 กล่อง | 1 ตัวต่อทั้งกลุ่ม |
| ตัวอย่างการใช้ | งานอดิเรก, ยอมรับเงื่อนไข | เพศ, ชั้นปี, วิธีชำระเงิน |

## 7. Combobox, Listbox และ Spinbox

ทั้งสามวิดเจ็ตให้ผู้ใช้เลือกจากรายการที่กำหนดไว้ ลดการพิมพ์ผิดได้ดีกว่า Entry

**Combobox (ดรอปดาวน์)** อยู่ในโมดูล `ttk` เหมาะกับรายการยาวที่เลือกได้ข้อเดียว

```python
from tkinter import ttk

tk.Label(root, text="คณะ:").grid(row=0, column=0, sticky="e", padx=5)
faculty_var = tk.StringVar()
cb = ttk.Combobox(root, textvariable=faculty_var, state="readonly",
                  values=["วิศวกรรมศาสตร์", "วิทยาศาสตร์", "บริหารธุรกิจ", "ศิลปศาสตร์"])
cb.grid(row=0, column=1, sticky="w")
cb.current(0)   # เลือกรายการแรกไว้ก่อน

# ทำงานทันทีเมื่อเปลี่ยนรายการ
cb.bind("<<ComboboxSelected>>", lambda e: print("เลือก:", faculty_var.get()))
```

`state="readonly"` บังคับให้เลือกจากรายการเท่านั้น ถ้าไม่ใส่ ผู้ใช้จะพิมพ์ค่าอื่นเองได้

**Listbox** แสดงรายการเป็นกล่อง และเลือกได้หลายข้อถ้าตั้ง `selectmode`

```python
lb = tk.Listbox(root, height=4, selectmode=tk.MULTIPLE, exportselection=False)
for s in ["Python", "Java", "C#", "JavaScript"]:
    lb.insert(tk.END, s)
lb.grid(row=1, column=1, sticky="w")

selected = [lb.get(i) for i in lb.curselection()]   # curselection() คืนค่าเป็น index
```

**Spinbox** ใช้รับตัวเลขในช่วงที่กำหนด มีปุ่มขึ้นลง

```python
age_var = tk.IntVar(value=18)
tk.Spinbox(root, from_=15, to=60, textvariable=age_var, width=5).grid(row=2, column=1, sticky="w")
```

สังเกตว่าใช้ `from_` (มีขีดล่าง) เพราะ `from` เป็นคำสงวนของ Python

## 8. Button, การรับค่า และการตรวจสอบข้อมูล

ปุ่มจะเรียกฟังก์ชันที่กำหนดใน `command` ทุกครั้งที่ถูกกด ฟังก์ชันนั้นคือที่ที่เราอ่านค่าจากทุกวิดเจ็ต ตรวจสอบ แล้วแสดงผล

```python
from tkinter import messagebox

def submit():
    name = name_var.get().strip()
    if name == "":
        messagebox.showwarning("ข้อมูลไม่ครบ", "กรุณากรอกชื่อ")
        entry_name.focus()
        return                      # หยุดทำงาน ไม่บันทึก
    messagebox.showinfo("สำเร็จ", f"บันทึกข้อมูลของ {name} แล้ว")

tk.Button(root, text="บันทึก", command=submit, width=10).grid(row=9, column=1, sticky="w")
```

**ข้อผิดพลาดที่พบบ่อยที่สุด:** เขียน `command=submit()` (มีวงเล็บ) ทำให้ฟังก์ชันทำงานทันทีตอนเปิดโปรแกรม ต้องเขียน `command=submit` โดยไม่มีวงเล็บ

**ชนิดของ messagebox**

| คำสั่ง | ใช้เมื่อ | ค่าที่คืนกลับ |
| --- | --- | --- |
| `showinfo(title, msg)` | แจ้งข้อมูลทั่วไป | `"ok"` |
| `showwarning(title, msg)` | เตือนผู้ใช้ | `"ok"` |
| `showerror(title, msg)` | แจ้งข้อผิดพลาด | `"ok"` |
| `askyesno(title, msg)` | ถามยืนยัน | `True` / `False` |

**ปุ่มล้างฟอร์ม** ตั้งค่าตัวแปรกลับเป็นค่าเริ่มต้น

```python
def clear():
    if messagebox.askyesno("ยืนยัน", "ต้องการล้างข้อมูลทั้งหมด?"):
        name_var.set("")
        txt_addr.delete("1.0", tk.END)
        agree_var.set(False)
        gender_var.set("ไม่ระบุ")
```

**แนวทางตรวจสอบข้อมูลก่อนบันทึก**

1. ช่องบังคับต้องไม่ว่าง (ใช้ `.strip()` ตัดช่องว่างก่อนตรวจ)
2. ตัวเลขต้องแปลงได้และอยู่ในช่วงที่ยอมรับ (ใช้ `try/except ValueError`)
3. รูปแบบเฉพาะ เช่น อีเมลต้องมี `@` หรือรหัสนักศึกษาต้องเป็นตัวเลข 10 หลัก (`s.isdigit() and len(s) == 10`)
4. แจ้งข้อผิดพลาดทีละข้อ แล้วย้าย focus ไปที่ช่องที่ผิด

## 9. ตัวอย่างรวม: ฟอร์มลงทะเบียนนักศึกษา

โปรแกรมนี้รวมทุกวิดเจ็ตที่เรียนมา ให้นักศึกษาพิมพ์ตามและทดลองรัน แล้วอธิบายว่าแต่ละบรรทัดทำอะไร

```python
import tkinter as tk
from tkinter import ttk, messagebox

root = tk.Tk()
root.title("ฟอร์มลงทะเบียนนักศึกษา")
root.resizable(False, False)

form = tk.Frame(root, padx=15, pady=15)
form.grid(row=0, column=0)

def add_label(text, row):
    tk.Label(form, text=text).grid(row=row, column=0, sticky="ne", padx=5, pady=4)

# ---------- ตัวแปร ----------
sid_var     = tk.StringVar()
name_var    = tk.StringVar()
gender_var  = tk.StringVar(value="ไม่ระบุ")
faculty_var = tk.StringVar()
year_var    = tk.IntVar(value=1)
agree_var   = tk.BooleanVar()
hobbies = {h: tk.IntVar() for h in ["กีฬา", "ดนตรี", "เขียนโปรแกรม"]}

# ---------- วิดเจ็ต ----------
add_label("รหัสนักศึกษา:", 0)
entry_sid = tk.Entry(form, textvariable=sid_var, width=28)
entry_sid.grid(row=0, column=1, sticky="w")

add_label("ชื่อ-สกุล:", 1)
entry_name = tk.Entry(form, textvariable=name_var, width=28)
entry_name.grid(row=1, column=1, sticky="w")

add_label("เพศ:", 2)
f_gender = tk.Frame(form)
f_gender.grid(row=2, column=1, sticky="w")
for g in ["ชาย", "หญิง", "ไม่ระบุ"]:
    tk.Radiobutton(f_gender, text=g, variable=gender_var, value=g).pack(side="left")

add_label("คณะ:", 3)
cb_faculty = ttk.Combobox(form, textvariable=faculty_var, state="readonly", width=25,
                          values=["วิศวกรรมศาสตร์", "วิทยาศาสตร์", "บริหารธุรกิจ", "ศิลปศาสตร์"])
cb_faculty.grid(row=3, column=1, sticky="w")

add_label("ชั้นปี:", 4)
tk.Spinbox(form, from_=1, to=4, textvariable=year_var, width=5,
           state="readonly").grid(row=4, column=1, sticky="w")

add_label("งานอดิเรก:", 5)
f_hobby = tk.Frame(form)
f_hobby.grid(row=5, column=1, sticky="w")
for h, v in hobbies.items():
    tk.Checkbutton(f_hobby, text=h, variable=v).pack(side="left")

add_label("ที่อยู่:", 6)
txt_addr = tk.Text(form, width=28, height=3)
txt_addr.grid(row=6, column=1, sticky="w")

tk.Checkbutton(form, text="ยืนยันว่าข้อมูลถูกต้อง",
               variable=agree_var).grid(row=7, column=1, sticky="w", pady=4)

# ---------- ฟังก์ชัน ----------
def validate():
    sid = sid_var.get().strip()
    if not (sid.isdigit() and len(sid) == 10):
        return "รหัสนักศึกษาต้องเป็นตัวเลข 10 หลัก", entry_sid
    if name_var.get().strip() == "":
        return "กรุณากรอกชื่อ-สกุล", entry_name
    if faculty_var.get() == "":
        return "กรุณาเลือกคณะ", cb_faculty
    if not agree_var.get():
        return "กรุณาติ๊กยืนยันข้อมูล", None
    return None, None

def submit():
    error, widget = validate()
    if error:
        messagebox.showwarning("ข้อมูลไม่ถูกต้อง", error)
        if widget:
            widget.focus()
        return
    chosen = [h for h, v in hobbies.items() if v.get() == 1]
    summary = (
        f"รหัส: {sid_var.get()}\n"
        f"ชื่อ: {name_var.get()}\n"
        f"เพศ: {gender_var.get()}\n"
        f"คณะ: {faculty_var.get()} ปี {year_var.get()}\n"
        f"งานอดิเรก: {', '.join(chosen) or '-'}\n"
        f"ที่อยู่: {txt_addr.get('1.0', tk.END).strip() or '-'}"
    )
    messagebox.showinfo("ลงทะเบียนสำเร็จ", summary)

def clear():
    if not messagebox.askyesno("ยืนยัน", "ล้างข้อมูลทั้งหมด?"):
        return
    sid_var.set(""); name_var.set(""); faculty_var.set("")
    gender_var.set("ไม่ระบุ"); year_var.set(1); agree_var.set(False)
    for v in hobbies.values():
        v.set(0)
    txt_addr.delete("1.0", tk.END)
    entry_sid.focus()

f_btn = tk.Frame(form)
f_btn.grid(row=8, column=1, sticky="w", pady=8)
tk.Button(f_btn, text="บันทึก", width=10, command=submit).pack(side="left", padx=(0, 5))
tk.Button(f_btn, text="ล้างข้อมูล", width=10, command=clear).pack(side="left")

entry_sid.focus()
root.mainloop()
```

**ประเด็นชวนนักศึกษาสังเกตระหว่างอธิบายโค้ด**

- ฟังก์ชัน `add_label()` ลดการเขียนโค้ดซ้ำ 7 ครั้งเหลือบรรทัดเดียว
- `validate()` แยกการตรวจสอบออกจาก `submit()` ทำให้อ่านง่ายและแก้ไขเงื่อนไขได้ที่เดียว
- Frame ช่วยให้ใช้ `pack()` ภายในได้ โดยไม่ขัดกับ `grid()` ของ form

## 10. ตารางสรุปและแบบฝึกหัด

**ตารางสรุปวิดเจ็ตฟอร์ม**

| วิดเจ็ต | ใช้ทำอะไร | ตัวแปรที่ใช้ | อ่านค่าด้วย |
| --- | --- | --- | --- |
| `Entry` | ข้อความบรรทัดเดียว | StringVar | `var.get()` หรือ `entry.get()` |
| `Text` | ข้อความหลายบรรทัด | ไม่มี | `txt.get("1.0", tk.END)` |
| `Checkbutton` | เลือกได้หลายข้อ / ยอมรับเงื่อนไข | IntVar, BooleanVar (1 ตัวต่อกล่อง) | `var.get()` |
| `Radiobutton` | เลือกข้อเดียวในกลุ่ม | StringVar, IntVar (1 ตัวต่อกลุ่ม) | `var.get()` |
| `ttk.Combobox` | ดรอปดาวน์ | StringVar | `var.get()` |
| `Listbox` | รายการ เลือกได้หลายข้อ | ไม่มี | `lb.curselection()` |
| `Spinbox` | ตัวเลขในช่วงที่กำหนด | IntVar | `var.get()` |
| `Button` | เรียกฟังก์ชันเมื่อกด | ไม่มี | `command=ฟังก์ชัน` |

**แบบฝึกหัด** (เรียงจากง่ายไปยาก)

1. สร้างฟอร์มเข้าสู่ระบบ มีช่องชื่อผู้ใช้และรหัสผ่าน (ซ่อนตัวอักษร) ถ้ากรอก `admin` / `1234` ให้แสดง "เข้าสู่ระบบสำเร็จ" นอกนั้นแสดง error
2. เพิ่ม Checkbutton "แสดงรหัสผ่าน" ในข้อ 1 เมื่อติ๊กให้เปลี่ยน `show` ของช่องรหัสผ่านเป็น `""` และเมื่อไม่ติ๊กให้กลับเป็น `"*"`
3. สร้างโปรแกรมคำนวณ BMI รับน้ำหนักและส่วนสูงจาก Entry ตรวจสอบว่าเป็นตัวเลขที่มากกว่า 0 แล้วแสดงผลใน Label พร้อมแปลผล (ผอม, ปกติ, น้ำหนักเกิน)
4. สร้างฟอร์มสั่งอาหาร: Radiobutton เลือกขนาด (S 40 บาท, M 60 บาท, L 80 บาท), Checkbutton เลือกท็อปปิ้ง (อย่างละ 10 บาท), Spinbox เลือกจำนวน 1–10 แล้วคำนวณราคารวม
5. ต่อยอดตัวอย่างข้อ 9 ให้บันทึกข้อมูลที่ลงทะเบียนลงไฟล์ `students.csv` และแสดงรายชื่อที่บันทึกแล้วใน Listbox

**เกณฑ์การให้คะแนนแนะนำ (ต่อข้อ)**

| เกณฑ์ | คะแนน |
| --- | --- |
| โปรแกรมทำงานได้ตามโจทย์ | 5 |
| ตรวจสอบข้อมูลและแจ้งข้อผิดพลาดครบ | 3 |
| จัดวางหน้าจอเป็นระเบียบ อ่านง่าย | 2 |
