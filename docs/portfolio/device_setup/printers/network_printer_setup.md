# Network Printer Setup
In the project we will configure a printer for network sharing.


## Setup
### Connect Printer to Network

First we must connect the printer to the network. In a corporate environment this usually done using an ethernet connection.

When using internet we connect it to the ethernet port on the printer and the wall. The ethernet port on the wall must be the port associated with the PRINTERS VLAN for the network.

![Ethernet Port Wall](./assets/images/ethernet_port_wall.png)

### Configure Static IP
Now we will assign a static IP to the printer. This ensures the IP address will remain the same in case the DHCP sever shuts down.

To configure the static go to your printers **Network Settings**, then **TCP/IP settings**, and finally the **IPv4 settings**.

![IPv4 Settings](./assets/images/ipv4_settings.png)

Here we will configure the IP address, subnet mask, default gateway, and DNS servers.

### Add Printer to Printer Server
Now we can add the printer to the Print Server. First we must ensure the **Print and Document Services** role is added to Server Manager.

![Print and Document Services](./assets/images/add_print_and_document_services_role_server.png)

After it installed we can now access the **Print Management** console in **Windows Administrative tools**.

Once we are here we add the printer using the static IP we assigned to the printer.

![Print Management Console](./assets/images/print_management_console.png)

### Add Network Printer to Client PC
On windows we go to:

```Settings > Bluetooth & Devices > Printers & Scanners > Add Device > Add a new device manually > Select a shared printer by name```

![Add Printer Client](./assets/images/add_printer_client.png)

Here we enter the network path of the printer we added to our print server.

## Troubleshooting
If we have trouble connecting to the printer from our client, these are some common troubleshootings steps.

### Power and Connection

If cannot connect to the printer, the first step we should take is make sure it is powered on.

If it is, then check if there is an ethernet connection from the printer to the correct VLAN port.

![Ethernet Port Printer](./assets/images/ethernet_port_printer.png)

### Use Printer Offline and Pause Printing
Sometimes when the printer powers off, reboots, or the network connection drops, the printers **Use Printer Offline** or **Pause Printing** setting is enabled.
This **stops** the client from sending print jobs to the printer.

To resolve this issue we select our printer in **Bluetooth & Devices** and disable this setting.

![Use printer offline](./assets/images/use_printer_offline_pause_printing.png)

### Ensure Printer Network Connection
Next we must ensure the printer is reachable on the network.

First we check the printer IP address by printing a network configuration page from the printer settings.

![Network Configuration Page](./assets/images/network_configuration_page.png)

Then we using ```ping``` using the appropriate IP address.

![Ping Printer](./assets/images/ping_printer.png)

### Enable File and Printer Sharing
If the printer is not reachable it may be because file and printer sharing is not enabled on the server.

To turn this on we go to the following control panel path:

```Control Panel\Network and Internet\Network and Sharing Center\Advanced sharing settings```

Then we turn on File and Printer sharing.

![Enable File and Printer Sharing](./assets/images/enable_file_and_printer_sharing_server.png)

### Restart Print Spooler
The print spooler is the service that manages print requests. Restarting it may resolve the issue.

To restart it we go to the services console:

```Win+R > services.msc```

![Services](./assets/images/services.png)

Then we navigate to Print Spooler:

```Right-click > Restart```

![Restart Print Spooler](./assets/images/restart_print_spooler.png)