# mta-sts

MTA-STS setup for Care And Fly

## DNS Zone

``` dns
mta-sts.careandfly.eu. CNAME careandfly.github.io.
_mta-sts.careandfly.eu. TXT "v=STSv1; id=<UNIX_TIMESTAMP>"
```