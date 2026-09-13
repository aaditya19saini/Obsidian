 A **decorator** is a function that takes another function (or class) and extends/modifies its behavior without changing its source code. The `@` syntax is just syntactic sugar:

```python
@dataclass
class Foo: ...
```

is equivalent to:

```python
class Foo: ...
Foo = dataclass(Foo)
```

### How it works

A decorator is just a callable (`dataclass` is a function) that receives the decorated thing as its argument and returns a replacement. For `@dataclass`, it:

1. Takes your class
2. Reads the <span style="color:rgb(0, 176, 240)">type annotations</span> (e.g., `current_revenue: float`)
3. Dynamically generates `__init__`, `__repr__`, `__eq__`, `__hash__` methods
4. Attaches them to the class
5. Returns the modified class (or a new one)

### Decorators are general-purpose

Common uses beyond `@dataclass`:

- **`@property`** — makes a method look like an attribute
- **`@staticmethod`** / **`@classmethod`** — changes method binding
- **`@functools.lru_cache`** — adds memoization
- **`@contextmanager`** — turns a generator into a context manager

### A simple custom decorator example:

```python
def add_greeting(func):
    def wrapper(*args, **kwargs):
        print("Hello!")
        return func(*args, **kwargs)
    return wrapper

@add_greeting
def say_name(name):
    print(f"My name is {name}")

say_name("Alice")
# Output:
# Hello!
# My name is Alice
```

Here `say_name` was replaced by `wrapper` which prints "Hello!" then calls the original. The original function is never executed directly — the decorator's wrapper runs instead.