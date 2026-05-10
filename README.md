# [dnstap-gael](https://snapcraft.io/dnstap-gael)

dnstap implements an encoding format for DNS server events. It uses a
lightweight framing on top of event payloads encoded using Protocol Buffers and
is transport neutral.

dnstap can represent internal state inside a DNS server that is difficult to
obtain using techniques based on traditional packet capture or unstructured
textual format logging.

**Usage**

`dnstap-gael.dnstap --help`

**Example using Knot Resolver [knot-resolver-gael](https://snapcraft.io/knot-resolver-gael)**

`sudo snap connect dnstap-gael:home :home`

`sudo snap connect knot-resolver-gael:home :home`

`sudo dnstap-gael.dnstap -q -u /root/dnstap.sock`

`sudo vi /var/snap/knot-resolver-gael/current/kresd.conf`

```
   modules = {
       dnstap = {
           socket_path = "/root/dnstap.sock",
           identity = "",
           version = package_version(),
           client = {
               log_queries = true,
               log_responses = true,
           },
       }
   }
```

`sudo snap restart knot-resolver-gael.kresd`

**2026-05-10**
* Go updated to v1.26.2

**2024-11-17**
* Switched to core24 to follow knot-resolver-gael

**2021-08-16**
* v0.4.0 available on amd64, arm64 & armhf
