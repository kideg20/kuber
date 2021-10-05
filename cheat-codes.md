- [1. Troubleshooting kubernetes cluster](#1-troubleshooting-kubernetes-cluster)
  - [1.1. AWS](#11-aws)
    - [1.1.1. check cni logs](#111-check-cni-logs)
# 1. Troubleshooting kubernetes cluster
## 1.1. AWS
login to EKS node. 
collect logs
copy logs to localmachine
delete collected logs
logout from eks node
```sh
ssh -i ~/.ssh/aws-mq-prod-eks.key ec2-user@10.240.21.152
sudo bash /opt/cni/bin/aws-cni-support.sh
exit
cd /tmp
mkdir analize_eks_logs
cd analize_eks_logs
scp -i ~/.ssh/aws-mq-prod-eks.key ec2-user@10.240.21.152:/var/log/eks_i-0c482b3e4edb7f2b3_2021-08-18_1035-UTC_0.6.2.tar.gz /tmp/analize_eks_logs
tar -xzvf eks_i-0c482b3e4edb7f2b3_2021-08-18_1035-UTC_0.6.2.tar.gz
ssh -i ~/.ssh/aws-mq-prod-eks.key ec2-user@10.240.21.152
sudo rm -rf /var/log/eks_i-0c482b3e4edb7f2b3_2021-08-18_1035-UTC_0.6.2.tar.gz
exit
```
If the script is not present at that location, then the CNI container failed to run. You can manually download and run the script with the following command:
```sh
curl -O https://raw.githubusercontent.com/awslabs/amazon-eks-ami/master/log-collector-script/linux/eks-log-collector.sh
```

### 1.1.1. check cni logs

var_log/aws-routed-eni/plugin.log
