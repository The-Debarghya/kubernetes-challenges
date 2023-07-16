1. Fix port in controlplane
2. check logs in `/var/logs/pods/` for kube-apiserver logs:

```
2023-07-16T02:06:52.105286015-04:00 stderr F I0716 06:06:52.105085       1 server.go:551] external host was not specified, using 192.7.169.6
2023-07-16T02:06:52.106246874-04:00 stderr F I0716 06:06:52.106155       1 server.go:165] Version: v1.27.0
2023-07-16T02:06:52.106256544-04:00 stderr F I0716 06:06:52.106199       1 server.go:167] "Golang settings" GOGC="" GOMAXPROCS="" GOTRACEBACK=""
2023-07-16T02:06:52.459607457-04:00 stderr F E0716 06:06:52.459455       1 run.go:74] "command failed" err="open /etc/kubernetes/pki/ca-authority.crt: no such file or directory"
```
3. Fix the directory
4. Uncordon node01
5. Fix coredns deployment to use `registry.k8s.io/coredns/coredns:v1.8.6` image.
6. Use `scp` to copy files from /media in controlplane to /web in node01
7. create from the manifests
8. k expose pod gop-file-server --name=gop-fs-service --port 8080
9. k edit svc gop-fs-service ... and use the nodeport