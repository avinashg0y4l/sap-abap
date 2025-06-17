# Session 11: Field Symbols in ABAP

## 🔍 Topic
- Introduction to Field Symbols
- Difference between Field Symbol and Work Area
- Using Field Symbols in Internal Table operations

---

## 🧾 Notes

### 🔹 What is a Field Symbol?
- A **Field Symbol** in ABAP is similar to a **pointer** in other programming languages (like C/C++). It does not store data by itself — instead, it points to the memory location of an existing variable or data object.


Field Symbols help to:
- ✅ Reduce memory consumption
- ⚡ Improve program performance
- 🔁 Avoid copying data in loops or operations

---

## 🧠 Syntax

```abap
FIELD-SYMBOLS: <fs_example> TYPE data_type.

ASSIGN variable TO <fs_example>.