# proxy-finder3
Python 3 library for sourcing proxy settings

Finds elite anonymity (L1) HTTP proxies then tests them all in parallel. Tests each proxy against 3 IP checking URLs including one which is HTTPS to make sure it can handle HTTPS requests. Then checks the proxy headers to confirm it's an elite L1 proxy that will not leak any extra info. By default the script will only print the proxy IP, request time, and country code of proxies that pass all four tests but you can see all the results including errors in any of the tests with the -a (--all) option. 

Requirements:
------
* Tested on Windows 10
* Python 3.6
  * asycio
  * aiohttp
  * beautifulsoup4
  * json
  * random

```
pip install beautifulsoup4
```

Usage:
------
```
    pf = ProxyFinder(gimme=0, freeproxylistuk=2, freeproxylistus=2)
    pprint(pf.list_of_proxies)
```

ProxyFinder creates an instance that retrieves proxy details from the sources provided. The default is one from each source:
```
__init__(self, gimme=1, freeproxylistuk=1, freeproxylistus=1)
```

If the source is a table of many proxy urls, it will scrape the whole table but only return the number of results requested.

The results will be a list of dictionaries, providing the ip, port and url source

```
 {'ip': '46.101.72.53',
  'port': '8118',
  'source': 'https://free-proxy-list.net/uk-proxy.html'},
 {'ip': '50.2.64.206',
  'port': '7808',
  'source': 'https://free-proxy-list.net/us-proxy.html'},
 {'ip': '173.213.113.111',
  'port': '8089',
  'source': 'https://free-proxy-list.net/us-proxy.html'}]
```

In the event of a proxy site hitting a limit, a dictionary will be returned with a message. Results for any other proxy requests will still be returned.
```
[{'Limit Exceeded': 'gimmeproxy'},
 {'ip': '139.59.168.33',
  'port': '8118',
  'source': 'https://free-proxy-list.net/uk-proxy.html'},
 {'ip': '173.213.113.111',
  'port': '8089',
  'source': 'https://free-proxy-list.net/us-proxy.html'}]
```


License
-------

Copyright (c) 2017, Lee Hayes
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:
* Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
* Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
* Neither the name of Lee Hayes nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL <COPYRIGHT HOLDER> BE LIABLE FOR ANY
DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.


***
* [wicket.me](http://wicket.me)
