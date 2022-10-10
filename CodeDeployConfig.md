
# Installing the CodeDeploy agent on EC2
```
sudo yum update -y
sudo yum install -y ruby wget
wget https://aws-codedeploy-eu-west-1.s3.eu-west-1.amazonaws.com/latest/install
chmod +x ./install
sudo ./install auto
sudo service codedeploy-agent status
```


# create a bucket and enable versioning
```
aws s3 mb s3://aws-devops-cicddemo-10082022 --region us-east-1 --profile cicd-user
aws s3api put-bucket-versioning --bucket aws-devops-cicddemo-10082022 --versioning-configuration Status=Enabled --region us-east-1 --profile cicd-user
```

# deploy the files into S3
```
aws deploy push --application-name cicd-Application --s3-location s3://aws-devops-cicddemo/codedeploy-demo/app.zip --ignore-hidden-files --region us-east-1 --profile cicd-user
```