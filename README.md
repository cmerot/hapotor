HAproxy + Polipo + Tor = Hapotor
=============================================================================

I used to use [mattes/rotating-proxy][https://github.com/mattes/rotating-proxy]
before creating this repo. Config and ideas come from there.

Synopsis
-----------------------------------------------------------------------------

Anonymous and cache proxy with rotating IPs

    Polipo:5567 --> HAProxy:5566 --> Polipo:20001 --> Tor:10001
                                 --> Polipo:20002 --> Tor:10002
                                 --> etc ...

Install
-----------------------------------------------------------------------------

Install system dependencies:

    $ `bin/install-dependencies.sh`.

Deploy upstart jobs with the script `bin/deploy-hapotor.sh`:

    $ ./bin/deploy-hapotor.sh 20

Manage upstart jobs with the script `bin/hapotor.sh`

    $ ./bin/hapotor.sh {status|start|stop|restart}

Usage
-----------------------------------------------------------------------------

Use without cache:

    $ curl --proxy localhost:5566 http://echoip.com

Use with cache (to use a geocoding API for instance):

    $ curl --proxy localhost:5567 http://echoip.com