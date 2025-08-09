tsb AND csv
Public Sub Create_UTF8_Both()
    Dim Wb As Workbook, ws As Worksheet
    Dim lastRow As Long, lastCol As Long
    Dim csvPath As String, tsvPath As String
    Dim ok As Boolean

    Set Wb = ActiveWorkbook
    Set ws = Wb.ActiveSheet

    If Wb.Path = "" Then
        MsgBox "Please save the workbook at least once before exporting.", vbExclamation, "Save Required"
        Exit Sub
    End If
    If WorksheetFunction.CountA(ws.Cells) = 0 Then
        MsgBox "The active sheet is empty. Nothing to export.", vbInformation, "Empty Sheet"
        Exit Sub
    End If

    Application.ScreenUpdating = False

    lastRow = ws.Cells.Find(What:="*", SearchOrder:=xlByRows, SearchDirection:=xlPrevious).Row
    lastCol = ws.Cells.Find(What:="*", SearchOrder:=xlByColumns, SearchDirection:=xlPrevious).Column

    csvPath = Wb.Path & "\" & Left(Wb.Name, InStrRev(Wb.Name, ".") - 1) & ".csv"
    tsvPath = Wb.Path & "\" & Left(Wb.Name, InStrRev(Wb.Name, ".") - 1) & ".tsv"

    ' Write CSV
    ok = ok Or WriteDelimitedUTF8(ws, lastRow, lastCol, ",", csvPath)

    ' Write TSV
    ok = ok Or WriteDelimitedUTF8(ws, lastRow, lastCol, vbTab, tsvPath)

    Application.ScreenUpdating = True

    If ok Then
        MsgBox "Exports created successfully:" & vbCrLf & vbCrLf & _
               "CSV: " & csvPath & vbCrLf & _
               "TSV: " & tsvPath, _
               vbInformation, "Export Complete"
    End If
End Sub

