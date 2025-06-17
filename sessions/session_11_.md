# Session 11: Field Symbols in ABAP

## 🔍 Topic
- Introduction to Field Symbols
- Difference between Field Symbol and Work Area
- Using Field Symbols in Internal Table operations

---

## 🧾 Notes

### 🔹 What is a Field Symbol?
- Field symbols in ABAP act like pointers in C.
- They are placeholders or symbolic names for other fields.
- They **do not store data**, but **reference** existing data objects dynamically at runtime.

### 🔹 Syntax
```abap
FIELD-SYMBOLS: <fs> TYPE data_type.
ASSIGN variable TO <fs>.