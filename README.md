## stagefright_exploit.py

Python script to generate a malicious MP4 file exploiting the 'stsc' vulnerability (CVE-2015-1538) (#1),
and start reverse TCP listener on attacker machine.  

### author: vvn (eudemonics)  
### built upon original exploit code from @jduck

####**usage:**  
./stagefright.py [-h] [-c CBHOST] [-p CBPORT] [-s SPRAY_ADDR] [-r ROP_PIVOT]
              [-o OUTPUT_FILE]  

####**optional arguments:**  
    -h, --help: show help message and exit  
    -c CBHOST, --connectback-host CBHOST: host address to listen for incoming TCP connection from victim (default is whatever ifconfig tells it)  
    -p CBPORT, --connectback-port CBPORT: port for reverse TCP listener (default is 54321)  
    -s SPRAY_ADDR, --spray-address SPRAY_ADDR: address for heap spray entry  
    -r ROP_PIVOT, --rop-pivot ROP_PIVOT: stack pivot  
    -o OUTPUT_FILE, --output-file OUTPUT_FILE: generated MP4 file  

Original README:

    Included is a python script that generates an MP4 exploiting the ‘stsc’ vulnerability otherwise known as CVE-2015-1538 (#1). This is one of the most critical vulnerabilities I reported in the Stagefright library. The expected result of the exploit is a reverse shell as the media user. As detailed in my Black Hat and DEF CON presentations, this user also has access to quite a few groups such as inet, audio, camera, and mediadrm. These groups allow an attacker to take pictures or listen to the microphone remotely without exploiting additional vulnerabilities.

    This exploit has several caveats. First, it is not a generic exploit. It's only been tested to work on a single device model. My target was the Galaxy Nexus device running Android 4.0.4 containing only a partial implementation of ASLR. Also, due to variances in heap layout, this is not a 100% reliable exploit by itself. However, I was able achieve 100% reliability when delivered through an attack vector that allowed multiple attempts. Finally, this vulnerability was one of several that was neutered by GCC 5.0’s ‘new[]’ integer overflow mitigation present on Android 5.0 and later.

    Enjoy! Please consider contributing to Android security through research!
