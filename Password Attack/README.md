# Cracking protected Archives
ZIp files 
Many file extensions: tar,gz,rar,zip,bitlocker,deb...
tar files commonly encrypted using openssl or gpg

**Cracking ZIP file**

Zip format is heavily used in Windows env.
zip2john ZIP.zip > zip hash
cat zip.hash
One we have a hash, we use JtR to crack with desired passsword list
john --wordlist=rockyou.txt zip.hash
john zip.hash -show

**Cracking openSSL encrypte GZIP file**s
 file command to determine the actual format of file
 Crack OpenSSL encrypted files, may encounter various challenges, including numerous false positives or complete failure to identify correct password.

 Use the openssl tool within a for loop that attempts to extract the contents directly
 
 for i in $(cat rockyou.txt);do openssl enc -aes-256-cbc -d -in GZIP.gzip -k $i 2>/dev/null| tar xz;done

**Cracking Bitlocker-encrypted drives**
Bitlocker is a full-disk encryption feature developed by Microsoft for Window operating system. Since Windows Vista, it uses the AES encryption algorithm with either 128 bit or 256 bit lengths. If the password or PIN used for Bitlocker is forgotten, decryption can still be performed using a recovery key - a 48 digit string generated during the set up progress.

In enterpirse environments, virtual drives are sometimes used to store personal information, documents, or notes on company-issued devices to prevent unauthorized access. To crack a Bitlocker encrypted drive, we can use a script called bitlocker2john to four different hashes: the first two correspond to the Bitlocker password, while the latter two represent the recovery key. Because the recovery key is very long and randomly gen, it is generally not practical to guess - unless parital knowledge is availabale. We focus on cracking the password using the first hash($bitlocker$0$...)

bitlocker2john -i Backup.vhd > backup.hashes
grep "bitlocker\$0" backup.hashes > backup.hash
cat backup.hash

Once a hash is generated, either John or hashcat to crack it.
hashcat -a 0 -m 22100 hash
After successfully cracking the password, we can access the encrypted drive

**Mounting Bitlokcer-encrypted drives in Windows**

The easiest method for mounting a BitLocker-encrypted virtual drive on Windows is to double-click the .vhd file. Since it is encrypted, Windows will initially show an error. After mounting, simply double click the Bitlock volume to be prompted for the password.

![alt text](image.png)

**Mouting Bitlocker-encrypted drives in Linux(or macOS)**
It is also possible to mount BitLocker-encrypted drives in Linux. To do this, we can use tool called dislocker. 

sudo apt-get install dislocker
sudo mkdir -p /media/bitlocker
sudo mkdir -p /media/bitlockermount

//use losetup to configure the VHD as loop device
sudo losetup -f -P Backup.vhd
sudo dislocker /dev/loop02p2 -u1234qwer -- /media/bitlocker
sudo mount -o loop /media/bitlocker/dislocker-file /media/bitlockermount

If every thing was done correctly, now browse the files

cd /media/bitlockermount/
ls -la

Unmount it using `umount` command

# Practice(Cracking Protected Archives)
1.
bitlocker2john -i Private.vhd > all.hashes
grep "bitlocker\$0" all.hashes > vhd.hash
cat vhd.hash
![alt text](image-1.png)
john --wordlist=/path/to/rockyou.txt vhd.hash
hashcat -a 0 -m 22100 vhd.hash /path/to/rockyou.txt

d/a: francisco

2.Mount the BitLocker-encrypted VHD and enter the contents of flag.txt as your answer.
sudo losetup -f -P Private.vhd
losetup -a
`/dev/loop0: []: (/home/htb-ac-1453865/Private.vhd)`
sudo mkdir -p /mnt/bitlocker /mnt/bitlockermount
sudo dislocker /dev/loop0p1 -ufrancisco -- /mnt/bitlocker
sudo mount -o loop /mnt/bitlocker/dislocker-file /mnt/bitlockermount
d/a: `43d95aeed3114a53ac66f01265f9b7af`