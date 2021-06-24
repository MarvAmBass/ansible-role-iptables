# Ansible Role: iptables

with this role you can setup your `iptables` firewall.

It brings support for `ipv4` and `ipv6` configuration, using configuration files for each host, grouping and also raw
configuration using variables.

It can restart your docker daemon, to fix all exposed ports.

## Configuration Variables

You can use several Variables to configure this role.

### Variables with predefined default value

- `restart_docker` - (default: `false`) restarts docker daemon, so it will recreate all exposed ports etc.

- `firewall_ipv4_groups` - list of all `ipv4` groups we want to apply
- `firewall_ipv6_groups` - list of all `ipv6` groups we want to apply

- `raw_ipv4_rules` - list of custom `ipv4` rules to apply
- `raw_ipv6_rules` - list of custom `ipv6` rules to apply

## Configuration Templates

If you want to create a new group with defined rules for you to use, just add a new `*.j2` file beneath `templates/group/$VERSION/`, after this you can use this with the `firewall_ipvX_groups` variable.

If you have host specific rules, you can also add those rules to a file `$HOSTNAME.j2` beneath `templates/hosts/$VERSION/` and it
gets automatically applied to the specific host with this name.