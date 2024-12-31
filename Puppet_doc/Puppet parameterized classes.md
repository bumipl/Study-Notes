# Documentation: Parameterized Classes in Puppet

## Introduction

Parameterized classes in Puppet allow you to create reusable, sharable components by providing flexibility through parameters. They enable better control over configuration and make it easier to define resources dynamically. By using parameterized classes, you can avoid hardcoding values and instead pass variables into classes to customize their behavior for different nodes or environments.

### Key Benefits

- **Reusability**: Parameterized classes can be reused across multiple nodes or projects.
- **Flexibility**: Allows dynamic customization through parameters.
- **Maintainability**: Makes Puppet manifests cleaner and easier to maintain.
- **Data Encapsulation**: Ensures a clear separation between logic and data.

---

## Variables in Classes

Variables in parameterized classes are defined as class parameters. These parameters can have default values or be explicitly specified when declaring the class.

### Example:

```puppet
class apache (
  Integer $port = 80,
  String $docroot = '/var/www/html'
) {
  file { '/etc/httpd/conf/httpd.conf':
    ensure  => file,
    content => epp('apache/httpd.conf.epp', {
      'port'    => $port,
      'docroot' => $docroot,
    }),
  }

  service { 'httpd':
    ensure => running,
    enable => true,
  }
}
```

In the example above, `$port` and `$docroot` are parameters with default values. These can be overridden when declaring the class.

---

## Transferring Variables from Class to Parameterized Class

When transitioning from a simple class to a parameterized class, you replace hardcoded variables with parameters, making the class more flexible.

### Example: Before and After

#### Non-Parameterized Class

```puppet
class apache {
  $port = 80
  $docroot = '/var/www/html'

  file { '/etc/httpd/conf/httpd.conf':
    ensure  => file,
	content => epp('apache/httpd.conf.epp', {
      'port'    => $port,
      'docroot' => $docroot,
    })
}
```

#### Parameterized Class

```puppet
class apache (
  Integer $port = 80,
  String $docroot = '/var/www/html'
) {
  file { '/etc/httpd/conf/httpd.conf':
    ensure  => file,
    content => epp('apache/httpd.conf.epp', {
      'port'    => $port,
      'docroot' => $docroot,
    })
}
```

The second example allows `$port` and `$docroot` to be overridden when the class is declared.

---

## Declaring a Class

You can declare a parameterized class using either of the following methods:

### Method 1: `include`

The `include` function does not allow you to pass parameters. It uses the class’s default parameter values or parameters specified in Hiera.

#### Example:

```puppet
include apache
```

### Method 2: Resource Declaration Syntax

This method allows you to pass parameters directly.

#### Example:

```puppet
class { 'apache':
  port    => 8080,
  docroot => '/var/www/custom',
}
```

---

## Parameter Defaults

Parameters can have default values, which are used if no value is explicitly provided when the class is declared.

### Example:

```puppet
class apache (
  Integer $port = 80,
  String $docroot = '/var/www/html'
) {
  notice("Apache will listen on port ${port} and serve files from ${docroot}.")
}

class { 'apache': }
# Outputs: Apache will listen on port 80 and serve files from /var/www/html.
```

If a value is passed during declaration, it will override the default:

```puppet
class { 'apache':
  port => 8080,
}
# Outputs: Apache will listen on port 8080 and serve files from /var/www/html.
```

---

## Data Type Validation

In modern Puppet, you can enforce strict data type validation for class parameters. This helps ensure the parameters are used correctly and avoids runtime errors.

### Example:

```puppet
class apache (
  Integer $port,
  String $docroot,
  Optional[Boolean] $ssl = false
) {
  if $ssl {
    notice("SSL is enabled on port ${port}.")
  } else {
    notice("Non-SSL server running on port ${port}.")
  }
}
```

If a parameter does not match the specified data type, Puppet will throw an error.

---

## Layout

For parameterized classes to function properly, the module layout should adhere to Puppet’s standard directory structure:

```
<module_root>/
├── manifests/
│   └── init.pp        # Contains the main parameterized class
├── templates/
│   └── httpd.conf.epp # Example template file
└── files/
    └── index.html     # Example static file
```

### Example `init.pp` File

```puppet
class apache (
  Integer $port = 80,
  String $docroot = '/var/www/html'
) {
  file { '/etc/httpd/conf/httpd.conf':
    ensure  => file,
    content => epp('apache/httpd.conf.epp', {
      'port'    => $port,
      'docroot' => $docroot,
    }),
  }

  service { 'httpd':
    ensure => running,
    enable => true,
  }

  file { $docroot:
    ensure => directory,
  }
}
```

---

## Additional Considerations

- **Integration with Hiera**: Parameters can be overridden with values from Hiera for environment-specific configurations.
- **Testing and Debugging**: Use `puppet apply` with different parameter values to ensure the class behaves as expected.
- **Documentation**: Always document your parameterized classes for clarity and maintainability.

---

Parameterized classes in Puppet are a powerful feature for building flexible and reusable modules. By combining them with data type validation, default values, and Hiera integration, you can create robust automation solutions that scale effectively across diverse environments.