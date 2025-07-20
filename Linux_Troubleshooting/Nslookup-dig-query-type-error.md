# nslookup Query Type Error: "unknown query type: all"

## Problem
Using `nslookup` with `set type=all` leads to an error.

### Observed:
- Command:
  ```
  nslookup
  > set type=all
  unknown query type: all
  ```

## Root Cause
nslookup does not support the `type=all` directive. It only accepts specific query types (e.g., A, MX, NS). The behavior is inconsistent compared to dig.

## Fix Steps

### Recommended Alternatives:

1. Use supported types in nslookup:
   ```
   set type=A
   set type=MX
   set type=TXT
   set type=NS
   ```

2. Use dig for ALL-like queries:
   ```bash
   dig example.com ANY
   ```

3. To get specific records with dig:
   ```bash
   dig example.com A
   dig example.com MX
   ```
