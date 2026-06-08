# Skill: M-PESA Daraja API Expert

## Purpose
Makes Claude an expert at Safaricom's Daraja API — endpoints, authentication,
sandbox vs production, common errors, and mpesa-mcp integration.

## Load this skill when:
- Building M-PESA payment integrations
- Debugging Daraja API errors
- Working with mpesa-mcp (pip install mpesa-mcp)
- Training AI agents to use M-PESA tools

---

## API Architecture

**Base URL (sandbox):** https://sandbox.safaricom.co.ke
**Base URL (production):** https://api.safaricom.co.ke
**Always use HTTPS. No HTTP fallback.**

### Authentication flow:
1. GET /oauth/v1/generate?grant_type=client_credentials
   - Basic Auth: base64(consumer_key:consumer_secret)
   - Returns: {"access_token": "...", "expires_in": "3599"}
2. Use Bearer token in Authorization header for all subsequent calls
3. Token expires in ~1 hour — cache and refresh

---

## Key Endpoints

### STK Push (Lipa Na M-PESA Online)
**Endpoint:** POST /mpesa/stkpush/v1/processrequest
**Use:** Customer-initiated payment from their phone (most common for apps)
**Key fields:**
- BusinessShortCode: 174379 (sandbox) or your paybill/till
- Password: base64(ShortCode + Passkey + Timestamp)
- Timestamp: YYYYMMDDHHMMSS (Nairobi time: UTC+3)
- Amount: integer (no decimals)
- PartyA: customer phone in 2547XXXXXXXX format
- PartyB: your shortcode
- PhoneNumber: same as PartyA (for CustomerPayBillOnline)
- TransactionType: CustomerPayBillOnline or CustomerBuyGoodsOnline
- CallBackURL: must be https, publicly accessible, no localhost

**Sandbox test phone:** 254708374149
**Sandbox passkey:** bfb279f9aa9bdbcf158e97dd71a467cd2e0c893059b10f78e6b72ada1ed2c919

### STK Query
**Endpoint:** POST /mpesa/stkpushquery/v1/query
**Use:** Check payment status after initiating STK Push
**Key field:** CheckoutRequestID from the STK Push response

### B2C (Business to Customer)
**Endpoint:** POST /mpesa/b2c/v1/paymentrequest
**Use:** Send money to a customer (disbursements, refunds, salaries)
**Additional auth:** InitiatorName + SecurityCredential (encrypted with Safaricom cert)
**Commands:** SalaryPayment, BusinessPayment, PromotionPayment

### Account Balance
**Endpoint:** POST /mpesa/accountbalance/v1/query
**Use:** Check your M-PESA business account balance
**Async:** Result comes to ResultURL callback

### Transaction Status
**Endpoint:** POST /mpesa/transactionstatus/v1/query
**Use:** Check status of any past transaction

---

## Phone Number Normalization

**Daraja expects:** 2547XXXXXXXX (12 digits, no +)
**Users may enter:**
- 07XXXXXXXX → 2547XXXXXXXX (add 254, remove leading 0)
- +2547XXXXXXXX → 2547XXXXXXXX (remove +)
- 2547XXXXXXXX → unchanged

```python
def normalize_phone(phone: str) -> str:
    phone = phone.strip().replace(" ", "").replace("-", "")
    if phone.startswith("+"):
        phone = phone[1:]
    if phone.startswith("07") or phone.startswith("01"):
        phone = "254" + phone[1:]
    if not phone.startswith("254"):
        phone = "254" + phone
    return phone
```

---

## Common Errors

| Error Code | Meaning | Fix |
|-----------|---------|-----|
| 400.002.02 | Invalid access token | Re-authenticate |
| 400.002.05 | Request cancelled | User cancelled on phone |
| 1037 | DS timeout (phone off/no signal) | Retry or notify user |
| 1032 | Request cancelled by user | No retry needed |
| 2001 | Wrong credentials | Check ShortCode/Passkey |
| 404 | Invalid initiator | Check InitiatorName for B2C |

---

## Callback Handling

All async operations (B2C, Balance, Transaction Status) return results via callback URL.
**Your callback must:**
- Return HTTP 200 immediately (within 5 seconds)
- Process result asynchronously
- Handle: ResultCode 0 (success) vs others (failure)
- Store: TransactionReceipt, Amount, Phone in your DB

---

## mpesa-mcp Integration

```python
# Using Claude Code or any MCP client:
# Tool: mpesa_stk_push
{
  "phone": "0712345678",  # auto-normalized to 2547XXXXXXXX
  "amount": 500,           # KES 500
  "account_ref": "INV001", # max 12 chars
  "description": "Invoice payment"
}

# Tool: mpesa_stk_query
{
  "checkout_request_id": "ws_CO_xxxxx"
}

# Tool: mpesa_account_balance
{}  # returns balance to configured callback
```

**Install:** pip install mpesa-mcp
**GitHub:** https://github.com/gabrielmahia/mpesa-mcp
**Docs:** 22 tools covering all major Daraja API endpoints

---

## Sandbox vs Production Checklist

| Setting | Sandbox | Production |
|---------|---------|------------|
| MPESA_SANDBOX | true | false |
| Base URL | sandbox.safaricom.co.ke | api.safaricom.co.ke |
| ShortCode | 174379 | Your registered shortcode |
| Passkey | bfb279f9... | From Daraja portal |
| Callback | Any HTTPS URL | Must be publicly accessible |
| Real money | NO | YES |

**NEVER test with production credentials in sandbox mode.**
**ALWAYS label demo transactions clearly.**

---
*© 2026 AI Kung Fu LLC · MIT License · claude-east-africa-skills*
