# PacketFilter App (apps.packet_filter.packet_filter)

The `PacketFilter` app receives packets on the `input` port and transmits
conforming packets to the `output` port. In order to conform, a packet
must match at least one of the *filter rules* of the `PacketFilter`
instance and/or belong to a sanctioned connection.

![PacketFilter](.images/PacketFilter.png)

## Configuration

The `PacketFilter` app accepts a table as its configuration argument. The
following keys are available:

— Key **rules**

*Required*. A list of filter rules as described in the *Filter Rules*
section below.

— Key **state_track**

*Optional*. A string naming a connection table. If set, packets passing
_any_ rule will be tracked in the specified connection table.

— Key **state_check**

*Optional*. A string denoting a connection table. If set, any packet that
belongs to a tracked connection in the specified connection table will
be let pass.

### Filter Rules

A filter rule is a table in which each key/value pair specifies a pattern
to match or track incoming packets against. The following keys are
defined:

— Key **ethertype**

*Required*. The ethernet type in use (IPv4 or IPv6). A string identifier,
either "ipv4" or "ipv6".

— Key **protocol**

*Optional*. The protocol is use (ICMP, UDP or TCP). A string identifier,
may be one of "icmp", "udp" or "tcp".

— Key **source_cidr**

— Key **dest_cidr**

*Optional*. Source and destination addresses. IP ranges in CIDR notation
as strings.

— Key **source_port_min**

— Key **source_port_max**

*Optional*. The source port range. Integers denoting the minimum and
maximum source port numbers. If only one is set then only that port is
allowed.

— Key **dest_port_min**

— Key **dest_port_max**

*Optional*. The destination port range. Integers denoting the minimum and
maximum destination port numbers. If only one is set then only that port
is allowed.

— Key **state_track**

*Optional*. A string naming a connection table. If set, packets passing
the rule are tracked in the specified connection table.

— Key **state_check**

*Optional*. A string denoting a connection table. If set, packets must
belong to a tracked connection in the specified connection table in
addition to any other condition in the rule to pass.
