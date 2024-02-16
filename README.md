Passive ARP Scanner

The Passive ARP Scanner is a network tool designed to monitor and log ARP (Address Resolution Protocol) traffic on a network interface without sending any packets itself. It captures live ARP packets, identifies devices on the local network, and maintains a detailed log of observed IP and MAC addresses, including timestamps, count of appearances, associated organizations (via OUI lookup), and DNS names if available.
Features

    Passive Listening: Captures ARP packets without generating network traffic.
    Organization Identification: Utilizes OUI data to identify the manufacturer or organization associated with a MAC address.
    DNS Lookup: Optionally resolves IP addresses to DNS names for easier identification of network devices.
    Timestamps: Records first and last seen timestamps for each unique ARP response.
    Summary Logging: Periodically logs a summary of all ARP packets observed.
    Flexible Output: Supports logging to a file or standard output. Output is in JSON format.

Dependencies

    libpcap: A portable C/C++ library for network traffic capture.
    pthreads: For multithreading support.

Installation

Before you can use the Passive ARP Scanner, you must have libpcap installed on your system. Most Linux distributions come with libpcap pre-installed, or it can be easily added using the package manager. For example, on Ubuntu or Debian:

bash

sudo apt-get update
sudo apt-get install libpcap-dev

Compilation

Compile the Passive ARP Scanner with the following command:

bash

gcc -o passive_arp_scanner passive_arp_scanner.c -lpcap -lpthread

Usage

bash

sudo ./passive_arp_scanner [options] <network_interface>

Options:

    -h: Display this help message.
    --no-dns: Disable DNS lookups.
    --summary: Enable periodic summary logging.
    --unix-time: Log timestamps in UNIX timestamp format.
    -o <output_file>: Specify a file to log output instead of standard output.
    --oui-file <file>: Specify a custom OUI file location.

Example

bash

sudo ./passive_arp_scanner --summary --unix-time -o arp_log.txt eth0

This command listens on the eth0 interface, logs summaries periodically, uses UNIX timestamp format for timestamps, and writes the output to arp_log.txt.
Customizing the OUI File

The OUI file (oui.txt) is used for looking up organizations associated with MAC addresses. By default, the scanner looks for this file at /usr/share/ieee-data/oui.txt. You can specify a custom location using the --oui-file option.
Contributing

Contributions to the Passive ARP Scanner are welcome. Please send pull requests or report issues via the GitHub repository.
