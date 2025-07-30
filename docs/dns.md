# Make systemd-resolved not occupy port 53

1.
```
sudo mkdir -p /etc/systemd/resolved.conf.d
```
2.
```
sudo tee /etc/systemd/resolved.conf.d/no-stub.conf <<EOF
[Resolve]
DNSStubListener=no
EOF
```
3. Enable pi-hole for dns
```
sudo tee /etc/systemd/resolved.conf.d/pi-hole.conf <<EOF
[Resolve]
DNS=127.0.0.1
FallbackDNS=
EOF
```

4. 
```
sudo systemctl daemon-reload
```
5.
```
sudo systemctl restart systemd-resolved
```