Private Function WriteDelimitedUTF8(ws As Worksheet, lastRow As Long, lastCol As Long, _
                                    delim As String, outPath As String) As Boolean
    Dim fileStream As Object
    Dim r As Long, c As Long
    Dim cellValue As String, fullRow As String

    On Error GoTo FailSafe

    Set fileStream = CreateObject("ADODB.Stream")
    fileStream.Type = 2                 ' adTypeText
    fileStream.Charset = "utf-8"
    fileStream.Open

    For r = 1 To lastRow
        fullRow = ""
        For c = 1 To lastCol
            cellValue = ws.Cells(r, c).Text
            If InStr(1, cellValue, delim, vbBinaryCompare) > 0 _
               Or InStr(1, cellValue, """", vbBinaryCompare) > 0 _
               Or InStr(1, cellValue, vbLf, vbBinaryCompare) > 0 _
               Or InStr(1, cellValue, vbCr, vbBinaryCompare) > 0 Then
                cellValue = """" & Replace(cellValue, """", """""") & """"
            End If
            fullRow = fullRow & cellValue
            If c < lastCol Then fullRow = fullRow & delim
        Next c
        fileStream.WriteText fullRow, 1  ' adWriteLine
    Next r

    fileStream.SaveToFile outPath, 2     ' adSaveCreateOverWrite
    WriteDelimitedUTF8 = True

FailSafe:
    On Error Resume Next
    If Not fileStream Is Nothing Then fileStream.Close
    Set fileStream = Nothing
End Function











----------------------------------------

# tsv or csv

'======================================================================
'
'  UTF-8 delimited exports (CSV + TSV) for the active sheet.
'  Macros: Create_UTF8_CSV, Create_UTF8_TSV, Create_UTF8_Both (one-click)
'
'======================================================================

Private Sub ExportActiveSheetUTF8(delim As String, ext As String, _
                                  Optional showMsg As Boolean = True, _
                                  Optional ByRef outPathResult As String)

    Dim Wb As Workbook
    Dim ws As Worksheet
    Dim outPath As String
    Dim fileStream As Object
    Dim lastRow As Long, lastCol As Long
    Dim r As Long, c As Long
    Dim cellValue As String
    Dim fullRow As String

    Set Wb = ActiveWorkbook
    Set ws = Wb.ActiveSheet

    If Wb.Path = "" Then
        MsgBox "Please save the workbook at least once before exporting.", vbExclamation, "Save Required"
        Exit Sub
    End If

    Application.ScreenUpdating = False

    ' Build output path with requested extension (".csv" or ".tsv")
    outPath = Wb.Path & "\" & Left(Wb.Name, InStrRev(Wb.Name, ".") - 1) & ext
    outPathResult = outPath

    ' Find used area
    If WorksheetFunction.CountA(ws.Cells) = 0 Then
        MsgBox "The active sheet is empty. Nothing to export.", vbInformation, "Empty Sheet"
        GoTo Cleanup
    End If

    lastRow = ws.Cells.Find(What:="*", SearchOrder:=xlByRows, SearchDirection:=xlPrevious).Row
    lastCol = ws.Cells.Find(What:="*", SearchOrder:=xlByColumns, SearchDirection:=xlPrevious).Column

    ' Create UTF-8 stream
    Set fileStream = CreateObject("ADODB.Stream")
    fileStream.Type = 2             ' adTypeText
    fileStream.Charset = "utf-8"
    fileStream.Open

    ' Write rows
    For r = 1 To lastRow
        fullRow = ""
        For c = 1 To lastCol
            cellValue = ws.Cells(r, c).Text

            ' Quote if we see the delimiter, a quote, or a line break
            If InStr(1, cellValue, delim, vbBinaryCompare) > 0 _
               Or InStr(1, cellValue, """", vbBinaryCompare) > 0 _
               Or InStr(1, cellValue, vbLf, vbBinaryCompare) > 0 _
               Or InStr(1, cellValue, vbCr, vbBinaryCompare) > 0 Then
                cellValue = """" & Replace(cellValue, """", """""") & """"
            End If

            fullRow = fullRow & cellValue
            If c < lastCol Then fullRow = fullRow & delim
        Next c

        fileStream.WriteText fullRow, 1 ' adWriteLine (adds CRLF)
    Next r

    ' Save and optionally notify
    fileStream.SaveToFile outPath, 2 ' adSaveCreateOverWrite
    If showMsg Then
        MsgBox "UTF-8 " & UCase(Replace(ext, ".", "")) & " created successfully!" & vbCrLf & vbCrLf & outPath, _
               vbInformation, "Export Complete"
    End If

Cleanup:
    On Error Resume Next
    If Not fileStream Is Nothing Then fileStream.Close
    Set fileStream = Nothing
    Application.ScreenUpdating = True
End Sub

' --- Public wrappers you can run individually ---
Public Sub Create_UTF8_CSV()
    ExportActiveSheetUTF8 ",", ".csv", True
End Sub

Public Sub Create_UTF8_TSV()
    ExportActiveSheetUTF8 vbTab, ".tsv", True
End Sub

' --- One-click: create BOTH CSV and TSV, single confirmation ---
Public Sub Create_UTF8_Both()
    Dim csvPath As String, tsvPath As String

    ' Suppress individual popups; show one combined message at the end.
    ExportActiveSheetUTF8 ",", ".csv", False, csvPath
    ExportActiveSheetUTF8 vbTab, ".tsv", False, tsvPath

    If Len(csvPath) > 0 Or Len(tsvPath) > 0 Then
        MsgBox "Exports created successfully:" & vbCrLf & vbCrLf & _
               IIf(Len(csvPath) > 0, "CSV: " & csvPath & vbCrLf, "") & _
               IIf(Len(tsvPath) > 0, "TSV: " & tsvPath & vbCrLf, ""), _
               vbInformation, "Export Complete"
    End If
End Sub
