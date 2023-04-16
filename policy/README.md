### Get ODIC Provider

```bash
aws eks describe-cluster --name tekton-cluster --query "cluster.identity.oidc.issuer" --output text
```

### Verify OIDC Provider

```bash

//Linux
aws iam list-open-id-connect-providers | grep <ID of the oidc provider>

//Windows
aws iam list-open-id-connect-providers | findstr <ID of the oidc provider>

```

### Create IAM Policy

```bash
aws iam create-role --role-name AmazonEKS_EBS_CSI_Driver --assume-role-policy-document file://"trust-policy.json"
```

### Attach IAM Policy

```bash
aws iam attach-role-policy --policy-arn arn:aws:iam::aws:policy/service-role/AmazonEBSCSIDriverPolicy --role-name AmazonEKS_EBS_CSI_Driver
```

### Deploy the Amazon EBS CSI driver

```bash
aws eks create-addon --cluster-name my-cluster --addon-name aws-ebs-csi-driver --service-account-role-arn arn:aws:iam::
YOUR_AWS_ACCOUNT_ID:role/AmazonEKS_EBS_CSI_Driver
```