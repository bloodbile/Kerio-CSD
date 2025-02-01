# 🎀 Kerio-CSD 🎀
## Overview
A client-side desynchronization (CSD) vulnerability has been discovered in the Kerio Connect Client, presenting a critical security risk by allowing attackers to exploit the server's handling of POST requests. This vulnerability can potentially lead to cross-site scripting (XSS) attacks, compromising user data and application integrity.
## Details
The vulnerability arises from the server's incorrect processing of the Content-Length in POST requests. During testing, a POST request was sent to the path '/webmail/generatedDefaults.js' with an additional request embedded within its body. The server responded prematurely, before the entire request body was transmitted, and did not close the connection afterward. This flaw may lead to the embedded smuggled request being treated as the following legitimate request. As demonstrated, this behavior opens the door for exploitation, where an attacker can manipulate the victim's browser to desynchronize its connection with the Kerio Connect Client.

[Request #1](request1.txt)/[Response #1](response1.txt)</br>
[Request #2](request2.txt)/[Response #2](response2.txt)
## Understanding Client-side Desync Attacks
Client-side desync vulnerabilities occur when a web server fails to appropriately manage the Content-Length of incoming POST requests. By leveraging this oversight, an attacker can craft a malicious request that, when processed, causes the victim's browser to interpret the desynchronized request as part of its legitimate interaction with the server. This can lead to the execution of arbitrary JavaScript code within the context of the victim's session, posing serious risks to user security and data integrity.
