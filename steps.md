# steps to get k8s cluster on digital ocean

## get dependencies

* `brew install kubectl`
* `brew install doctl`
* `brew install terraform`
* `brew instal cfssl`
* `brew install stern`

## import ssh keys into digital ocean

either use existing or create new

`doctl compute ssh-key import k8s-ssh --public-key-file
~/.ssh/id_rsa.pub`

get key id from digitalocean
SSH_ID=`doctl compute ssh-key list | grep "k8s-ssh" | cut -d' ' -f1`

get fingerprint for key
SSH_KEY=`doctl compute ssh-key get $SSH_ID --format FingerPrint --no-header`

## run terraform
terraform apply
