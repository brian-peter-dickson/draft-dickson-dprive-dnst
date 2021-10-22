%%%
title = "Service Binding for DNS over TLS to Authority Servers"
abbrev = "Service Binding for ADoT"
docName = "draft-dickson-dprive-svcb-dnst"
category = "info"

[seriesInfo]
name = "Internet-Draft"
value = "draft-dickson-dprive-svcb-dnst-00"
stream = "IETF"
status = "standard"


ipr = "trust200902"
area = "Operations"
workgroup = "DPRIVE Working Group"
keyword = ["Internet-Draft"]

[pi]
toc = "yes"
sortrefs = "yes"
symrefs = "yes"
stand_alone = "yes"

[[author]]
initials = "B."
surname = "Dickson"
fullname = "Brian Dickson"
organization = "GoDaddy"
  [author.address]
  email = "brian.peter.dickson@gmail.com"

%%%


.# Abstract

This Internet Draft proposes a service binding for DNS transport types. A new RRTYPE "DNST" is used which is an instance of the SVCB type.
The service binding includes optional parameters for use of the DoT (DNS over TLS) transport using TCP port 853, and default transports of TCP and UDP on port 53 (DNS).

{mainmatter}
{{README.md}}
{backmatter}


# Mapping Summary

This table serves as a non-normative summary of the DNST mapping for SVCB.

|                                  |                                        |
| -------------------------------- | -------------------------------------- |
| **Mapped scheme**                | "dns"                                  |
| **RR type**                      | DNST (TBD)                             |
| **Name prefix**                  | `_dns` for port 53, else `_$PORT._dns` |
| **Required keys**                | `alpn`                                 |
| **Automatically Mandatory Keys** | `port`                                 |
| **Special behaviors**            | TBD                                    |


# Acknowledgments

Thanks to everyone who helped create the tools that let everyone use Markdown to create 
Internet Drafts, and the RFC Editor for xml2rfc.

Thanks to Dan York for his Tutorial on using Markdown (specificially mmark) for writing IETF drafts.

Thanks to YOUR NAME HERE for contributions, reviews, etc.
