##Wordpress Stack for Kubernetes

Based on the example in Kubernete's repo.
https://github.com/kubernetes/kubernetes/tree/master/examples/mysql-wordpress-pd


##Setup Mysql Database Password Secret

Put your desired mysql password in a file called `password.txt` with
no trailing newline. The first `tr` command will remove the newline if
your editor added one.

```shell
tr --delete '\n' <password.txt >.strippedpassword.txt && mv .strippedpassword.txt password.txt
kubectl create secret generic mysql-pass --from-file=password.txt
```

##Create Persistent Volumes 
Mysql and Wordpress Containers need persistent volumes. This setup uses GlusterFS volumes since
it is running in Digital Ocean.



