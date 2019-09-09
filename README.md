# Hexa Payload Decoder 

![Arcane|Transmutation](https://i.imgur.com/hbsbZnt.png)

### Issue
When analyzing malware traffic on the network sometimes we find ourselves spending several minutes decoding the data from the hexadecimal streams. In the best of the scenarios we can use some tools (like Wireshark) to see this hexadecimal streams already decoded, but sometimes the decoded characters are not supported by most of the networking analyzers.

### The Solution
The idea is to develope an unified tool aimed to extract the TCP hexadecimal data from flows filtering by some user provided specific port, decode it with powerfull decoding techniques and translate it from any language to english.

The workflow of the tool is the following:
  - User runs the bash script with two parameters, the pcap file to analyze and some port.
  - The bash script extracts the hexadecimal data from the TCP flows filtering by the user provided port using Tshark command.
  - The extracted hexadecimal data is passed to CyberChef decoder which uses multiple decoding techniques to get the raw data in the language it had been written.
  - The decoded data is finally passed to Google Translate python library which automatically detects the language and translate it to english.
  - The decoded and translated data is written to an output file to see the results.
  - This flow repeats for every TCP flow found in the pcap.

> NOTE: The bash script need to be ran with root priveleges because it need to write in /var/log to create the results file. 

---

Here is the script working with some example pcap:

![Imgur](https://i.imgur.com/HI5xseO.png)

---

### References:

- CyberChef Decoder https://gchq.github.io/CyberChef/.
- Google Translaty Python Library https://py-googletrans.readthedocs.io/en/latest/.

