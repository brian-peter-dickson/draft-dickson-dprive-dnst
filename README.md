# draft-dickson-dprive-svcb-dnst

### Prerequisite: New SVCB Binding for DNS and DoT

(NB: To be separated out into its own draft and expanded fully.)
This SVCB binding will be given the RRTYPE value {TBD} with mnemonic name DNST ("DNS Transport").
Like any SVCB binding, there is a mandatory TargetName (which will normally be ".", indicating the target is the same as the record owner name).
The default binding is the standard DNS ports, UDP/53 and TCP/53.

The SVCB binding includes support for an optional ADoT port, which is the standard DoT port TCP/853. This is signaled by "alpn=dot". The actual port number may be overridden with the "DOTport=N" SvcParam, and the UDP and TCP ports may also be overridden with optional "UDPport=N" and "TCPport=N" SvcParams.

Since DNST is a type-specific binding, it does NOT require the underscore prefix naming that the generic SVCB RRTYPE requires. It may occur anywhere, including at the apex of a DNS zone, and may co-exist with any other type that also permits other types.o

The DNST binding allows both AliasMode and ServiceMode record types (per the proposed SVCB standard). Both mode types use a TargetName parameter, which supports same-name usage (TargetName = ".") as well as redirected TargetName values. The resolver must follow AliasMode in the same manner as CNAME, i.e. rewriting the QNAME and restarting resolution using the new QNAME.

Once the DNST is in ServiceMode, the authoritative server returns both the DNST record(s) and A and AAAA records with the same owner name (TargetName). This reduces the number of queries the resolver would otherwise have to make (i.e. two additional queries for A and AAAA record types).

#### Default Ports for DNS

This scheme uses an SVCB binding for DNS Transport, DNST. The binding has default ports UDP/53 and TCP/53 as the default-alpn. These are assumed unless "no-default-alpn" is added as an optional SvcParam.

#### Optional Port for DoT

The DNST binding uses the defined ALPN for DNS-over-TLS with the assigned label "dot". Use of ADoT is signaled if and only if the the SvcParam of "alpn=dot" is present.


