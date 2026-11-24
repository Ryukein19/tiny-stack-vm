# Tiny Stack VM — notes

## Practice set (kit, 40)
- **40/40 exact, 40,000/40,000 points, score 1,000,000/1,000,000.**
- Byte-identical to the reference VM (vm.mjs) on all 40; deterministic.
- Official kit grade-local: score 1,000,000, passed=1, L1 regrade byte-identical.
- Runtime ~0.36 s for the whole set (wall 60 s).
- All 14 edge cases pass: return-empty (8), bad-opcode (5), unsigned, mul-wrap,
  signed-division, truncated-immediate (9), memory-store (6), divide-by-zero (4),
  output-limit (11, 65,536 B), shifts, stack-overflow (3).

## Generalisation (fresh sets, kit generator)
- 10 fresh sets (400 new instances): **all 40/40, all 1,000,000.**
- Edge kinds covered: stack-underflow, call-depth, jump-outside, fall-off-end,
  input-end, sign-extension, memory-load, step-limit, plus all of the above.

## House baseline (plain-vm 1.0.0)
- Practice: 20/40, 26,800 points, score **670,000**. Exits 1 on every trap,
  no STORE trap, wrong unsigned ops and MUL, crashes on some programs.
- This entry beats it by 330,000 points.

## Size
- main.ts 5,169 B; total under the 8,192 B repo cap.
