# Cambridge A Level Computer Science (9618)
# Chapter 1: Information Representation

> **Teaching Notes (Roman Urdu)**  
> Yeh notes specially teachers ke liye banaye gaye hain taake woh students ko asaani se concept samjha saken.

---

# What is Information Representation?

Sab se pehle student ko yeh concept samjhao.

## Definition

Computer sirf **0 aur 1** samajhta hai.

Is liye har cheez (numbers, letters, pictures, sound, videos) ko **Binary (0 aur 1)** ki form mein convert kiya jata hai.

### Example

```
A → 01000001

5 → 00000101

Red Colour → Binary Values

Music → Binary Values

Image → Binary Values
```

**Conclusion**

Computer ke andar har cheez Binary hoti hai.

---

# Topic 1.1 — Data Representation

Is topic ke 8 important parts hain.

---

# 1. Binary Magnitudes & Prefixes

Sab se pehle student se poochho:

> **1 KB kitna hota hai?**

Most students kahenge

```
1000 Bytes
```

Yeh galat bhi nahi hai.

Computer Science mein **2 systems** use hote hain.

---

## Decimal Prefixes (SI Units)

Yeh humans use karte hain.

```
Kilo = 1000

Mega = 1000²

Giga = 1000³

Tera = 1000⁴
```

### Example

```
1 Kilometre = 1000 metres

1 Kilogram = 1000 grams
```

---

## Binary Prefixes

Computer Binary system use karta hai.

```
Kibi = 1024 Bytes

Mebi = 1024 KiB

Gibi = 1024 MiB

Tebi = 1024 GiB
```

### Comparison Table

| Decimal Prefix | Binary Prefix |
|---------------|---------------|
| Kilo (KB) = 1000 | Kibi (KiB) = 1024 |
| Mega (MB) = 1000² | Mebi (MiB) = 1024² |
| Giga (GB) = 1000³ | Gibi (GiB) = 1024³ |
| Tera (TB) = 1000⁴ | Tebi (TiB) = 1024⁴ |

### Easy Trick

Agar prefix mein **"bi"** ho

```
KiBi

MeBi

GiBi

TeBi
```

to matlab

```
1024
```

Agar

```
Kilo

Mega

Giga

Tera
```

to matlab

```
1000
```

---

# 2. Number Systems

Computer different number systems use karta hai.

## Binary

Digits:

```
0
1
```

Base:

```
2
```

Example

```
101101
```

---

## Denary (Decimal)

Hum roz use karte hain.

Digits

```
0–9
```

Base

```
10
```

---

## Hexadecimal

Digits

```
0–9

A B C D E F
```

Values

```
A = 10

B = 11

...

F = 15
```

Base

```
16
```

---

## Binary Coded Decimal (BCD)

Har decimal digit ko separately Binary mein convert karte hain.

Example

Decimal Number

```
59
```

Normal Binary

```
111011
```

BCD

```
5 → 0101

9 → 1001
```

Answer

```
0101 1001
```

---

## One's Complement

Negative number represent karne ke liye bits reverse karte hain.

Rule

```
0 → 1

1 → 0
```

Example

```
101100
```

↓

```
010011
```

---

## Two's Complement

Steps

1. Find One's Complement
2. Add 1

Example

```
101100
```

↓

```
010011
```

↓

```
010100
```

---

# 3. Number Base Conversion

Students ko yeh sab conversions aani chahiye.

- Binary → Decimal
- Decimal → Binary
- Binary → Hexadecimal
- Hexadecimal → Binary
- Decimal → Hexadecimal
- Hexadecimal → Decimal
- BCD Conversions

> **Exam ka sab se important topic.**

---

# 4. Binary Addition

Rules

```
0 + 0 = 0

0 + 1 = 1

1 + 0 = 1

1 + 1 = 10

1 + 1 + 1 = 11
```

Example

```
1010

0011

-----

1101
```

---

# 5. Binary Subtraction

Rules

```
1 − 0 = 1

1 − 1 = 0

0 − 0 = 0

0 − 1 → Borrow
```

---

# 6. Overflow

Overflow tab hota hai jab answer ko store karne ke liye bits kam ho jayein.

Example

4-bit system

Maximum value

```
1111
```

Addition

```
1111

0001

-----

10000
```

Lekin sirf 4 bits available hain.

Store hoga

```
0000
```

Yeh **Overflow** hai.

---

# 7. Practical Uses

## Hexadecimal

Use hota hai

- HTML Colour Codes
- Memory Addresses
- MAC Addresses
- Error Codes

Examples

```
#FF0000

#00FF00

#0000FF
```

---

## Binary Coded Decimal (BCD)

Use hota hai

- Calculator
- Digital Clock
- Digital Meter
- Banking Machines

Reason

BCD decimal digits ko exact store karta hai.

---

# 8. Character Representation

Computer letters ko bhi Binary mein store karta hai.

Iske liye Character Sets use hote hain.

---

## ASCII

English characters.

Examples

