# How to Run diskman on TeraStation

This guide explains the basic workflow to run `diskman` on a TeraStation device.

### 1. Download Required Packages

Download binaries for your CPU architecture from:

- ACP Commander Go: [https://github.com/mitslabo/acp-commander-go/releases](https://github.com/mitslabo/acp-commander-go/releases)
- musl-builder: [https://github.com/mitslabo/musl-builder](https://github.com/mitslabo/musl-builder)
- diskman-web: [https://github.com/mitslabo/diskman-web/releases](https://github.com/mitslabo/diskman-web/releases)

### 2. Discover Your TeraStation

Use ACP Commander Go to find your TeraStation on the network.

Command:

```bash
acp-commander_XXXX -f
```

Example:

```bash
acp-commander_linux_amd64 -f
```

### 3. Upload ddrescue and diskman to TeraStation

Transfer executables to the target device.

Command:

```bash
acp-commander_XXXX -pw <admin_password> -t <terastation_ip> -x <local_file>=<remote_path>
```

Example:

```bash
acp-commander_linux_amd64 -pw password -t 192.168.11.111 -x diskman-web.amd64=/usr/local/bin/diskman
acp-commander_linux_amd64 -pw password -t 192.168.11.111 -x ddrescue.amd64=/usr/local/bin/ddrescue
```

### 4. Enable Telnet

Enable telnet access on your TeraStation.

Command:

```bash
acp-commander_XXXX -pw <admin_password> -t <terastation_ip> -o
```

Example:

```bash
acp-commander_linux_amd64 -pw password -t 192.168.11.111 -o
```

### 5. Connect and Grant Execute Permission

Connect via telnet, then set executable permissions.

Command:

```bash
telnet <terastation_ip>
chmod +x /usr/local/bin/diskman-web
chmod +x /usr/local/bin/ddrescue
```

### 6. Run diskman

Start diskman after login.

Command:

```bash
diskman-web --daemon
```

Example:

```bash
/usr/local/bin/diskman-web --daemon
```

### 7. Access via a web browser

Command:

```
http://<terastation_ip>:8080
```