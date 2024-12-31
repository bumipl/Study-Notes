## Introduction

Defined resources in Puppet allow you to create reusable resource blocks that encapsulate common configurations. These resources can be parameterized to enable dynamic behavior and tailored configurations. Unlike classes, defined resources are primarily used for creating instances of configurations, such as managing virtual hosts or specific directories. By using defined resources, you can:

- Simplify repetitive configurations.
- Reuse resource definitions across multiple nodes.
- Parameterize values for flexibility.

Defined resources are particularly helpful for modularizing configurations and keeping your manifests DRY (Don’t Repeat Yourself).

---

## Writing Defined Resource Types

A defined resource type is named using the convention `<module>::<name>`. For example, a defined resource named `apache::vhost` would be defined in the `apache` module with the `vhost` resource type.

Defined resource types must be placed in a manifest file within the `manifests` directory of the module. The filename should match the name of the resource type. For example:

### Example Structure

A defined resource `apache::vhost` would be defined in:

```
<modulepath>/apache/manifests/vhost.pp
```

### Example: Defining `apache::vhost`

```puppet
# apache/manifests/vhost.pp
define apache::vhost (
  Variant[String, Integer] $port,
  String $docroot,
) {
  # Create the virtual host configuration file
  file { "/etc/httpd/conf.d/vhost_${name}.conf":
    ensure  => file,
    owner   => 'root',
    group   => 'root',
    content => epp('apache/vhost.epp', {
      'port'        => $port,
      'docroot'     => $docroot,
      'server_name' => $name,
    }),
  }

  # Ensure the document root directory exists
  file { $docroot:
    ensure => directory,
    owner  => 'root',
    group  => 'root',
  }
}
```

In the example above:

- The `apache::vhost` resource is parameterized with `$port` and `$docroot`.
- The `$name` variable is automatically available within defined resources and represents the title of the resource declaration.
- The `content` attribute uses an Embedded Puppet (EPP) template to generate the configuration file dynamically.

---

## Declaring a Defined Resource

Defined resources are declared similarly to native Puppet resources, using resource declaration syntax. Each instance of the resource is identified by a unique title.

### Example: Declaring `apache::vhost`

#### `site.pp`

```puppet
node "agent.localdomain" {
  # Include the Apache class
  class { 'apache':
    port    => 8080,
    docroot => '/var/www/html',
  }

  # Declare multiple virtual hosts using apache::vhost
  apache::vhost { 'acme.com':
    port    => 80,
    docroot => '/var/www/acme.com',
  }

  apache::vhost { 'foo.com':
    port    => 80,
    docroot => '/var/www/foo.com',
  }

  apache::vhost { 'tango.com':
    port    => 80,
    docroot => '/var/www/tango.com',
  }
}
```

Here:

- The `apache` class is declared to manage the global Apache configuration.
- Three instances of the `apache::vhost` defined resource are declared for different virtual hosts.

---

## Example File Structure

The following directory structure corresponds to the `apache` module:

```bash
apache/
├── files
│   └── index.html
├── manifests
│   ├── init.pp
│   └── vhost.pp
└── templates
    ├── httpd.conf.epp
    └── vhost.epp
```

### File Breakdown

- **`manifests/vhost.pp`**: Contains the `apache::vhost` defined resource type.
- **`templates/vhost.epp`**: Embedded Puppet (EPP) template for generating virtual host configuration files.
- **`files/index.html`**: Static file that can be used as the default web page.

---

## Example Template: `vhost.epp`

EPP templates allow dynamic content generation based on variables passed from the defined resource.

```epp
<% |
  Variant[String, Integer] $port,
  String $docroot,
  String $server_name
| %>

<VirtualHost *:<%= $port %>>
  ServerName <%= $server_name %>
  DocumentRoot <%= $docroot %>
</VirtualHost>
```

In this template:

- The `port`, `docroot`, and `server_name` variables are used to generate the `<VirtualHost>` block dynamically.
- These variables are passed from the `apache::vhost` resource.

---

## Variable Declaration

Variables in Puppet can be declared at different levels depending on their purpose and scope:

### Site-Level Variables

Variables that apply globally or to specific nodes are defined in the `site.pp` file.

#### Example: `site.pp`

```puppet
node "agent.localdomain" {
  $default_docroot = '/var/www/html'

  apache::vhost { 'example.com':
    port    => 80,
    docroot => $default_docroot,
  }
}
```

### Manifest-Level Variables

Variables specific to a module or class can be defined within manifest files.

#### Example: `manifests/vhost.pp`

```puppet
define apache::vhost (
  String $docroot = '/var/www/html',
) {
  file { $docroot:
    ensure => directory,
    owner  => 'root',
    group  => 'root',
  }
}
```

### Template-Level Variables

Variables passed to templates are declared in the EPP template file and must match the names of variables passed from the manifest.

#### Example: `templates/vhost.epp`

```epp
<% |
  Variant[String, Integer] $port,
  String $docroot,
  String $server_name
| %>

<VirtualHost *:<%= $port %>>
  ServerName <%= $server_name %>
  DocumentRoot <%= $docroot %>
</VirtualHost>
```

---

## Additional Tips

1. **Testing Defined Resources**: Use `puppet apply` with a test manifest to verify the behavior of your defined resource.
    
    ```bash
    puppet apply -e "apache::vhost { 'test.com': port => 8080, docroot => '/var/www/test.com' }"
    ```
    
2. **Error Handling**: Ensure that variables passed to defined resources are validated with proper data types. Use Puppet’s data type system for stricter validation.
    
3. **Hiera Integration**: Use Hiera to provide values for variables, enabling environment-specific configurations without modifying code.
    

---

Defined resources in Puppet provide a powerful mechanism for creating reusable and modular configurations. By adhering to best practices and leveraging tools like templates and Hiera, you can simplify and scale your infrastructure automation efficiently.