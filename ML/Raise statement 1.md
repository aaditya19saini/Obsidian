
### `raise` Statement

**Purpose**: Manually trigger an exception to signal an error.

**Syntax**:
```python
raise ExceptionClass("message")
# or re-raise current exception:
raise
```

**Common built-in exceptions**:
- `ValueError` — wrong value
- `TypeError` — wrong type
- `KeyError` — missing dict key
- `RuntimeError` — generic error

**Flow**:
1. `raise` → immediately exits current block
2. Propagates up the call stack
3. If uncaught → program crashes with traceback

**Catching**:
```python
try:
    risky_code()
except ValueError as e:
    handle_error(e)
```

**Key gotcha**: A bare `raise` in an `except` block re-raises the *same* exception (preserving stack trace). A bare `raise` outside an `except` block is a `RuntimeError`.