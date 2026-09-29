# So sánh L với R

Chỉ số L/R là thứ tự box cao ≥ H=40 trong từng frame, theo thứ tự XML; bắt đầu từ 1.
Box L trong ignore_region được báo IGNORE_SCOPE, không tính SPURIOUS.

## adasind_014670.jpg
- L2 center SPURIOUS
- L5 center SPURIOUS
- L7+R5 mid WRONG_CLASS
## adasind_032280.jpg
- L2 edge SPURIOUS
- L5 mid SPURIOUS
## adasind_034080.jpg
- L2 mid SPURIOUS
- L6 center SPURIOUS
- L9 center SPURIOUS
- L11+R2 center BOX_GEOMETRY
- R9 center MISSING

## Theo zone
| zone | n_ref | matched | missing | spurious |
|---|---|---|---|---|
| center | 7 | 5 | 2 | 5 |
| mid | 11 | 10 | 1 | 3 |
| edge | 2 | 2 | 0 | 1 |
