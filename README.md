# mock-wp-pulumi

Mock project that deploys WordPress on AWS using Pulumi.

## Resources Deployed

```
     Type                                 Name                                 Plan       
 +   pulumi:pulumi:Stack                  mock-wp-dev                          create     
 +   ├─ custom:resource:VPC               mock-wp-net                          create     
 +   │  ├─ aws:ec2:Vpc                    mock-wp-net-vpc                      create     
 +   │  ├─ aws:ec2:Subnet                 mock-wp-net-subnet-eu-central-1a     create     
 +   │  ├─ aws:ec2:InternetGateway        mock-wp-net-igw                      create     
 +   │  ├─ aws:ec2:SecurityGroup          mock-wp-net-fe-sg                    create     
 +   │  ├─ aws:ec2:Subnet                 mock-wp-net-subnet-eu-central-1b     create     
 +   │  ├─ aws:ec2:SecurityGroup          mock-wp-net-rds-sg                   create     
 +   │  ├─ aws:ec2:RouteTable             mock-wp-net-rt                       create     
 +   │  ├─ aws:ec2:RouteTableAssociation  vpc-route-table-assoc-eu-central-1a  create     
 +   │  └─ aws:ec2:RouteTableAssociation  vpc-route-table-assoc-eu-central-1b  create     
 +   ├─ random:index:RandomPassword       db_password                          create     
 +   ├─ custom:resource:Backend           mock-wp-be                           create     
 +   │  ├─ aws:rds:SubnetGroup            mock-wp-be-sng                       create     
 +   │  └─ aws:rds:Instance               mock-wp-be-rds                       create     
 +   └─ custom:resource:Frontend          mock-wp-fe                           create     
 +      ├─ aws:ecs:Cluster                mock-wp-fe-ecs                       create     
 +      ├─ aws:iam:Role                   mock-wp-fe-task-role                 create     
 +      ├─ aws:lb:TargetGroup             mock-wp-fe-app-tg                    create     
 +      ├─ aws:iam:RolePolicyAttachment   mock-wp-fe-task-policy               create     
 +      ├─ aws:lb:LoadBalancer            mock-wp-fe-alb                       create     
 +      ├─ aws:lb:Listener                mock-wp-fe-listener                  create     
 +      ├─ aws:ecs:TaskDefinition         mock-wp-fe-app-task                  create     
 +      └─ aws:ecs:Service                mock-wp-fe-app-svc                   create     
 ```