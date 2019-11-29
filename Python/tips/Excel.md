> 填充单员格
```python
import xlrd
import pandas as pd

f = r'‪C:\Users\frank\Desktop\jojo.xlsx'
# 判断sheet信息
wb = xlrd.open_workbook(f)
print(wb.sheet_names())

# 打开一个sheet
sheet1 = wb.sheet_by_name(wb.sheet_names[0])

# 获取合并单元格
merged_cells= sheet1.merged_cells

# pandas操作excel
import pandas as pd
df = pd.read_excel(io=wb, sheetname=sheet1.sheet_names()[0], engine='xlrd')

# 填充单元格
for (begin_row, end_row, begin_col, end_col) in sheet1.merged_cells:
    print(begin_row, end_row, begin_col)
    fill_value = df.iloc[begin_row-1, begin_col]
    df.iloc[begin_row:end_row-1, begin_col] = fill_value

# 写到excel
df.to_excel(r'F:\output.xlsx')
```
