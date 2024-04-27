# systemd Units and Services

## 1. Unit

In systemd, a "unit" is the basic building block that represents a system resource. There are various types of units, such as services, sockets, and mounts.

## 2. Service

A "service" is a type of unit in systemd that represents a system service or a background process. The configuration for a service unit includes information such as the command to start the service, dependencies, restart behavior, and more.

### Task10.service

Our `Task10.service` is an example service unit. It specifies that the service should run after the graphical.target, meaning it will start after graphical user interfaces are available. The service runs the `/home/rania/Task10.sh` script and restarts the script if it exits.
![Your Image Alt Text](https://private-user-images.githubusercontent.com/101398177/304699158-5734d11e-a167-4f00-a77f-bdfe530005fd.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDc5MDY0MjMsIm5iZiI6MTcwNzkwNjEyMywicGF0aCI6Ii8xMDEzOTgxNzcvMzA0Njk5MTU4LTU3MzRkMTFlLWExNjctNGYwMC1hNzdmLWJkZmU1MzAwMDVmZC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwMjE0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDIxNFQxMDIyMDNaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0zNDJiM2RiOGM1ZDJiMGRhMWQ2ODFmZTg5MjZkMDE1ZDFkNTgxYmQ3NmM2ZDhmYzg3NjdmNjhkNmZlYTUxZWFmJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.xbpvPps8sr8foQfj0Maq79rYCMHtIXQ9twNzZfdV6Wg)


![Your Image Alt Text](https://private-user-images.githubusercontent.com/101398177/304699195-aa6b84a5-2987-492a-8e3a-658cc608baf3.jpeg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDc5MDY0MjMsIm5iZiI6MTcwNzkwNjEyMywicGF0aCI6Ii8xMDEzOTgxNzcvMzA0Njk5MTk1LWFhNmI4NGE1LTI5ODctNDkyYS04ZTNhLTY1OGNjNjA4YmFmMy5qcGVnP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MDIxNCUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDAyMTRUMTAyMjAzWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9ZTJmN2YyOTVkNTA2MjMwMmU5ZTg0MzdmMzhkZDk1NDJjNDk0MDY4NTFiMWY1MDZlZjQ2Y2JmMWQwYzIzMWJmZiZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmYWN0b3JfaWQ9MCZrZXlfaWQ9MCZyZXBvX2lkPTAifQ.VqzK4257thEpAlROHYUlP0Np_vJIWarXaMHe9EPNvQY)
)

### Service Commands

To manage systemd services, you can use the following commands:

1. **Reload systemd Configuration:**
   ```bash
   sudo systemctl daemon-reload


and then plays these commands :

1. **sudo systemctl daemon-reload**

this command reloads the systemd manager configuration. When you make changes to systemd service unit files (such as adding, modifying, or removing a service file), you need to inform systemd to reload its configuration to pick up the changes.

2. **sudo systemctl start Task10.service**
You can use this command when you want to manually start a service. It's particularly useful if the service is not set to start automatically at boot time or if you want to ensure that the service is running.

3.**sudo systemctl status Task10.service**

![status ](https://private-user-images.githubusercontent.com/101398177/304699189-d0176e35-3a42-4a9d-ba6d-ec79ad8437df.jpeg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDc5MDYyODksIm5iZiI6MTcwNzkwNTk4OSwicGF0aCI6Ii8xMDEzOTgxNzcvMzA0Njk5MTg5LWQwMTc2ZTM1LTNhNDItNGE5ZC1iYTZkLWVjNzlhZDg0MzdkZi5qcGVnP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MDIxNCUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDAyMTRUMTAxOTQ5WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9MzY3OWQ3N2VkMzUzZThkZmEzYTIwYzNjYWU1MzE5NWIxOWU0ZGNlMDljYWYyZGYxMDJkNTBjODBlNzJhYjcwNCZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmYWN0b3JfaWQ9MCZrZXlfaWQ9MCZyZXBvX2lkPTAifQ.2Q2GscwS4JuEVNkrgKCA3_cfHfbI2ee75P-u7nxBhqs)


