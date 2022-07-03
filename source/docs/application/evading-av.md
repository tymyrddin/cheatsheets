# Evading Anti-Virus

Whether delivering a payload through an application vulnerability exploit, or through social engineering, running code on target machines is part of most penetration tests. That means bypassing antivirus software or other host-based protections. 

Tools like Veil and MSFVenom may in the lab be good for learning everything around this in a lab context, but the most effective way to avoid antivirus detection on a target machine is to create customized backdoors.

* Don't develop for avoiding all. Include finding out what protections the target uses in reconnaisance.
* Keep it as simple as possible. Just enough to get in, disable antivirus, and then move in with more-featured tools.

Use Metasploit templates in the `data/templates/src` directory for DLLs, EXEs, and Windows Services. Find shell codes 
in https://www.exploit-db.com/shellcodes) to plug into the template, and compile.

Or use msfpayload or msfvenom from Metasploit to generate C shell code and plug that into the template
	
	$ ./msfpayload windows/shell_bind_tcp C
	
This generates C shell code to bind a shell to TCP port 4444. 

After compilation, check to see if the AV product running in the lab detects the bugger. If it gets detected start 
playing with segments and other formats, etcetera.

Or, [learn to write your own in python from scratch](https://github.com/tymyrddin/nirridit). Not that hard.