# 🔐 Terminal Commands for Web Analysis

[![en](https://img.shields.io/badge/lang-en-red.svg)](https://github.com/Ryuzakxx/ctf-web-toolkit/blob/main/README.md)
[![it](https://img.shields.io/badge/lang-it-green.svg)](https://github.com/Ryuzakxx/ctf-web-toolkit/blob/main/README_IT)

> 🎯 Complete guide for CTF and Penetration Testing on Kali Linux

[![Kali Linux](https://img.shields.io/badge/Kali-Linux-blue?logo=kalilinux)](https://www.kali.org/)
[![CTF](https://img.shields.io/badge/CTF-Ready-green)](https://ctftime.org/)
[![Security](https://img.shields.io/badge/Security-Tools-red)](https://github.com)

---

## 📋 Table of Contents

- [🌐 HTTP Header Analysis](#-http-header-analysis)
- [🔍 HTTP Methods (Verbs)](#-http-methods-verbs)
- [📤 Sending POST Requests and Forms](#-sending-post-requests-and-forms)
- [🚀 Advanced HTTP Requests](#-advanced-http-requests)
- [🌍 General Web Scanning](#-general-web-scanning)
- [🔌 Port and Service Scanning](#-port-and-service-scanning)
- [🌐 DNS Analysis](#-dns-analysis)
- [📂 Directory and File Scanning](#-directory-and-file-scanning)
- [📡 WHOIS and Traceroute Information](#-whois-and-traceroute-information)
- [🛠️ Specialized Tools](#️-specialized-tools)
- [💡 Useful Tips](#-useful-tips)

---

## 🌐 HTTP Header Analysis

### HEAD request (headers only)
```bash
curl -I http://example.com
```

### GET request with visible headers
```bash
curl -i http://example.com
```

### Headers with detailed output
```bash
curl -v http://example.com
```

### Follow redirects
```bash
curl -L -I http://example.com
```

---

## 🔍 HTTP Methods (Verbs)

> 💡 **CTF Tip**: Always use OPTIONS to discover supported methods, then try "hidden" ones too!

### Discover supported methods (OPTIONS)
```bash
curl -X OPTIONS http://example.com/ -i
```

### GET - Retrieve resource
```bash
curl -X GET http://example.com/
```

### HEAD - Headers only (no body)
```bash
curl -X HEAD http://example.com/ -i
# or
curl -I http://example.com/
```

### POST - Send data
```bash
curl -X POST http://example.com/ -d "data"
```

### PUT - Replace entire resource
```bash
curl -X PUT http://example.com/resource -d "data"
```

### PATCH - Partial modification
```bash
curl -X PATCH http://example.com/resource -d "data"
```

### DELETE - Remove resource
```bash
curl -X DELETE http://example.com/resource
```

### TRACE - Path debugging
```bash
curl -X TRACE http://example.com/
```

### CONNECT - TCP/IP tunnel
```bash
curl -X CONNECT http://example.com/
```

### OPTIONS verbose (ideal for CTF)
```bash
curl -v -X OPTIONS http://example.com/
```

---

## 📤 Sending POST Requests and Forms

### POST with form data (URL-encoded)
```bash
curl -X POST http://example.com/login -d "username=admin&password=admin"
```

### POST with explicit Content-Type
```bash
curl -X POST http://example.com/login \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d "username=admin&password=admin"
```

### POST with JSON (single quotes) ⭐
```bash
curl -X POST http://example.com/api \
  -H "Content-Type: application/json" \
  -d '{"username":"admin","password":"admin"}'
```

### POST with JSON (escaped double quotes)
```bash
curl -X POST http://example.com/api \
  -H "Content-Type: application/json" \
  -d "{\"username\":\"admin\",\"password\":\"admin\"}"
```

### POST with JSON (header with single quotes)
```bash
curl -X POST http://example.com/api \
  -H 'Content-Type: application/json' \
  -d '{"username":"admin","password":"admin"}'
```

### POST verbose (for debugging) 🐛
```bash
curl -v -X POST http://example.com/api \
  -H "Content-Type: application/json" \
  -d '{"key":"value"}'
```

### POST with file
```bash
curl -X POST http://example.com/upload -F "file=@document.txt"
```

### POST multipart/form-data
```bash
curl -X POST http://example.com/form \
  -F "name=John" \
  -F "file=@photo.jpg"
```

---

## 🚀 Advanced HTTP Requests

### Add custom header
```bash
curl -H "User-Agent: MyBot" http://example.com
```

### Multiple headers
```bash
curl -H "User-Agent: Bot" \
     -H "Authorization: Bearer token123" \
     http://example.com
```

### Verbose mode (show everything) 📊
```bash
curl -v http://example.com
```

### Include response headers
```bash
curl -i http://example.com
```

### Save cookies 🍪
```bash
curl -c cookies.txt http://example.com
```

### Use saved cookies
```bash
curl -b cookies.txt http://example.com
```

### Basic authentication
```bash
curl -u username:password http://example.com
```

### Follow redirects automatically
```bash
curl -L http://example.com
```

### Save output to file
```bash
curl -o output.html http://example.com
```

### Request timeout ⏱️
```bash
curl --max-time 10 http://example.com
```

### Ignore SSL certificate errors
```bash
curl -k https://example.com
```

---

## 🌍 General Web Scanning

### Download a page
```bash
wget http://example.com
```

### View server headers
```bash
wget --server-response --spider http://example.com
```

### Recursively download a site
```bash
wget -r http://example.com
```

---

## 🔌 Port and Service Scanning

### Basic nmap scan
```bash
nmap example.com
```

### Scan common ports
```bash
nmap -F example.com
```

### Scan with service detection
```bash
nmap -sV example.com
```

### Complete scan 💪
```bash
nmap -A example.com
```

---

## 🌐 DNS Analysis

### Basic DNS information
```bash
nslookup example.com
```

### Detailed DNS information
```bash
dig example.com
```

### All DNS records
```bash
dig example.com ANY
```

### Reverse DNS
```bash
dig -x 192.168.1.1
```

---

## 📂 Directory and File Scanning

### Gobuster (directory enumeration) 🔎
```bash
gobuster dir -u http://example.com \
  -w /usr/share/wordlists/dirb/common.txt
```

### Dirb
```bash
dirb http://example.com
```

### Nikto (vulnerability scanner) 🛡️
```bash
nikto -h http://example.com
```

---

## 📡 WHOIS and Traceroute Information

### Domain information
```bash
whois example.com
```

### Trace the route
```bash
traceroute example.com
```

### Basic ping
```bash
ping example.com
```

---

## 🛠️ Specialized Tools

### HTTPie (colored and readable output) 🎨
```bash
http http://example.com
```

### Netcat (manual connection)
```bash
nc example.com 80
```

### Telnet (for manual HTTP)
```bash
telnet example.com 80
```

---

## 💡 Useful Tips

### 🎯 CTF Tips

- ✅ **curl** is the most versatile tool for analyzing HTTP headers
- ✅ **nmap** is essential for port and service scanning
- ✅ **gobuster** and **dirb** are great for finding hidden directories
- ✅ In CTFs, always check **custom HTTP headers** for flags
- ✅ Use **-v** (verbose) to get more information during execution
- ✅ **OPTIONS** reveals supported HTTP methods, but always try **PUT**, **PATCH**, **DELETE** too
- ✅ The "unexpected" method in CTFs might **not be** in the `Allow` list
- ✅ For JSON use external single quotes: `-d '{"key":"value"}'`
- ✅ If a method returns **401 Unauthorized**, try other available HTTP methods

### 🔒 Security

> ⚠️ **Warning**: These commands are intended exclusively for educational purposes such as training for CTFs. Do not use on systems without explicit authorization.

### 📚 Useful Resources

- [CTFtime](https://ctftime.org/) - CTF Database
- [HackTheBox](https://www.hackthebox.eu/) - Training Platform
- [TryHackMe](https://tryhackme.com/) - Learning Cybersecurity
- [PortSwigger Web Security Academy](https://portswigger.net/web-security) - Free Web Security Training
- [OWASP](https://owasp.org/) - Open Web Application Security Project
- [OLICYBER](https://olicyber.it/) - Italian Cybersecurity Olympics (CTF)

---

## 🤝 Contributing

Have suggestions or new commands to add? Feel free to:

1. 🍴 Fork the repository
2. ✨ Create a branch for your feature
3. 📝 Commit your changes
4. 🚀 Push to the branch
5. 🎉 Open a Pull Request

---

## 📝 License

This project is released under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Author

Created for computer science students - **Kali Linux & CTF**

⭐ If this guide was helpful, leave a star!

---

<div align="center">

**Happy Hacking! 🚀🔐**

Made by Ryuzakxx

</div>
