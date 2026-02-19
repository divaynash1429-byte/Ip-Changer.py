# Ip-Changer.py
This tool help you to change your current id address and mac address 
import subprocess

def chnage_mac(interface, new_mac):
	print(f"[*] changing MAC address for {interface} to{new_mac}")

#Using a list with subprocess.run is more secure then shell=True
	subprocess.run(["sudo", "ifconfig", interface, "down"])
	subprocess.run(["sudo", "ifconfig", interface, "hw", "ether", new_mac])
	subprocess.run(["sudo", "ifconfig", interface, "up"])

#Example usage:
#change_mac("eth0", "00:11:22:33:44:55")

import subprocess

def chnage_ip(interface, new_ip, subnet_mask="255.255.255.0"):
	print(f"[+] Changing IP address for {interface} to {new_ip}")

	#Assigning a static IP
	subprocess.run(["sudo", "ifconfig", interface, new_ip, "netmask", subnet_mask])
