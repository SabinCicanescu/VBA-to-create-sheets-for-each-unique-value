Sub createNewSheet()
Application.ScreenUpdating = False
Dim x As Range
Dim rng As Range
Dim last As Long
Dim sht As String

'specify sheet name in which the data is stored
sht = "Data Export"

'change filter column & range in the following code
last = Sheets(sht).Cells(Rows.Count, "I").End(xlUp).Row
Set rng = Sheets(sht).Range("A1:K" & last)

Sheets(sht).Range("I1:I" & last).AdvancedFilter Action:=xlFilterCopy, CopyToRange:=Range("AA1"), Unique:=True

For Each x In Range([AA2], Cells(Rows.Count, "AA").End(xlUp))
With rng
.AutoFilter
.AutoFilter Field:=9, Criteria1:=x.Value
.SpecialCells(xlCellTypeVisible).Copy

Sheets.Add(After:=Sheets(Sheets.Count)).Name = x.Value
ActiveSheet.Paste
End With
Next x

' Turn off filter
Sheets(sht).AutoFilterMode = False

With Application
.CutCopyMode = False
.ScreenUpdating = True
End With

End Sub
