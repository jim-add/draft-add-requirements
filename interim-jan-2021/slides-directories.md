# Scenario 3: Directories of Encrypted Resolvers

Three Parties:
* Publisher: Curates a list of distinct resolvers
* Client: Fetches the list from a trusted source
* Resolvers: Identified in the list, ready for access by the client
------------------------------------------------
# Example use cases

* A browser vendor wants to provide users with a list of resolvers to consider, curated by a trusted third party
* An OS vendor wants to keep its list of trusted resolvers current without requiring a software update
* A network operator/manager wants to provide a list of resolvers to local devices/users (think DHCP on steroids but not necessarily using DHCP)
* A user wants to choose a resolver from a list offered by a network operator who they trust
* A user wants to select a resolver from a list determined by a third party (eg from an app-supplied list)
------------------------------------------------
# Requirements

* A list can be published by a trusted network
* A list can be published at an HTTP URL
* A signalling mechanism to describe resolver (protocol and policy) properties:
  eg DNSSEC or ECS support, DoH/DoT/DoQ/Do53, split DNS, filtering
* Each resolver controls its own self-description
* Suitable for use in an onscreen interactive menu
* Can be used as an additional safeguard for untrusted upgrade instructions
* Uses the same protocols as the previous scenarios
* Fail safe fallback(s) and least surprise if/when a suitable resolver isn't on the list
* Verification of list info (certs? DNSSEC?)
------------------------------------------------
# Non-requirements

* Defending against a malicious or inept publisher
  I disagree with this. Sorry. Clients will need to verify whatever the publisher is publishing. If not, why bother using their list at all?
* Defending against a malicious or inept resolver
* Support for extremely long lists (e.g. >1000 resolvers)
* Resolvers that are restricted to a subset of names (e.g. one CDN)
  Not sure about this either Ben - split DNS setups in enterprise nets?
* Grouping related resolvers
* Enable connection without use of a bootstrap resolver

