


**Booting from TFTP server...**

We are trying to boot from another server to save memory by avoiding the need for "Zimage," "hw.dtb," and other files on our SD card. We will use the TFTP protocol.

**Installing TFTP server...**

1. **Become root:**
    ```bash
    sudo su
    ```

2. **Install tftpd-hpa:**
    ```bash
    sudo apt-get install tftpd-hpa
    ```

3. **Edit tftpd-hpa configuration file:**
    ```bash
    nano /etc/default/tftpd-hpa
    ```
    Add `--create` to the `TFTP_OPTIONS` line to enable uploads to the TFTP server.

4. **Change working directory owner:**
    ```bash
    chown tftp:tftp /srv/tftp
    ls -l /srv
    ```

5. **Restart tftpd-hpa service and verify its status:**
    ```bash
    systemctl restart tftpd-hpa
    systemctl status tftpd-hpa
    ```

6. **Create the files you want to send from the server (e.g., HWinterface.dtb and Zimage).**

7. **Change the owner of these files to tftp:tftp:**
    ```bash
    chown tftp:tftp HWinterface.dtb Zimage
    ```

![Screenshot from 2024-01-20 19-02-47](https://github.com/RanianMustafa17/EmbeddedLinux/assets/101398177/254e3f0f-44b6-48de-8875-b3ff398b1a3a)

**Writing the QEMU script for interfacing...**

1. **Find your wireless interface IP:**
    ```bash
    rania@raniamustafa:/srv/tftp$ ip addr
    ```

    Note the IP address, e.g., `192.168.1.2/24`.

2. **Write the script and name the file `qemu-ifup`:**
    ```bash
    #!/bin/sh
    ip a add 192.168.1.2 dev $1
    ip link set $1 up
    ```

3. **Run QEMU with the following command:**
    ```bash
    sudo qemu-system-arm -M vexpress-a9 -m 128M -nographic -kernel u-boot -sd sd.img -net tap,script=./qemu-ifup -net nic
    ```

4. **In U-Boot, set the server and IP addresses:**
    ```bash
    ITI_44=> setenv serverip 192.168.1.2
    ITI_44=> setenv ipaddr 192.168.1.4
    ITI_44=> saveenv
    ```

5. **Load files from the TFTP server:**
    ```bash
    tftp 0x60000000 Zimage
    tftp 0x60010000 HWinterface.dtp
    ```

6. **Display memory contents:**
    ```bash
    md 0x60000000
    md 0x60010000
    ```
![WhatsApp Image 2024-01-20 at 5 30 17 PM](https://github.com/RanianMustafa17/EmbeddedLinux/assets/101398177/7a824490-7d6c-46f2-b597-5fe1bb945508)

![WhatsApp Image 2024-01-20 at 5 30 18 PM](https://github.com/RanianMustafa17/EmbeddedLinux/assets/101398177/2097930d-dfdb-4598-9e81-2716afa1fdaf)


