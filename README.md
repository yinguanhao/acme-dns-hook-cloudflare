DNS verification hook for [acmetool](https://github.com/hlandau/acme) using cloudflare API.

## Usage


Download `dns.hook` to your server. Install dependencies: python 3, requests. You also need the `dig` program. On debian based systems it is available in the `dnsutils` package.

Allow only yourself to read/write/execute it:
```
$ chmod 700 dns.hook
```

Edit dns.hook, set EMAIL and KEY.

Test run:
```
$ ./dns.hook test [sub.yourdomain.tld]
```
The script will try to create a TXT record `_acme-challenge.[sub.yourdomain.tld]`, verify it, and delete it.

If it works, copy/move to acmetool hooks dir (e.g. `/usr/lib/acme/hooks/`):

```
$ sudo mv dns.hook /usr/lib/acme/hooks/
```
