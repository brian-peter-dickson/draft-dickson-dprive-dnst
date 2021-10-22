# Introduction

Notes on design decisions, including the decision NOT to use an SVCB-compatible format:

* NS records MUST point to non-CNAME records. Thus, there is no need for the SVCB "Alias-form" behavior. DNST does not support aliasing,
* DNST allows for explicit rejection of default transport (UDP/53 and TCP/53)
* DNST allows explicit signaling of DoT
* There is no need for alternate port numbers for UDP or TCP port 53, or for DoT port 853.
* There is no need for DoH, since the expected clients are limited to DNS resolvers.

# draft-dickson-dprive-dnst

# Section-name
This defines the RRTYPE value {TBD} with mnemonic name DNST ("DNS Transport").
This consists of a set of flags indicating supported transport for the DNS server at the owner name.
The flag bits are UDP/53, TCP/53, and DoT (DNS over TLS on port 853).

# Restrictions
The DNST record may occur anywhere, including at the apex of a DNS zone, and may co-exist with any other type that also permits other types.

# Wire Format

The RDATA wire format is an 8-bit octet of flag bits.

```
| UDP | TCP | DOT | 5 unused bits |
```

# Presentation Format

    OWNER CLASS TTL DNST [UDP] [TCP] [DOT]

At least one of the transport types must be present.

# Additional Processing

The authoritative server MAY/SHOULD return both the DNST record(s) and any/all A and AAAA records with the same owner name. This reduces the number of queries the resolver would otherwise have to make (i.e. two additional queries for A and AAAA record types).

# Security Considerations

The DNST record MUST be in a DNSSEC-signed zone. This ensures protection against downgrade attacks on the transport signaling.
