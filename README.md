**SSH honeypot** designed to mimic a fully functional SSH server, deceiving malicious actors into interacting with a controlled environment. It captures valuable data about unauthorized access attempts and command executions, providing actionable insights into potential attack patterns.

## **Features**

- **Log SSH connection attempts**: Captures IP addresses, usernames, and passwords used in authentication attempts.
- **Interactive shell simulation**: Provides a realistic shell environment to interact with attackers.
- **Command logging**: Logs all commands executed by the attacker.
- **Customizable authentication**: Allows setting a custom username and password for authentication.
- **Rotating log files**: Logs are stored in rotating files to prevent excessive disk usage.
- **Configurable CLI**: Easily set IP addresses, ports, and credentials.
- **Secure by Default**: Automatically generates server keys for encrypted communication. 

## **Installation**

1. **Clone this repository**:  
   ```bash
   git clone https://github.com/rihadroshan/ssh-honeypot.git

   cd ssh-honeypot
   ```
2. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
   
## **Basic Usage**

By default, the honeypot will use the username `root`, no password, and bind to the machine's default IP address.

```bash
python3 server.py -p <port>
```

## Usage with Custom Authentication

You can specify a custom username and password for authentication. The `-a` (or `--address`) argument is optional and defaults to the machine's IP address if not provided.

```bash
python3 server.py -p <port> -u <username> -d <password>
```

To bind to a specific IP address, use the `-a` argument:

```bash
python3 server.py -a <IP address> -p <port> -u <username> -d <password>
```

## Examples

### Basic Usage
```bash
python3 server.py -p 2222

sudo python3 server.py -p 22
```

### Usage with Custom Authentication
```bash
python3 server.py -p 2222 -u ubuntu -d pass

sudo python3 server.py -p 22 -u ubuntu -d pass
```

## Logs

The honeypot logs activities in three rotating log files:

1. **`ssh_sys.log`**: General log file for server activities.
2. **`command_log.log`**: Logs all commands executed by the attacker.
3. **`auth.log`**: Logs authentication attempts, including usernames and passwords.

Log files are rotated when they reach 2000 bytes, with up to 5 backup files retained.

## Contributions & Reporting Issues:

Contributions of new features, improvements, or bug fixes are always welcome!

Feel free to open a pull request or open an issue.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Disclaimer

Use it responsibly and only on networks you own or have permission to test. The authors are not responsible for any misuse or damage caused by this tool.

## Files in the Repository

- **`server.py`**: The main Python script for the SSH honeypot.
- **`README.md`**: This readme file providing an overview and usage instructions.
- **`LICENSE`**:  The license file (`LICENSE`) contains the legal terms under which the SSH honeypot project is distributed and used.
