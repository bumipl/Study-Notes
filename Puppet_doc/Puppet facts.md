# Understanding `$facts` and `$::facts` in Puppet

In Puppet, `$facts` and `$::facts` are used to access facter variables that provide information about the system's environment. This documentation explains their differences, usage, and best practices.

---

## 1. **What Are Facts?**

Facts in Puppet are pieces of information about the system, such as operating system details, network settings, and hardware specifications. These facts are provided by [Facter](https://puppet.com/docs/facter/latest/index.html), Puppet's fact-gathering tool.

Facts are stored as key-value pairs and can be accessed in Puppet manifests using the `$facts` or `$::facts` variables.

### Examples of Common Facts:

- `$facts['os']['name']`: The name of the operating system (e.g., `Ubuntu`, `RedHat`).
- `$facts['os']['family']`: The family of the operating system (e.g., `Debian`, `RedHat`).
- `$facts['networking']['ip']`: The primary IP address of the system.

---

## 2. **Difference Between `$facts` and `$::facts`**

### **`$facts`**

- Introduced in Puppet 4.
- A **global variable** that stores all the facts gathered by Facter.
- Simplifies access to facts without the need for a global namespace prefix.

### **`$::facts`**

- `$::` explicitly references a **global scope** variable.
- Useful in complex manifests or modules to avoid conflicts with local variables.
- `$::facts` ensures that you are explicitly accessing the global facts variable.

### Practical Difference:

In most cases, `$facts` and `$::facts` behave the same because `$facts` is inherently global. However, `$::facts` can be helpful to avoid ambiguity in deeply nested manifests or modules.

---

## 3. **Examples**

### Using `$facts`:

```puppet
notify { "Operating System: ${facts['os']['name']}": }
notify { "OS Family: ${facts['os']['family']}": }
```

### Using `$::facts`:

```puppet
notify { "Operating System: ${::facts['os']['name']}": }
notify { "OS Family: ${::facts['os']['family']}": }
```

Both examples produce the same output, but `$::facts` explicitly ensures that the global variable is referenced.

---

## 4. **When to Use `$::facts`**

- In complex modules where local variables might conflict with fact names.
- When writing reusable modules that may introduce variable conflicts.
- To ensure clarity and avoid accidental usage of local variables instead of global facts.

Example:

```puppet
class example {
  $facts = 'local value' # Local variable

  notify { "Local variable: ${facts}": }
  notify { "Global fact: ${::facts['os']['name']}": }
}
```

Output:

```
Notice: Local variable: local value
Notice: Global fact: Ubuntu
```

---

## 5. **Best Practices**

1. **Prefer `$facts` for Simplicity**:
    
    - Use `$facts` for most scenarios as it is less verbose and easier to read.
2. **Use `$::facts` for Explicit Global References**:
    
    - In complex manifests or nested scopes, use `$::facts` to avoid ambiguity and ensure clarity.
3. **Avoid Overwriting Global Variables**:
    
    - Avoid creating local variables with the same name as facter keys (e.g., `os`, `networking`) to prevent confusion.

---

## 6. **Commonly Used Facts**

Here are some commonly used facts that you might encounter:

|Fact Key|Description|Example Value|
|---|---|---|
|`$facts['os']['name']`|Name of the operating system|`Ubuntu`|
|`$facts['os']['family']`|OS family|`Debian`|
|`$facts['os']['release']`|OS version details|`{"major": "20.04"}`|
|`$facts['networking']`|Networking details|`{...}`|
|`$facts['processors']`|CPU information|`{...}`|

---

## 7. **Troubleshooting Facts**

If facts are not working as expected:

1. **Check Fact Availability:**
    
    - Run `facter` directly on the system to list all available facts:
        
        ```bash
        facter
        ```
        
2. **Debugging in Puppet:**
    
    - Use the `puppet apply` command with debug flags:
        
        ```bash
        puppet apply my_manifest.pp --debug
        ```
        
3. **Ensure Compatibility:**
    
    - Ensure that your Puppet version supports the `$facts` variable (Puppet 4 and later).

---

By understanding `$facts` and `$::facts`, you can write more robust and maintainable Puppet manifests while avoiding common pitfalls.