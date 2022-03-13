# Route-53-domain-level-hosted-zone-using-IAM-user
Allowing access to specific hosted zones with Route 53 and IAM Route 53 - Hosted zone domain level restriction using IAM POLICY

![](https://i.ibb.co/rcgRtSd/hosted-drawio.png)

# Description
-------------------------------------------------- 

Amazon Route 53 is a highly available and scalable cloud [Domain Name System (DNS)](https://aws.amazon.com/route53/what-is-dns/) web service. It is designed to give developers and businesses an extremely reliable and cost effective way to route end users to Internet applications by translating names like www.example.com into the numeric IP addresses like 192.0.2.1 that computers use to connect to each other. Amazon Route 53 is fully compliant with IPv6 as well.

A hosted zone is an Amazon Rote 53 concept. A hosted zone is analogous to a traditional DNS zone file; it represents a collection of records that can be managed together, belonging to a single parent domain name. All resource record sets within a hosted zone must have the hosted zone's domain name as a suffix.


# Pre-requisites:
-------------------------------------------------- 

#### Step 1: After logging in to the [Amazon console](https://console.aws.amazon.com/iamv2/home?#/policies), create a policy for the user. You can check more information regarding the IAM policy [here](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html)

#### Step2: [Create an user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html) after access [IAM user console](https://console.aws.amazon.com/iamv2/home?#/users) and then attach the previously created policy to this user.

IAM Policy
-------------------------------------------------- 

### Policy i have created for the John user to manage the www.google.com domain using IAM :


```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "route53:GetHostedZone",
                "route53:ChangeResourceRecordSets",
                "route53:ListResourceRecordSets"
            ],
            "Resource": "arn:aws:route53:::hostedzone/<Hosted zone ID of domain from route 53>"
        },
        {
            "Sid": "VisualEditor1",
            "Effect": "Allow",
            "Action": [
                "route53:ListHostedZones",
                "route53:GetHostedZoneCount",
                "route53:ListHostedZonesByName"
            ],
            "Resource": "*"
        }
    ]
}
```


> In the above Rosource section, replace the resource's hosted zone ID for your domain. In my case "Resource": "arn:aws:route53:::hostedzone/Z06144853TPKZNO30IBQX"


Please access your domain hosted zone dashboard and you will get the hosted zone ID, please check following image more infomration regarding the hosted zone ID

![](https://i.ibb.co/Zfb9C7Y/image.png)


## Conclusion

This article explains how to allow access to specific hosted zones with Route 53 and IAM Route 53 - Hosted zone domain level restriction using IAM POLICY. Thank you!

### ⚙️ Connect with Me
<p align="center">
<a href="https://www.instagram.com/iamvyjith/"><img src="https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white"/></a>
<a href="https://www.linkedin.com/in/vyjith-ks-3bb8b7173/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
