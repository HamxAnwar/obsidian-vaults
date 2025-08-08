- Usage
```
hashcat -m <hash_type> -a <attack_mode> hashfile wordlist
```
- Where:
	- `-m <hash_type>` specifies the hash-type in numeric format. For example, `-m 1000` is for NTLM. Check the official documentation (`man hashcat`) and [example page](https://hashcat.net/wiki/doku.php?id=example_hashes) to find the hash type code to use.
	- `-a <attack_mode>` specifies the attack-mode. For example, `-a 0` is for straight, i.e., trying one password from the wordlist after the other.
	- `hashfile` is the file containing the hash you want to crack.
	- `wordlist` is the security word list you want to use in your attack.