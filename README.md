# Introduction

# Conventions and Definitions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in BCP 14 [@RFC2119] [@!RFC8174]
when, and only when, they appear in all capitals, as shown here.

# Background

DNS over TLS is defined in FIXME. However, there is no explicit signaling for when DoT should be used. Without explicit signaling, there is no protection against downgrade attacks by an on-path attacker.

# Remove Before Publication
Notes on design decisions, including the decision NOT to use an SVCB-compatible format:

* NS records MUST point to non-CNAME records. Thus, there is no need for the SVCB "Alias-form" behavior. DNST does not support aliasing,
* DNST allows for explicit rejection of default transport (UDP/53 and TCP/53)
* DNST allows explicit signaling of DoT
* There is no need for alternate port numbers for UDP or TCP port 53, or for DoT port 853.
* There is no need for DoH, since the expected clients are limited to DNS resolvers.

# DNS Transport RRTYPE
The solution to this problem is to introduce a method for explicit signaling for when DoT is available. When combined with TLSA records for the corresponding DNS server name, any client wishing to use DoT is able to know that it is available, and can detect and avoid any attempts at transport downgrade.

This document defines the RRTYPE value {TBD} with mnemonic name DNST ("DNS Transport").
This consists of a set of flags indicating supported transport for the DNS server at the owner name.
The flag bits represent transports UDP on port 53, TCP on port 53, and DoT (DNS over TLS on port 853).

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

# IANA Considerations

IANA is directed to add a new record to the DNS RRTYPES table to add the entry "DNST" with value "TBD", referencing this document.
