# 🐍 Scapy Error: 'summary' is Not Defined

## 🐛 Problem
Calling summary() directly in Scapy throws an error.

### 💬 Observed:
```python
NameError: name 'summary' is not defined
```

## 🔍 Root Cause
The function summary() must be called on a packet object or packet list. Scapy does not expose summary as a global function.

## 🛠️ Fix Steps

### ✅ Correct Usage Example:
```python
from scapy.all import sniff

a = sniff(count=10)
a.summary()
```

- Ensure you're using the method on the sniffed packet list or individual packet.

### ❌ Incorrect:
```python
summary()
```
