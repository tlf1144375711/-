# VBA
 在Excel中查找文本字符串中第一个数字的位置

>= MIN(SEARCH({0,1,2,3,4,5,6,7,8,9},A2&"0123456789"))

```
; vba删除密码
Sub DeletePW()
    ActiveSheet.Protect DrawingObjects:=True, Contents:=True, AllowFiltering:=True
    ActiveSheet.Protect DrawingObjects:=False, Contents:=True, AllowFiltering:=True
    ActiveSheet.Protect DrawingObjects:=True, Contents:=True, AllowFiltering:=True
    ActiveSheet.Protect DrawingObjects:=False, Contents:=True, AllowFiltering:=True
    ActiveSheet.Unprotect
End Sub
```

## 运用替换功能删除换行符。
1. 找到一个含有手工换行符的单元格，并记住换行符所在位置。

2. 按下Ctrl+C组合键复制此单元格。

3. 按Ctrl+H组合键调出替换对话框。

4. 在“查找内容”文本框内按Ctrl+V组合键将刚才复制的内容粘贴下来。

5. 将光标定位到“查找内容”文本框开头，按DEL键删除换行符前的内容，将光标定位到“查找内容”文本框末尾，按BackSpace(退格)键删除换行符后面的内容。

>注意：换行符看不到，要根据前面记下的换行符位置来操作。

6. 将“替换为”对话框中的内容删除――如有，根据需要按下“查找下一个”、“替换”或“全部替换”按钮，就可将手工换行符删除。

>这种方法将删除手工换行符，而对单元格格式中设置的自动换行没有任何影响。

```
;vba聚光灯
Private Sub Workbook_SheetSelectionChange(ByVal Sh As Object, ByVal Target As Range)
Cells.Interior.Pattern = 0
Target.EntireColumn.Interior.Pattern = xlChecker
Target.EntireColumn.Interior.PatternColor = 49407
Target.EntireRow.Interior.Pattern = xlChecker
Target.EntireRow.Interior.PatternColor = 49407
End Sub
```