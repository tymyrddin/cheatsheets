# Evading Anti-Virus

Whether delivering a payload through an application vulnerability exploit, or through social engineering, running code 
on target machines is part of most penetration testing. That means bypassing antivirus software or other host-based 
protections. 

Tools like Veil and MSFVenom may be useful for learning purposes in a lab context, but the most effective way to avoid 
antivirus detection on a target machine in a real-life organisational context is to create customised payloads or 
develop your own from scratch based on context of the pentesting/red teaming..

## Customised payloads

For customisation, use Metasploit templates in the `data/templates/src` directory for DLLs, EXEs, and Windows Services.
Plug in [exploit-db shellcodes](https://www.exploit-db.com/shellcodes) into the template. Or use `msfpayload` or 
`msfvenom` from Metasploit to generate C shell code to bind a shell to TCP port 4444 and plug that into the template:
	
	$ ./msfpayload windows/shell_bind_tcp C

After compilation, check to see if the AV products running in the lab detect the bugger. If it gets detected start 
playing with segments and other formats, etcetera.

## Payloads from scratch

Note that creating a new payload or shellcode that creates a new signature that is not present in the antivirus tools 
database can still be effective but falls short on the new solutions that base their detection on heuristics 
and behavioural analysis.

[Learn to write your own payloads in python from scratch](https://github.com/tymyrddin/nirridit). 

* Don't develop for avoiding all. Include finding out what protections the target uses in reconnaisance.
* Keep it as simple as possible. 
* Perhaps just enough to get in, disable antivirus, and then move in with more-featured tools?

> “The important thing is not to shout at this point, Vimes told himself. Do not…what do they call it…go postal? 
> Treat this as a learning exercise. Find out why the world is not as you thought it was. Assemble the facts, digest 
> the information, consider the implications. THEN go postal. But with precision.” ― Terry Pratchett, Thud! 