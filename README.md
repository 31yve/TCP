

# TCP - A Multi-threaded TCP Stress Testing Tool

`TCP` is a powerful, multi-threaded TCP stress testing tool written in C. It is designed to send a high volume of crafted TCP packets to a specified IP address and port, allowing network administrators and security professionals to test the resilience of their infrastructure under heavy load.

The tool operates at a low level by creating raw sockets, which allows it to manually construct and send custom IP and TCP headers.

## ✨ Features

   Multi-threaded: Utilizes POSIX threads (`pthreads`) to send packets from multiple threads concurrently, enabling high packet-per-second rates.
   Raw Socket Implementation: Crafts packets manually, bypassing the kernel's TCP/IP stack for greater control over the packet contents.
   Header Randomization: Populates TCP and IP header fields with randomized values (sequence numbers, source ports, etc.) to generate varied traffic.
   Custom Packet Logic: Alternates between sending TCP packets with `PSH/ACK` flags and `FIN/ACK` flags to simulate different types of traffic.
   Lightweight & Performant: Written in C for minimal overhead and high performance.

## ⚠️ Disclaimer & Warning

This tool is intended for educational and security testing purposes only. You should only use this tool to test networks and systems that you own or have explicit, written permission to test.

Unauthorized attacks on any network or server are illegal. The author and any contributors are not responsible for any damage or legal issues caused by the misuse of this software. Use it at your own risk and act responsibly.

## ⚙️ Compilation

This program is designed for Linux or other Unix-like systems. You will need a C compiler like `gcc` installed.

To compile the code, open your terminal and run the following command:

```bash
gcc -o tcp tcp.c -pthread
```

   `gcc`: The C compiler.
   `-o tcp`: Specifies the name of the output executable file.
   `tcp.c`: The name of your source code file.
   `-pthread`: Links the POSIX threads library, which is required for multi-threading.

## 🚀 Usage

Because this tool uses raw sockets, it requires root privileges to run. Use `sudo` to execute it.

### Command Format

```bash
sudo ./tcp <target_ip> <port> <threads> <time_seconds>
```

### Parameter Descriptions

   `<target_ip>`: The IP address of the server you want to test.
   `<port>`: The target port on the server.
   `<threads>`: The number of concurrent threads to use for the test.
   `<time_seconds>`: The duration of the test in seconds.

### Example Command

This command will start a test against the IP `192.168.1.100` on port `80`, using `8` threads for a duration of `120` seconds.

```bash
sudo ./tcp 192.168.1.100 80 8 120
```
