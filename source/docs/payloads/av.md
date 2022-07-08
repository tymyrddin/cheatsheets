# Anti-Virus

Almost all AV applications employ multiple ways to block malware attacks. If one mechanism is bypassed, another may still block the malware. Some AV applications are designed to protect a single computer, others are specifically designed for servers or networks, but the underlying mechanisms of an AV remain mostly the same: It actively scans files that are introduced to a system, relying on a method to identify potentially hazardous files. This is called signature detection. And it attempts to identify suspicious behaviour on a system. This ranges from making suspicious registry entries, or adding items to a list that executes automatically on system startup. This approach is what helps protect against encrypted viruses, or viruses that are yet to be identified.

## Virus definitions

The programs rely upon signatures to detect new malware. Provided the company has already analysed and extracted a proper signature of the file that is kept in a database. Potential threats are compared to this database, and action is taken in case the signatures match.

## Heuristics

A heuristic detection allows a scanner to detect viruses even when they are padded with extra or meaningless code, using what are called wildcard characters. This detects a virus family, even by an inexact match to an existing signature. And it must not flag legitimate software as malware.

## Behavioural blocking

This is a signatureless approach to detection that helps the program build a full context around every process execution path in real time, and identify the stealthier, more advanced malware threats. Suspicious behavior includes unpacking of malicious code, modifying the host files, or observing keystrokes. Noticing actions like these allows an Anti-Virus program to detect previously unseen malware on a system.

## Sandbox detection

This is a behavioural-based detection technique that executes the programs in a virtual environment, as opposed to detecting its fingerprint at run time. Actions a potential malware performs are logged to determine whether the application is malicious or not. This technique is resource intensive and slow, and it is rarely used in AV designed to protect a single computer. 

## Data mining

Features of files are extracted from files, and then data mining and machine learning algorithms are used to classify the behaviour of a file and the likelihood it has malicious intent or not. This is used to detect the newest forms of malware in the wild.

## Types of scans

* On demand: A conventional scan is either run when the user requests it, or at a scheduled instance that the Anti-Virus sets up. This type of scan searches the contents of the disks, directories and files, as well as boot sectors and system components. 
* Real time: The system is monitored for any suspicious activity in real time, when data is loaded into the active memory.
* Smart: An Anti-Virus only scans selected files, that are more suspicious to be altered or infected.
* On startup: A quick scan of the boot sectors and critical system files, instead of a full disk scan that takes a long time to finish, to catch boot sector viruses.

