---
title: "如何在 Powershell 上创建符号链接"
type: How
created-date: 2022-06-15T11:01:40.011+0800
tag: 
alias: 
  - "如何在 Powershell 上创建符号链接"
dg-publish: true
dg-permalink: "How/powershell-symlink"
share: true
category: "how"
---

# 如何在 Powershell 上创建符号链接

%%
> [!example]+ **Comments**    
> ```dataview
> TABLE 
>     WITHOUT ID
>     link(Source, dateformat(date(Source), "yyyy-MM-dd")) as Date___, 
>     regexreplace(rows.Comments,"^@@\[\[.+?\]\]\s","") as "Comments"
> FROM "journals"
> WHERE  contains(cmnt, this.file.name)
> FLATTEN cmnt as Comments
> WHERE contains(Comments, this.file.name)
> GROUP BY file.link as Source
> SORT rows.file.day desc
> ```
>  **Comments**:: 
%%

## 用 mklink 创建符号链接的局限性

在正常的情况下，Windows 上需要创建文件或者文件夹的符号链接，需要用 `mklink` 命令来创建。但是 `mklink` 不是一个单独的程序，而是 `cmd.exe` 内置的命令。所以当你使用 Powershell 的时候，并不存在所谓的 `mklink` 命令。

## 在 Powershell 上创建符号链接

首先，必须要进管理员权限的 Powershell 。

然后使用以下命令创建：

```powershell
New-Item -ItemType SymbolicLink -Path "Link" -Target "Target" #创建符号链接文件
New-Item -ItemType Junction -Path "Link" -Target "Target" #创建符号链接目录
```

# Reference

- **创建日期**:: [[2022-06-15]]
- **Source**:: [Create Symbolic Link in Windows 10 with PowerShell](https://winaero.com/create-symbolic-link-windows-10-powershell/)