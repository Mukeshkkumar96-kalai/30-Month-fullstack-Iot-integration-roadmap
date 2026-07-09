# Digital System Design — Unit 1: Number Systems
**Date:** 2026-06-30
**Topic Covered:** Number Systems (Decimal–Binary–Hex Conversions)

---

## 1) Today's Learnings

- Why digital systems exist (noise immunity via discrete 0/1 states) — historical context: vacuum tubes → transistors (1947) → ICs (1958-59).
- Why analog dominated audio/telephony for decades even after digital logic existed (sampling/ADC/DAC limitations, not "precise control").
- Positional number systems and place value (base/radix concept).
- Decimal → Binary conversion using the **division-by-2 method** (remainders, read bottom-to-top).
- Binary → Decimal conversion using **place values (powers of 2)** as a verification check.
- Why 1 hex digit = 4 binary bits, and why grouping works mathematically (because 16 = 2⁴, and 8 = 2³ for octal).
- Binary → Hexadecimal conversion using the **4-bit grouping method**, including how to pad with leading zeros correctly.

---

## 2) Explanation & Example (Simple Terms)

**Decimal to Binary (Division Method):**
Keep dividing the number by 2, write down the remainder (0 or 1) each time, stop when the quotient becomes 0. Read the remainders **bottom to top** — that's your binary number.

```
 Example: 50 → 50÷2=25 r0, 25÷2=12 r1, 12÷2=6 r0, 6÷2=3 r0, 3÷2=1 r1, 1÷2=0 r1   // r --> remainder
 Remainders bottom-to-top: **110010**
 Check: 32+16+2 = 50 ✓
```

**Binary to Hex (4-bit Grouping):**
Since 4 bits can represent exactly 0–15 (one hex digit's full range), split the binary number into groups of 4 starting from the **right**. Pad zeros on the **left** if the total bit count isn't a multiple of 4. Convert each group to its decimal value (0–15, using A–F for 10–15), then write the hex digits in the **same left-to-right order as the groups**.

```
 Example: 101111001 → pad to 12 bits → 0001 0111 1001 → 1, 7, 9 → **0x179**        // r --> remainder
 Check via full decimal conversion: binary = 377 decimal = 0x179 ✓
```

---

## 3) Problems Faced

- Wrote invalid binary digits (used 2 and 3 as bit coefficients) — binary digits can only be 0 or 1.
- Skipped a division step in the middle of a division-by-2 chain (jumped from quotient 5 straight to 1, missing the 2÷2 step), leading to a wrong/incomplete remainder sequence.
- Forgot to actually perform the **reversal** step after listing remainders — got lucky on two examples where the un-reversed and reversed sequences looked nearly identical (near-palindromes), which masked the mistake.
- In binary-to-hex grouping, calculated each 4-bit group's value correctly, but wrote the final hex digits in the **wrong order** (reverse of the correct left-to-right group order), and also kept an unnecessary leading zero digit.
- Did not show the final verification/reverse-conversion check when asked, relying on the answer alone instead of confirming it independently.

---

## 4) How I Fixed It

- Corrected invalid binary digits by re-deriving the conversion using only 0/1, via both subtraction-of-powers-of-2 and division-by-2 methods.
- Re-traced the full quotient chain (50→25→12→6→3→1→0, or 22→11→5→2→1→0) explicitly to catch and fill in the skipped division step before reversing.
- Practiced on a **non-palindromic** example (decimal 22) specifically chosen to make the reversal step visibly matter, instead of relying on examples where skipping reversal wouldn't have been noticeable.
- Re-grouped the binary number correctly (groups read left-to-right, in the same order as the original number), and verified by independently converting the full binary number to decimal, then decimal to hex via division — confirming both methods agree (0x179).
- Adopted the habit of always doing a **reverse-conversion check** (multiply each digit by its place value and sum back to the original number) before finalizing any answer, going forward.

---

**Next Session:** Octal conversions, binary arithmetic (addition/subtraction), and signed number representations (sign-magnitude, 1's complement, 2's complement).
