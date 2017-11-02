# KodeNet IRC: TLS
Connect securely to Kode IRC with `irssi` or `weechat`

> TLS connections are accepted on port 6697

## Irssi
`/server add -auto -tls -tls_verify -network kodenet -port 6697 irc.koderoot.net`

### client certificates (optional)
```
openssl req -newkey rsa:2048 -days 3650 -x509 -keyout kodenet.key -out kodenet.crt -nodes
cat kodenet.crt kodenet.key > ~/.irssi/ssl/kodenet.pem
chmod 600 ~/.irssi/ssl/kodenet.pem
rm kodenet.crt kodenet.key
```

`/server add -tls_cert ~/.irssi/ssl/kodenet.pem -auto -tls -tls_verify -network kodenet -port 6697 irc.koderoot.net`

### TLS cetificate fingerprint
`openssl x509 -sha1 -fingerprint -noout -in ~/.irssi/ssl/kodenet.pem | sed -e 's/^.*=//;s/://g;y/ABCDEF/abcdef/'`

## WeeChat
[WeeChat Resource](https://weechat.org/files/doc/devel/weechat_faq.en.html#irc_ssl_handshake_error)

### Linux
`/set weechat.network.gnutls_ca_file "/etc/ssl/certs/ca-certificates.crt"`

### macOS
`/set weechat.network.gnutls_ca_file "/usr/local/etc/openssl/cert.pem"`
