# autohotkey notes

https://www.autohotkey.com/#keyfeatures
https://www.autohotkey.com/download/

## instructions

build commands in a .txt file
save to specific folder



## AHK commands

using v1.1.33.09

::STRING::expanded


::STRING::
SendInput,
( Join+{Enter}
print
multi-line output
without sending
)
return


::STRING::
FormatTime, currentdate,, yyyy-MM-dd
sendinput %currentdate%-
return

-------------------

## my ahk script

```

#NoEnv  ; Recommended for performance and compatibility with future AutoHotkey releases.
; #Warn  ; Enable warnings to assist with detecting common errors.
SendMode Input  ; Recommended for new scripts due to its superior speed and reliability.
SetWorkingDir %A_ScriptDir%  ; Ensures a consistent starting directory.


::bbd::BBDIGITAL
return


::]ady::
SendInput,
( Join+{Enter}
address line1
address line2
address line3
)
return


::]d::
FormatTime, currentdate,, yyyy-MM-dd
sendinput %currentdate%-
return

F2::	;F2
^c	;copy
return

+F2::	;shift F2
^x	;cut
return

F4::	;F4
^v	;paste
return

```
