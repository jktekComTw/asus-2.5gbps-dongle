1. clone Linus's linux source code from github and checkout branch of 6.8.12
2. put in the same level folder of the folder of this repo.
3. make Makefile&insmod the output ko file for PVE.
4. load the rule into /etc/udev.
5. then plug in the dongle into server of pve of 6.8.12 reversion.



==================below is old readme===========================================

- If you want to support S5 WOL, you have to find

	EXTRA_CFLAGS += -DRTL8152_S5_WOL

  in the Makefile. Then, remove the first character '#", if it exists.


- For Fedora, you may have to run the following command after installing the
  driver.

	# dracut -f

- For Ubuntu, you may have to run the following command after installing the
  driver.

	# sudo depmod -a
	# sudo update-initramfs -u

- Example of setting speed

	2.5G before kernel v4.10
	# ethtool -s eth0 autoneg on advertise 0x802f

	2.5G for kernel v4.10 and later
	# ethtool -s eth0 autoneg on advertise 0x80000000002f

	# ethtool -s eth0 autoneg on advertise 0x002f (1G)
	# ethtool -s eth0 autoneg on advertise 0x000f (100M full)
	# ethtool -s eth0 autoneg on advertise 0x0003 (10M full)

- Disable center tap short

	# make CONFIG_CTAP_SHORT=OFF modules

- Ring parameter

	Show Ring parameter
	# ethtool -g eth0

	Changes the number of ring entries for the Rx ring.
	# ethtool -G eth0 rx 100
