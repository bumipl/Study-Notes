# Puppet Templates Documentation

This document provides a comprehensive guide to using Puppet templates, covering their types, calling methods, template tags, handling blank lines, and creating dynamic file content. It also includes examples and recommended module layouts.

---

## What Are Puppet Templates?

Puppet templates allow you to create dynamic content for configuration files or other text-based resources. They are powerful tools for generating customized files based on variable data or facts.

---

## Types of Template Formats

Puppet supports two main types of template formats:

1. **EPP (Embedded Puppet Templates)**
    
    - Preferred in modern Puppet versions.
    - Use `.epp` file extensions.
    - Cleaner syntax with parameterized content.
    - Example:
        
        ```epp
        <% | String $role, String $server_name | -%>
        This is a <%= $role %> server named <%= $server_name %>.
        ```
        
2. **ERB (Embedded Ruby Templates)**
    
    - Use `.erb` file extensions.
    - Embedded Ruby code inside templates.
    - Example:
        
        ```erb
        This is a <%= @role %> server named <%= @server_name %>.
        ```
        

**Note**: EPP is recommended as it integrates better with Puppet's DSL and has stricter syntax validation.

---

## Calling Puppet Templates

Templates can be called in manifests to generate content dynamically.

![Opis obrazu](Screenshot%20from%202024-12-30%2010-55-43.png)

### Example of Calling an EPP Template:

```puppet
$params = {
  'role'        => 'database',
  'server_name' => 'oracle01',
}

$output = epp('mymodule/welcome.epp', $params)
```

### Expected Template Path:

```
<modulepath>/mymodule/templates/welcome.epp
```

In the above example:

- `mymodule` is the module name.
- The template is located in the `templates` directory of the module.

---

## Template Tags

Templates support three types of tags for embedding Puppet or Ruby logic:

1. **Output Tag `<%= ... %>`**
    
    - Outputs the result of the expression.
    - Example:
        
        ```epp
        Hello, <%= $name %>!
        ```
        
2. **Code Tag `<% ... %>`**
    
    - Executes logic without producing output.
    - Example:
        
        ```epp
        <% if $os == 'Linux' -%>
        Welcome to Linux!
        <% end -%>
        ```
        
3. **Comment Tag `<%# ... %>`**
    
    - Adds comments that are ignored in the output.
    - Example:
        
        ```epp
        <%# This comment will not appear in the generated file %>
        ```
        

---

## Handling Blank Lines

To prevent blank lines in the output, use a trailing `-` in the tags:

- Without `-`:
    
    ```epp
    <% if $condition %>
    Content here
    <% end %>
    ```
    
    **Output**: Includes a blank line.
    
- With `-`:
    
    ```epp
    <% if $condition -%>
    Content here
    <% end -%>
    ```
    
    **Output**: No blank line.
    

---

## Dynamic File Content with Templates

Templates are often used to create dynamic configuration files or other text-based outputs.

### Example: Using an EPP Template to Generate `/etc/motd`

#### Manifest:

```puppet
class motd {
  $params = {
    'os_name'     => $facts['os']['name'],
    'os_major'    => $facts['os']['release']['major'],
    'os_minor'    => $facts['os']['release']['minor'],
    'server_name' => $trusted['certname'],
  }

  file { '/etc/motd':
    ensure  => file,
    content => epp('motd/motd.epp', $params),
    owner   => 'root',
    group   => 'root',
    mode    => '0644',
  }
}
```

#### Template (`motd.epp`):

```epp
<% | String $os_name, String $os_major, String $os_minor, String $server_name | -%>
Welcome to Puppet-managed system!

Server Name: <%= $server_name %>
Operating System: <%= "${os_name} ${os_major}.${os_minor}" %>
```

### Resulting `/etc/motd`:

```
Welcome to Puppet-managed system!

Server Name: agent.localdomain
Operating System: Ubuntu 22.04
```

---

## Recommended Module Layout

To organize templates effectively, use the following directory structure for your module:

```
mymodule/
├── manifests/
│   └── init.pp          # Manifest file for the module
├── templates/
│   └── welcome.epp      # Template file
├── files/               # Static files (if any)
├── examples/            # Example manifests (optional)
└── metadata.json        # Module metadata
```

---

## Additional Notes

- **ERB Templates**: Use `template()` function instead of `epp()`:
    
    ```puppet
    file { '/etc/motd':
      ensure  => file,
      content => template('mymodule/motd.erb'),
    }
    ```
    
- **EPP Advantage**: Supports type validation in parameters for better error handling.
    

---
