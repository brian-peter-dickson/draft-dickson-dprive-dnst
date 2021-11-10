%%%
title = "Resource Record for Signaling Transport for DNS to Authority Servers"
abbrev = "DNS Transport"
docName = "draft-dickson-dprive-dnst"
category = "info"

[seriesInfo]
name = "Internet-Draft"
value = "draft-dickson-dprive-dnst-00"
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

This document specifies an RRTYPE to signal explicit support for transport types for DNS service. This new RRTYPE is "DNST".
The available transports to signal are TCP and UDP on port 53 (DNS), and DoT (DNS over TLS) transport using TCP port 853.

{mainmatter}
{{README.md}}
{backmatter}


# Acknowledgments

Thanks to everyone who helped create the tools that let everyone use Markdown to create 
Internet Drafts, and the RFC Editor for xml2rfc.

Thanks to Dan York for his Tutorial on using Markdown (specificially mmark) for writing IETF drafts.

Thanks to YOUR NAME HERE for contributions, reviews, etc.
