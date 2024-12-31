# Puppet Functions: Comprehensive Documentation

This document provides a detailed overview of Puppet functions, including their usage, levels of function calling, and advanced features like lambdas and iterators. It also includes information on writing custom functions and structuring Puppet modules.

---

## Puppet DSL and Server-Side Methods

### What is Puppet DSL?

Puppet DSL (Domain-Specific Language) is a declarative language designed for configuration management. It simplifies expressing system configurations and automations by focusing on the desired state rather than implementation details. Puppet DSL supports the use of functions to process data, perform operations, and manage resources.

### Server-Side Methods

Server-side methods refer to functions that run on the Puppet Server during catalog compilation. These functions typically fetch data, manage facts, or retrieve hiera configurations.

**Example:**

```puppet
$os_family = fact('os.family')  # Fetches the OS family fact from the server
```

---

## Calling Puppet Functions

Puppet functions can be called in two primary ways:

1. **Traditional Function Call**:
    
    ```puppet
    notice("Hello World")
    ```
    
2. **Chained Method Call**:
    
    ```puppet
    "Hello World".notice
    ```
    

### Example:

```puppet
$greeting = "Hello Puppet"
notice($greeting)  # Outputs: Hello Puppet
$greeting.notice    # Outputs: Hello Puppet
```

---

## Levels of Calling Functions

Puppet functions can be executed at various levels depending on the scope and purpose.

### 1. Global Level

Functions that are universally available and can be called anywhere in the manifest.

**Example:**

```puppet
notice('This is a global function.')
```

### 2. Environment Level

Functions that are tied to a specific Puppet environment.

**Example:**

```puppet
$env_data = hiera('environment_specific_data')
```

### 3. Module Level

Functions defined within a module's scope and are available only when the module is used.

**Example:**

```puppet
include mymodule::myfunction
```

---

## Assignment Function

Assignment functions are used to assign values to variables or manipulate data.

**Example:**

```puppet
$user_roles = ['admin', 'user', 'guest']
notice($user_roles)
```

---

## Match Function

The `match` function is used to check whether a string matches a regular expression and to extract data using capture groups.

**Example:**

```puppet
$string = 'user@example.com'
if $string =~ /(\w+)@(\w+)\.(\w+)/ {
  notice("Username: ${1}, Domain: ${2}, TLD: ${3}")
}
```

---

## Lambdas (Code Blocks)

Lambdas, or code blocks, are anonymous functions that can be passed as arguments to other functions. They are used with iterators like `each`, `map`, or `reduce`.

**Example:**

```puppet
$names = ['Alice', 'Bob', 'Charlie']
$names.each |$name| {
  notice("Hello ${name}")
}
```

---

## Loops and Iterators

Puppet supports iterating over collections using functions like `each`, `map`, and `filter`.

**Example: `each`**

```puppet
$numbers = [1, 2, 3, 4]
$numbers.each |$num| {
  notice("Number: ${num}")
}
```

**Example: `map`**

```puppet
$squared = $numbers.map |$num| { $num * $num }
notice($squared)  # Outputs [1, 4, 9, 16]
```

---

## Data Validation in Code Blocks

You can validate data inside code blocks using conditionals or assertions.

**Example:**

```puppet
$values = [10, 20, 30]
$values.each |$value| {
  if $value > 15 {
    notice("${value} is greater than 15")
  } else {
    notice("${value} is not greater than 15")
  }
}
```

---

## Writing Custom Functions

Puppet allows you to write custom functions using its Ruby-based API. In the latest Puppet versions, custom functions are written in Ruby within modules.

### Steps for Writing a Custom Function

1. Create a directory structure for the function:
    
    ```
    mymodule/
    ├── lib/
        └── puppet/
            └── functions/
                └── my_function.rb
    ```
    
2. Define the function in `my_function.rb`:
    
    ```ruby
    Puppet::Functions.create_function(:my_function) do
      def my_function(arg)
        "Hello, #{arg}!"
      end
    end
    ```
    
3. Use the function in your manifest:
    
    ```puppet
    $greeting = my_function('Puppet')
    notice($greeting)  # Outputs: Hello, Puppet!
    ```
    

---

## Functions Demo

Here is a demonstration of multiple Puppet functions:

### Example Manifest:

```puppet
# Global function
notice("Starting the Puppet demo!")

# Assignment function
$os = fact('os.name')
notice("Operating System: ${os}")

# Iterator with lambda
$files = ['/etc/hosts', '/etc/resolv.conf']
$files.each |$file| {
  if file($file) {
    notice("${file} exists.")
  } else {
    notice("${file} does not exist.")
  }
}

# Custom function usage
$custom_message = my_function('world')
notice($custom_message)
```

---

## Module Layout (Tree)

Puppet modules have a specific layout to organize code, data, and functions effectively. Here’s an example module structure:

```
mymodule/
├── manifests/
│   ├── init.pp          # Entry point for the module
│   └── myclass.pp       # Additional classes
├── lib/
│   └── puppet/
│       └── functions/
│           └── my_function.rb  # Custom functions
├── templates/           # ERB or EPP templates
├── files/               # Static files
├── hiera.yaml           # Hiera configuration (if applicable)
├── data/                # Hiera data files
└── metadata.json        # Module metadata
```

---
