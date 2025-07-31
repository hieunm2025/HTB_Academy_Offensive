# Wifi Password Cracking and WPA Security
- Wifi is essential for connecting devices to internet but can be vulnerable due to weak passwords and misconfigurations
- Wifi password cracking : attempt to retrieve passphrase or encryption key protecting the network
# Wifi Encryption Protocols
Recommend WPA3-Enterprise
# Password Cracking Strategy
Quality of the wordlist and the techniques applied
Common password patterns: user habits or factory defaults
# Wifi Cracking Techniques
- Tradional WPA Cracking Steps:
  1.Recon: Identifying nearby Wifi networks(tools like airodump-ng)
  2.Handshake Capture: Capturing the handshake by disconnecting a client(aireplay-ng)
  3.Password Cracking: Attempting to crack handshake using bruteforce (aircrack-ng,hashcat,cowpatty,john)
  4.Access Verification: If successful, test the cracked key by connecting to the network
- Advanced Cracking methods:
    - Wordlist Gen: Use default credentials or pattern specific to users to create effective wordlists
    - Mask-based & Rule-based Cracking: Focus on applying known structures or rules to the password
    - Combination and Hybrid Attack: use a mix of methods for higher success rates
    - CPU vs GPU