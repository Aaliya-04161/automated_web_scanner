# Automated Web Scanner

A simple Python command-line tool that checks a website's **HTTP security headers** and produces a quick pass/fail report with an overall score.

> ⚠️ **Use responsibly.** Only scan websites you own or have explicit permission to test. The tool asks for confirmation before every scan.

---

## Features

- Asks for permission confirmation before scanning
- Accepts a URL with or without `https://` (e.g. `example.com`)
- Reports the site's HTTP status code
- Checks 6 common security-related headers
- Gives each header a `PASS`, `FAIL` or `WARN` result
- Prints an overall score out of 6

## Headers Checked

| Header | Why it matters |
|---|---|
| `Content-Security-Policy` | Helps prevent cross-site scripting (XSS) and data injection attacks |
| `X-Frame-Options` | Protects against clickjacking by controlling iframe embedding |
| `Strict-Transport-Security` | Forces browsers to use HTTPS |
| `X-Content-Type-Options` | Stops browsers from MIME-sniffing responses |
| `Referrer-Policy` | Controls how much referrer information is shared |
| `Access-Control-Allow-Origin` | Defines which origins can access the resource (CORS); overly open values are flagged as `WARN` |

## Project Structure

```
automated_web_scanner/
├── Aaliya_AutomatedWebScanner.py   # Main scanner script
├── requirements.txt                # Python dependencies
└── README.md                       # Project documentation
```

## Requirements

- Python 3.8 or higher
- The packages listed in `requirements.txt`

## Installation

1. **Clone or download** this project and open the folder:
   ```bash
   cd automated_web_scanner
   ```

2. **(Optional) Create a virtual environment:**
   ```bash
   python -m venv venv
   venv\Scripts\activate        # Windows
   source venv/bin/activate     # macOS / Linux
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

## Usage

Run the script:

```bash
python Aaliya_AutomatedWebScanner.py
```

Then follow the prompts:

1. Confirm you have permission to scan the site (`yes` / `no`)
2. Enter the website URL (e.g. `example.com`)

## Sample Outputs

### Example 1: `example.com`

```
Do you have permission to scan this site? (yes/no) yes
Enter a website URL: example.com

Automated Web Scanner Report
----------------------------
Website: https://example.com
HTTP status: 200

Header checks:
- Content-Security-Policy: FAIL
- X-Frame-Options: FAIL
- Strict-Transport-Security: FAIL
- X-Content-Type-Options: FAIL
- Referrer-Policy: FAIL
- Access-Control-Allow-Origin: PASS

Score: 1/6
```

### Example 2: `github.com`

```
Do you have permission to scan this site? (yes/no) yes
Enter a website URL: github.com

Automated Web Scanner Report
----------------------------
Website: https://github.com
HTTP status: 200

Header checks:
- Content-Security-Policy: PASS
- X-Frame-Options: PASS
- Strict-Transport-Security: PASS
- X-Content-Type-Options: PASS
- Referrer-Policy: PASS
- Access-Control-Allow-Origin: PASS

Score: 6/6
```

### Example 3: `httpbin.org`

```
Do you have permission to scan this site? (yes/no) yes
Enter a website URL: httpbin.org

Automated Web Scanner Report
----------------------------
Website: https://httpbin.org
HTTP status: 200

Header checks:
- Content-Security-Policy: FAIL
- X-Frame-Options: FAIL
- Strict-Transport-Security: FAIL
- X-Content-Type-Options: FAIL
- Referrer-Policy: FAIL
- Access-Control-Allow-Origin: WARN

Score: 0/6
```

## Understanding the Results

| Result | Meaning |
|---|---|
| `PASS` | The header is present and configured acceptably |
| `WARN` | The header is present but may be too permissive |
| `FAIL` | The header is missing |

**Score:** the number of headers that received a `PASS`, out of 6. A higher score means better baseline header hygiene.

## Limitations

- Only checks response headers; it does **not** detect vulnerabilities in the site's code or content
- A high score does not guarantee a site is secure, and a low score does not mean it is vulnerable
- Results reflect the response from the site's home page only

## Disclaimer

This project is for **educational purposes**. The author is not responsible for misuse. Always obtain authorization before scanning any website.

## Author

**Aaliya Rehman**

Developed as a Python / cybersecurity learning project.