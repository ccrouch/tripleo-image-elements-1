Provide configuration for seed clouds
-------------------------------------

Seed clouds are booted without any cloud infrastructure. The seed-stack-config
element stubs out enough infrastructure to permit the rest of boot-stack to
work either when booted by a cloud, or booted without.

In particular, it sets up resolv.conf, a hosts file, and delivers a Heat
metadata file with static data into the image (rather than that being delivered
at boot-time by Heat itself).

Usage
-----

Edit config.json to customise it for your deployment environment. The default
is configured for nova-baremetal operation in a seed VM. The configuration
options are documented in the actual elements that use the configuration - e.g.
nova, neutron etc.

Configuration keys
------------------

bootstack:
  public\_interface\_ip: 192.0.2.1/24
    - What IP address to place on the ovs public interface. Only intended for
      use when the interface will not be otherwise configured.
  masquerade\_networks: [192.0.2.0]
    - What networks, if any, to masquerade. When set, all traffic being
      output from each network to other networks is masqueraded. Traffic
      to 192.168.122.1 is never masqueraded.
