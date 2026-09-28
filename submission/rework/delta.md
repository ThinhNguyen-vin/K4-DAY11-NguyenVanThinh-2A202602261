# Rework delta

| zone | matched before | matched after | missing before | missing after | spurious before | spurious after |
|---|---:|---:|---:|---:|---:|---:|
| center | 4 | 4 | 0 | 0 | 0 | 0 |
| mid | 9 | 9 | 0 | 0 | 0 | 0 |
| edge | 7 | 7 | 0 | 0 | 0 | 0 |

## Findings action=rework

Không có finding nào trong `findings.csv` có `action=rework`; các bất đồng được
phân loại là model-domain hoặc chưa đủ bằng chứng và giữ nguyên annotation.
Vì vậy bản rework v2 giữ nguyên hình học và số liệu trước/sau, không sửa nhãn
chỉ để làm giảm bất đồng với model.
