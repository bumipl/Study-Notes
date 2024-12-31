# Advanced Resource Declaration in Puppet

## Introduction

This document explains advanced techniques for declaring resources in Puppet 8, focusing on resource grouping, resource defaults, and dynamic attributes. These practices simplify Puppet manifests, improve readability, and reduce repetition.

---

## 1. Resource Grouping

Resource grouping allows you to declare multiple resources of the same type in a concise way, improving manifest structure and readability.

### Example 1: Grouping Virtual Hosts

The following `site.pp` declares several `apache::vhost` resources individually:

```puppet
node "agent.localdomain" {
  include motd

  class { 'apache':
    port    => 8080,
    docroot => '/var/www/html',
  }

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

With resource grouping, this can be rewritten as:

```puppet
node "agent.localdomain" {
  include motd

  class { 'apache':
    port    => 8080,
    docroot => '/var/www/html',
  }

  apache::vhost {
    'acme.com':
      port    => 80,
      docroot => '/var/www/acme.com';
    'foo.com':
      port    => 80,
      docroot => '/var/www/foo.com';
    'tango.com':
      port    => 80,
      docroot => '/var/www/tango.com';
  }
}
```

### Example 2: Managing Multiple Files

The following `advanced.pp` manages three files individually:

```puppet
file {
  '/etc/foo':
    ensure => file;
  '/etc/bar':
    ensure => file;
  '/etc/tango':
    ensure => file;
}
```

Using grouping, it becomes:

```puppet
file {
  '/etc/foo':
    ensure => file;
  '/etc/bar':
    ensure => file;
  '/etc/tango':
    ensure => file;
}
```

---

## 2. Resource Defaults

Resource defaults let you define default attributes for all resources of a specific type. This reduces duplication and ensures consistency.

### Example: Defining Defaults for Files

```puppet
File {
  owner => 'root',
  group => 'root',
  mode  => '0644',
}

file {
  '/etc/foo':
    ensure => file;
  '/etc/bar':
    ensure => file;
  '/etc/tango':
    ensure => file;
}
```

Here, the `File` block sets default `owner`, `group`, and `mode` for all `file` resources.

### Using Inline Defaults

You can also define defaults inline within the manifest:

```puppet
file {
  default:
    owner => 'root',
    group => 'root',
    mode  => '0722';

  '/etc/foo':
    ensure  => file,
    content => 'Hello foo';
  '/etc/bar':
    ensure  => file,
    content => 'Hello bar';
  '/etc/tango':
    ensure   => file,
    content => 'Hello tango';
}
```

---

## 3. Dynamic Attributes

Dynamic attributes allow you to define resource parameters programmatically, enhancing flexibility and reusability.

### Example: Using a Hash for Attributes

```puppet
$attrs = {
  'ensure' => 'file',
  'owner'  => 'root',
  'group'  => 'root',
  'mode'   => '0644',
}

file {
  default:
    * => $attrs;

  '/etc/foo':
    ensure  => file,
    content => 'Hello foo';
  '/etc/bar':
    ensure  => file,
    content => 'Hello bar';
  '/etc/tango':
    ensure   => file,
    content => 'Hello tango';
}
```

In this example, the `* => $attrs` syntax applies all key-value pairs from the `$attrs` hash to the default attributes of the `file` resource.

---

## Summary

These advanced resource declaration techniques in Puppet improve efficiency and maintainability:

1. **Resource Grouping** simplifies managing multiple resources of the same type.
2. **Resource Defaults** ensure consistent configuration across resources.
3. **Dynamic Attributes** provide programmatic flexibility for complex scenarios.

By adopting these practices, you can write cleaner, more scalable Puppet manifests that adapt well to evolving infrastructure needs.