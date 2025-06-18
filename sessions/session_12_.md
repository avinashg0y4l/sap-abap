# Session 11: Modularization in ABAP

## 🎯 Objective
Understand and implement modularization techniques in ABAP to make code more structured, reusable, and maintainable.

---

## 🔹 What is Modularization in ABAP?

Modularization is the technique of dividing large programs into smaller, manageable, and reusable blocks (modules).

**Benefits:**
- Improves readability
- Enables reuse of code
- Simplifies debugging and testing
- Reduces redundancy

---

## 🔸 Types of Modularization Techniques

### ✅ A. INCLUDE

- Used to insert reusable ABAP code from one program into another.
- Typically used for code reuse like declarations or logic blocks.

**Syntax:**
```abap
INCLUDE zinclude_name.

```

### ✅ B. SUBROUTINE (FORM...ENDFORM)

- A reusable block of code that can be called multiple times.
- Good for encapsulating a procedure.

**Syntax:**
```abap

PERFORM sub_name USING lv_input CHANGING lv_output.

```