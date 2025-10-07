# 🏁 RACER v2.0 Elite

<div align="center">

**Professional Race Condition Detection Tool for Web Applications**

![Version](https://img.shields.io/badge/version-2.0%20Elite-purple)
![License](https://img.shields.io/badge/license-MIT-green)
![Platform](https://img.shields.io/badge/platform-Browser%20Bookmarklet-blue)

*Created by me aka shadowxp*

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [What are Race Conditions?](#-what-are-race-conditions)
- [Features](#-features)
- [Installation](#-installation)
- [Usage Guide](#-usage-guide)
- [Understanding the Interface](#-understanding-the-interface)
- [Vulnerability Patterns](#-vulnerability-patterns)
- [Interpreting Results](#-interpreting-results)
- [Exploit Generation](#-exploit-generation)
- [Technical Details](#-technical-details)
- [Security & Ethical Considerations](#-security--ethical-considerations)
- [Contributing](#-contributing)
- [Credits](#-credits)

---

## 🎯 Overview

**RACER v2.0 Elite** is an advanced browser-based bookmarklet designed to identify race condition vulnerabilities in web applications. It automatically intercepts HTTP requests, analyzes them for race-prone patterns, and provides comprehensive testing capabilities to detect Time-of-Check to Time-of-Use (TOCTOU) vulnerabilities.

This tool is invaluable for:
- 🔍 **Security Researchers**: Identify critical race condition vulnerabilities
- 🛡️ **Penetration Testers**: Comprehensive testing of web applications
- 👨‍💻 **Bug Bounty Hunters**: Discover high-value vulnerabilities with verified proof
- 🏢 **Development Teams**: Test and secure their applications before deployment

---

## 💡 What are Race Conditions?

A **race condition** occurs when multiple operations execute concurrently and the system's behavior depends on the precise timing or sequence of these operations. In web applications, this typically happens when:

1. **Multiple requests** are sent simultaneously to the same endpoint
2. The server **doesn't properly handle** concurrent operations
3. This leads to **unexpected behavior** like:
   - Processing a payment multiple times
   - Withdrawing more than the available balance
   - Redeeming a coupon/voucher multiple times
   - Bypassing rate limits or quantity restrictions

### Real-World Example

```
User has $100 in their account
→ Send 50 simultaneous withdrawal requests for $100 each
→ If vulnerable, multiple requests process before balance update
→ User withdraws $5000 from a $100 balance
```

This is also known as a **TOCTOU (Time-of-Check to Time-of-Use)** vulnerability.

---

## ✨ Features

### 🔍 Auto Detection
- **Automatic Request Interception**: Captures all HTTP requests (Fetch & XHR)
- **Smart Pattern Recognition**: Identifies 12+ elite HackerOne vulnerability patterns
- **Risk Scoring**: Assigns severity and bounty estimates to each endpoint
- **H1 References**: Links to known HackerOne reports for similar vulnerabilities

### 🎮 Manual Testing
- **Custom Endpoint Testing**: Test any API endpoint manually
- **Configurable Parameters**: Control request count, method, body, and headers
- **Real-time Progress**: Visual feedback during testing
- **Credential Injection**: Automatically includes authentication tokens and CSRF tokens

### 📊 State Verification
- **Before/After Snapshots**: Captures application state before and after testing
- **Balance Tracking**: Monitors account balance changes
- **DOM Monitoring**: Detects UI changes that indicate state modification
- **Verified Proof**: Provides concrete evidence of successful exploitation

### 💣 Exploit Generation
- **JavaScript Exploits**: Copy-paste ready browser console scripts
- **Python Exploits**: Async Python scripts with aiohttp
- **Detailed Documentation**: Each exploit includes target info, severity, and impact
- **One-Click Testing**: Re-run tests with saved parameters

### 🎨 Premium UI
- **Modern Design**: Gradient-rich, professional interface
- **Dark Theme**: Easy on the eyes during long testing sessions
- **Responsive Layout**: Clean organization with tabbed navigation
- **Visual Feedback**: Color-coded results, badges, and animations

---

## 🚀 Installation

### Method 1: Bookmark Bar (Recommended)

1. **Copy the bookmarklet code** from `racer.js`
2. **Create a new bookmark** in your browser
3. **Paste the entire code** as the URL/Location
4. **Name it** something memorable like "🏁 RACER"
5. **Save** the bookmark

### Method 2: Browser Console (Quick Test)

1. Open your browser's **Developer Console** (F12)
2. Copy and paste the entire contents of `racer.js`
3. Press **Enter** to execute

### Step-by-Step Visual Guide

#### Chrome/Edge:
1. Press `Ctrl+Shift+B` (Windows) or `Cmd+Shift+B` (Mac) to show bookmarks bar
2. Right-click on bookmarks bar → "Add page"
3. Name: `🏁 RACER v2.0`
4. URL: Paste the bookmarklet code from `racer.js`
5. Save

#### Firefox:
1. Press `Ctrl+Shift+B` (Windows) or `Cmd+Shift+B` (Mac) to show bookmarks
2. Right-click in bookmarks toolbar → "New Bookmark"
3. Name: `🏁 RACER v2.0`
4. Location: Paste the bookmarklet code
5. Save

#### Safari:
1. Show favorites bar: View → Show Favorites Bar
2. Drag any link to favorites bar
3. Right-click → Edit
4. Replace URL with bookmarklet code
5. Rename to `🏁 RACER v2.0`

---

## 📖 Usage Guide

### Getting Started

1. **Navigate to your target website**
   - Log in to your account if testing authenticated endpoints
   - Ensure you have permission to test the application

2. **Activate RACER**
   - Click the bookmarklet in your bookmark bar
   - A panel will slide in from the right side of your screen

3. **Start Testing**
   - Use the application normally to capture requests
   - RACER automatically analyzes all HTTP traffic

### Workflow Example

#### Testing a Banking App

```
1. Click RACER bookmarklet
2. Navigate to withdrawal page
3. Initiate a withdrawal request
4. RACER captures the request automatically
5. Check "Auto Detect" tab → See the endpoint ranked
6. Click "🏁 Test Race" on the endpoint
7. Review results in "Results" tab
8. If vulnerable, generate exploit in "Exploits" tab
```

#### Manual Testing

```
1. Activate RACER
2. Go to "🎮 Manual Test" tab
3. Enter endpoint URL: https://api.example.com/api/withdraw
4. Select HTTP Method: POST
5. Add request body: {"amount": 100}
6. Set parallel requests: 50
7. Expected successes: 1
8. Click "🚀 START RACE ATTACK"
9. Wait for results
```

---

## 🖥️ Understanding the Interface

### Tab Overview

#### 🔍 Auto Detect
- **Purpose**: Automatically discovers race-prone endpoints
- **Display**: Shows captured requests with risk scores
- **Action**: One-click testing of detected endpoints

**What you'll see:**
- Total requests captured
- Number of race candidates found
- High-priority targets with:
  - Category (e.g., "Balance/Wallet Withdrawal")
  - Risk score (0-100)
  - Severity (CRITICAL, HIGH, MEDIUM)
  - H1 badge (if similar vulnerability reported)
  - Matched keywords
  - Estimated bounty range
  - "🏁 Test Race" button

#### 🎮 Manual Test
- **Purpose**: Test specific endpoints with custom parameters
- **Configuration**:
  - **Endpoint URL**: Full API endpoint URL
  - **HTTP Method**: POST, PUT, PATCH, or DELETE
  - **Request Body**: JSON payload (optional)
  - **Parallel Requests**: Number of simultaneous requests (10-500)
  - **Expected Successes**: How many should normally succeed (usually 1)

**Pro Tip**: Start with Auto Detect to find targets, then use Manual Test for fine-tuning.

#### 📊 Results
- **Purpose**: View all test results
- **Information Shown**:
  - Total tests run
  - Number of vulnerable endpoints found
  - Detailed results for each test:
    - Success/failure counts
    - Timing information
    - Vulnerability status
    - State verification proof
    - Visual race request chart

#### 💣 Exploits
- **Purpose**: Generate proof-of-concept exploits
- **Capabilities**:
  - Copy JavaScript exploit for browser console
  - Copy Python exploit script
  - View detailed vulnerability description
  - See verified proof of exploitation
  - Estimated bounty range
  - Re-run test button

---

## 🎯 Vulnerability Patterns

RACER v2.0 Elite detects **12 elite vulnerability patterns** based on real HackerOne reports:

### Critical Severity (Score: 90-98)

| Pattern | Keywords | Impact | Bounty Range |
|---------|----------|--------|--------------|
| **Balance/Wallet Withdrawal** | withdraw, withdrawal, balance, wallet, funds, payout | Withdraw more than available balance | $25K - $50K |
| **Fund Transfer** | transfer, send, move_funds, payment_transfer | Transfer without sufficient funds | $20K - $45K |
| **Voucher/Coupon Redemption** | voucher, coupon, promo, redeem, apply_code | Redeem multiple times | $10K - $35K |
| **Gift Card Application** | gift, gift_card, credit, apply_credit | Apply gift card multiple times | $12K - $40K |
| **Purchase/Payment Processing** | payment, checkout, purchase, buy, order | Buy without payment | $8K - $30K |

### High Severity (Score: 80-89)

| Pattern | Keywords | Impact | Bounty Range |
|---------|----------|--------|--------------|
| **User Invitation** | invite, send_invite, invitation | Bypass invitation limits | $3K - $15K |
| **Group/Team Join** | join, join_group, member_add | Bypass membership restrictions | $2K - $12K |
| **Retest/Confirmation** | retest, confirm, verify, approve | Multiple confirmations | $5K - $20K |

### Medium Severity (Score: 70-79)

| Pattern | Keywords | Impact | Bounty Range |
|---------|----------|--------|--------------|
| **Booking/Reservation** | book, reserve, ticket, appointment | Book without payment | $3K - $15K |
| **Social Interactions** | like, follow, subscribe, vote | Bypass rate limits | $1K - $8K |
| **Flag/Score Submission** | submit, flag, score, achievement | Submit multiple times | $1.5K - $10K |
| **Update Resource** | update, edit, modify, change | Inconsistent updates | $1K - $5K |

---

## 📈 Interpreting Results

### Understanding Test Results

#### Safe Result ✅
```
Test #1 SAFE
POST /api/update_profile
Results: ✓ 1 / ✗ 49 | ⏱ 245ms
✅ No race condition detected
```
**Interpretation**: Only 1 request succeeded (as expected). The endpoint is properly protected.

#### Vulnerable Result 🔴
```
Test #2 CRITICAL
POST /api/withdraw
Results: ✓ 47 / ✗ 3 | ⏱ 189ms
⚠️ Vulnerability: More successes than expected (47 > 1)
Confidence: 95%
```
**Interpretation**: 47 requests succeeded when only 1 should have. Race condition detected!

#### Verified Vulnerable Result ✓ 🔴
```
Test #3 CRITICAL - VERIFIED
POST /api/withdraw
Results: ✓ 45 / ✗ 5 | ⏱ 192ms

✓ VERIFIED PROOF:
• Balance: $100.00 → $-4400.00
• Difference: $-4500.00
⚠️ Balance went negative!
Impact: CRITICAL - Negative balance achieved
```
**Interpretation**: Not only did multiple requests succeed, but RACER verified the account balance changed from $100 to -$4400. This is concrete proof of exploitation!

### Confidence Levels

- **85-100%**: High confidence - Very likely vulnerable
- **70-84%**: Medium-high confidence - Likely vulnerable, needs verification
- **50-69%**: Medium confidence - Possibly vulnerable, further testing recommended
- **Below 50%**: Low confidence - May be false positive

### Race Visualization

Each small bar represents a request:
- **Green bars**: Successful requests
- **Red bars**: Failed requests

**Normal**: 1 green, 49 red (1 success out of 50)  
**Vulnerable**: 45 green, 5 red (45 successes out of 50)

---

## 💻 Exploit Generation

### JavaScript Exploit

Perfect for quick testing in browser console:

```javascript
// RACER V2.0 Elite - JS Exploit
// Target: https://api.example.com/api/withdraw
// Severity: CRITICAL - VERIFIED

(async()=>{
  console.log("[RACER] 🏁 Starting...");
  const p=[];
  for(let i=0;i<50;i++){
    p.push(fetch("https://api.example.com/api/withdraw",{
      method:"POST",
      body:'{"amount":100}',
      credentials:"include"
    }));
  }
  const r=await Promise.all(p);
  const s=r.filter(x=>x.ok).length;
  console.log("[RACER] ✓ Success:",s);
  console.log("[RACER] ✗ Failed:",r.length-s);
  if(s>1)console.log("[RACER] 🔴 RACE DETECTED!");
})();
```

### Python Exploit

Professional async script with colorful output:

```python
#!/usr/bin/env python3
"""RACER V2.0 Elite - Race Condition Exploit

Target: https://api.example.com/api/withdraw
Method: POST
Severity: CRITICAL - VERIFIED
"""
import asyncio,aiohttp,time
from colorama import Fore,Style,init
init(autoreset=True)

TARGET="https://api.example.com/api/withdraw"
METHOD="POST"
PARALLEL=50
EXPECTED=1
BODY='''{"amount":100}'''

async def exploit():
    print(f"{Fore.CYAN}[*] RACER V2.0 - Starting attack...")
    async with aiohttp.ClientSession() as s:
        tasks=[s.post(TARGET,data=BODY) for _ in range(PARALLEL)]
        r=await asyncio.gather(*tasks,return_exceptions=True)
        success=sum(1 for x in r if not isinstance(x,Exception)and x.status==200)
        print(f"{Fore.GREEN}✓ Success: {success}")
        print(f"{Fore.RED}✗ Failed: {len(r)-success}")
        if success>EXPECTED:print(f"{Fore.GREEN}🔴 RACE DETECTED!")

if __name__=="__main__":asyncio.run(exploit())
```

**Usage:**
```bash
# Save as exploit.py
python3 exploit.py
```

---

## 🔧 Technical Details

### How RACER Works

#### 1. Request Interception
```javascript
// Overrides native fetch API
window.fetch = function() {
  // Captures request details
  // Calls original fetch
}

// Overrides XMLHttpRequest
XMLHttpRequest.prototype.open = function() {
  // Captures request details
  // Calls original XHR
}
```

#### 2. Pattern Analysis
- Analyzes URLs and request bodies for keywords
- Matches against 12 vulnerability patterns
- Assigns risk scores based on:
  - Pattern severity
  - Number of keyword matches
  - HTTP method
  - Known HackerOne reports

#### 3. Race Condition Testing
```
1. Capture state snapshot (balance, DOM)
2. Send N parallel requests simultaneously
3. Wait for all responses
4. Capture state snapshot again
5. Compare snapshots
6. Analyze response patterns
```

#### 4. Vulnerability Detection
RACER identifies race conditions by:
- **Success Count**: More successes than expected
- **Response Patterns**: Duplicate responses indicating race
- **State Changes**: Verified balance or data changes
- **Timing Analysis**: Similar response times suggesting concurrent execution

#### 5. State Verification
- Queries balance endpoints: `/api/balance`, `/api/wallet`, etc.
- Parses DOM for balance elements
- Compares before/after states
- Provides concrete proof of exploitation

### Automatic Credential Injection

RACER automatically finds and includes:
- **CSRF Tokens**: From meta tags, hidden inputs
- **Auth Tokens**: From localStorage, sessionStorage
- **API Keys**: From storage
- **Session Cookies**: Via `credentials: 'include'`

This ensures tests run with proper authentication!

---

## ⚠️ Security & Ethical Considerations

### Legal Usage Only

**IMPORTANT**: This tool should ONLY be used on:
- ✅ Applications you own
- ✅ Applications you have written permission to test
- ✅ Bug bounty programs that explicitly allow testing
- ✅ Authorized penetration testing engagements

**NEVER use this tool on:**
- ❌ Applications without permission
- ❌ Production systems without authorization
- ❌ Financial or critical systems without proper approval

### Responsible Disclosure

If you discover a vulnerability:

1. **Document everything**: Screenshots, requests, responses
2. **DO NOT exploit maliciously**: Test minimally to confirm
3. **Report immediately**: To the security team or bug bounty program
4. **Give time to fix**: Follow responsible disclosure timelines
5. **Don't disclose publicly**: Until the vendor has patched

### Bug Bounty Programs

RACER is perfect for authorized bug bounty testing on platforms like:
- HackerOne
- Bugcrowd
- Synack
- Intigriti
- YesWeHack

Always read and follow the program rules!

### Testing Best Practices

- **Start small**: Begin with 10-20 parallel requests
- **Monitor impact**: Watch for server load issues
- **Use test accounts**: Don't test on real user accounts
- **Clean up**: Revert any changes made during testing
- **Document thoroughly**: Keep detailed notes for your report

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

### Reporting Bugs
- Open an issue with details about the bug
- Include browser version and steps to reproduce
- Screenshots or console errors are helpful

### Feature Requests
- Describe the feature and use case
- Explain why it would be valuable
- Consider submitting a PR!

### Code Contributions
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

### Adding Vulnerability Patterns
Found a new race condition pattern? Add it to the patterns array:

```javascript
{
  name: 'Your Pattern Name',
  keywords: ['keyword1', 'keyword2'],
  methods: ['POST', 'PUT'],
  score: 85,
  severity: 'HIGH',
  bounty: [5000, 20000],
  h1Report: true,
  reference: 'Description or H1 report link'
}
```

---

## 📜 Credits

**RACER v2.0 Elite** - Created by **me** aka **shadowxp**

### Acknowledgments
- Inspired by real-world HackerOne reports
- Built with modern web technologies
- Community feedback and suggestions

### Version History

**v2.0 Elite** (Current)
- ✨ Enhanced UI with modern gradients
- ✅ State verification system
- 🎯 12 elite H1 patterns
- 💣 Advanced exploit generation
- 📊 Visual race charts
- 🔍 Improved detection algorithms

**v1.0** (Legacy)
- Basic race condition testing
- Request interception
- Manual testing only

---

## 📄 License

MIT License - Feel free to use, modify, and distribute with attribution.

---

## 🔗 Links

- **Repository**: [github.com/Sahil01010011/Racer](https://github.com/Sahil01010011/Racer)
- **Issues**: Report bugs and request features
- **Discussions**: Share your findings and get help

---

## 💬 Support

Having issues or questions?

1. Check this README thoroughly
2. Search existing issues
3. Open a new issue with details
4. Join the discussion section

---

<div align="center">

**Happy Hunting! 🏁**

*Remember: With great power comes great responsibility.*

*Always hack ethically and legally.*

---

Made with ❤️ by me aka shadowxp

</div>
