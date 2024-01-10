# AHK

[官网文档](https://www.autoahk.com/help/autohotkey/zh-cn/docs/AutoHotkey.htm)

[知乎](https://zhuanlan.zhihu.com/p/360570752)

[中文乱码解决方案](https://zhuanlan.zhihu.com/p/472008013)

[常用技巧分享](https://zhuanlan.zhihu.com/p/103357456)

```autohotkey
; 该代码可以将剪贴版记录保存到文件
#Persistent
OnClipboardChange("ClipChanged")
return
ClipChanged(Type) {
FileAppend, %Clipboard%`n, C:\\clip_history.txt
}
```


```autohotkey
; 检测窗口存在后自动输入密码
DetectHiddenWindows, off
SetTitleMatchMode, 2
taget:="密码"
SetTimer, WatchWindows, 1000
return

WatchWindows:
	WinGet, active_id, ID, %taget%
	if(active_id = "")
	{
		ToolTip
	}
	else
	{
		Send 6186{enter}
	}
	return

#Persistent
ToolTip, 点=筛选`n减=拆分`n加=合并`n自动输密码6186
SetTimer, RemoveToolTip, -6000
return
RemoveToolTip:
ToolTip
return

; 筛选与取消筛选
NumpadDot::
Send {ctrl down}{Shift down}l{ctrl up}{Shift up}
return
```
