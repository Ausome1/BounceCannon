# BounceCannon
A tool to remotely control a relay to hide where downloads are coming from.

# Requirements:
1. PHP
2. SOCAT

# How to use?
Start a PHP server is one isn't already running:
PHP -S 0.0.0.0:8080

Load bounce-cannon:
curl --data "load=[bounce to domain/ip]" [url to bounce-cannon]
ex: curl --data "load=10.1.2.3" http://1.2.3.4:8080/bounce-cannon.php
ex: curl --data "load=example.com" http://localhost:8080/bounce-cannon.php

Unload bounce-cannon:
curl --data "unload" [url to bounce-cannon]
ex: curl --data "unload" http://1.2.3.4:8080/bounce-cannon.php

Remotely delete bounce-cannon:
curl --data "kill" [url to bounce-cannon]
ex: curl --data "kill" http://1.2.3.4:8080/bounce-cannon.php

# Some caveats:
1. Socat does a DNS lookup before the relay. So if you use "load=example.com" the relay will connect to the IP instead. If you can't access the same files visiting http://example.com/some-directory as http://1.2.3.4/some-directory, you won't see your files.
2. Some main domains use frame buster code. This will cause the relay to redirect to the hidden domain in the URL, defeating the purpose of hiding the files. You can still use domains like this just make sure to append /some-directory the domain in the URL that doesn't have frame buster code.
