# Bash commands to analyze URLs
A list of bash commands to analyze and get output of elements in URLs, send POST, PUT, PATCH requests to servers. ecc...


HEADER Request 
```bash
curl -I http://example.com
```

GET Request with visible headers
```bash
curl -i http://example.com
```

HEADER with detailed output
```bash
curl -v http://example.com
```

Follow the redirect
```bash
curl -L -I http://example.com
```

# GENERAL WEB SCAN

Download a page
```bash
wget http://example.com
```