```
A

B

C
```

Har character ki Binary value hoti hai.

---

## Extended ASCII

ASCII se zyada symbols.

Examples

```
£

€

©
```

---

## Unicode

Unicode almost har language support karta hai.

Examples

```
English

اردو

العربية

中文

日本語

😊
```

Modern computers Unicode use karte hain.

---

# Topic 1.2 — Multimedia

Do parts hain

- Graphics
- Sound

---

# Graphics

Graphics do types ki hoti hain.

- Bitmap
- Vector

---

# Bitmap Graphics

Bitmap image chhote chhote dots se banti hai.

Har dot ko **Pixel** kehte hain.

Example

```
🟩🟩🟩🟩

🟩🟥🟥🟩

🟩🟥🟥🟩

🟩🟩🟩🟩
```

---

## Important Terms

### Pixel

Image ka smallest dot.

---

### Image Resolution

Image mein total pixels.

Example

```
1920 × 1080
```

---

### Colour Depth (Bit Depth)

Har pixel kitne colours show kar sakta hai.

Higher Colour Depth

- Better Quality
- Larger File Size

---

### File Header

Image ki information store karta hai.

Example

- Width
- Height
- Colour Depth
- File Format

---

# Bitmap File Size Formula

```
File Size

=

Width

×

Height

×

Colour Depth

÷

8
```

---

# Vector Graphics

Vector images pixels se nahi banti.

Shapes aur mathematical formulas use karti hain.

Examples

- Circle
- Rectangle
- Line
- Curve

---

## Important Terms

### Drawing Object

- Circle
- Rectangle
- Line

### Property

- Colour
- Size
- Thickness

### Drawing List

Sab objects ki list.

---

# Bitmap vs Vector

## Bitmap

Use for

- Photographs
- Camera Images

## Vector

Use for

- Logos
- Icons
- Maps
- Cartoons

---

# Sound Representation

Computer sound ko bhi Binary mein convert karta hai.

---

## Sampling

Continuous sound ko small pieces mein divide karna.

---

## Sampling Rate

1 second mein kitni baar sound record ki gayi.

Example

```
44100 Hz
```

Matlab

```
44100 samples per second
```

---

## Sampling Resolution

Har sample kitni detail se record hua.

---

## Analogue Data

Continuous signal.

Example

Human Voice.

---

## Digital Data

Binary form.

```
0 and 1
```

---

## Effect of Increasing Sampling Rate

- Better Quality
- Larger File Size

---

## Effect of Increasing Sampling Resolution

- Better Accuracy
- Larger File Size

---

# Topic 1.3 — Compression

## Why Compression?

Compression ka purpose file ko chhota banana hai.

Benefits

- Less Storage
- Faster Download
- Faster Upload
- Easy Email Sharing

---

# Types of Compression

## Lossless Compression

Original file perfectly recover ho sakti hai.

Quality lose nahi hoti.

Examples

- ZIP
- PNG
- FLAC

Use

- Documents
- Programs
- Text Files

---

## Lossy Compression

Kuch data permanently delete ho jata hai.

Quality thori kam hoti hai.

Examples

- JPEG
- MP3
- MP4

Use

- Photos
- Music
- Videos

---

# Compression of Different File Types

| File Type | Compression |
|-----------|-------------|
| Text File | Lossless |
| Bitmap Image | Lossless or Lossy |
| Vector Graphic | Lossless |
| Sound File | Lossless or Lossy |

---

# Final Revision Mind Map

```
Information Representation
│
├── Data Representation
│   ├── Binary Prefixes
│   ├── Decimal Prefixes
│   ├── Number Systems
│   ├── Number Conversion
│   ├── Binary Addition
│   ├── Binary Subtraction
│   ├── Overflow
│   ├── BCD
│   ├── Hexadecimal
│   └── ASCII / Unicode
│
├── Multimedia
│   ├── Bitmap
│   ├── Vector
│   ├── Sound
│   ├── Sampling
│   └── Resolution
│
└── Compression
    ├── Lossless
    └── Lossy
```

---

# Suggested Teaching Plan

Instead of teaching the entire chapter in one class, divide it into **10 lessons**.

| Lesson | Topic |
|---------|------|
| 1 | Information Representation & Binary Basics |
| 2 | Decimal vs Binary Prefixes |
| 3 | Number Systems (Binary, Denary, Hex, BCD) |
| 4 | Number Base Conversions |
| 5 | Binary Addition, Subtraction & Overflow |
| 6 | ASCII, Extended ASCII & Unicode |
| 7 | Bitmap Graphics & File Size Calculations |
| 8 | Vector Graphics & Bitmap vs Vector |
| 9 | Sound Representation (Sampling & Resolution) |
| 10 | Compression + Cambridge Style Practice Questions |

---

> **Teaching Tip:**  
> Har lesson ke end par 5–10 practice questions aur ek short quiz zaroor karwayein. Is se students ka concept strong hoga aur exam preparation bhi behtar hogi.
