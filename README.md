# AWS-via-WSL2

Install wsl from Command Promt or PowerShell <br>
restart computer and confirm installation<br>
```
wsl --install
wsl.exe -l -v
```
![image](https://github.com/qaswarh/AWS-via-WSL2/assets/47313728/7f578c50-ec27-45b0-835d-ad841110a0cf)

Follow https://us-east-1.console.aws.amazon.com/iamv2/home#/users/details/${user}?section=security_credentials to create access key<br>
Replace ${user} with the AWS user<br>
Configure aws with access key credentials and suitable region<br>
```php
sudo apt-get update
sudo apt install python3-pip
sudo pip3 install awscli
aws configure
```
Check users<br>

![image](https://github.com/qaswarh/AWS-via-WSL2/assets/47313728/cfe07e67-9dab-462d-b0c8-eb9988b9763c)

WSL2 is now AWS CLI ready<br>

![image](https://github.com/qaswarh/AWS-via-WSL2/assets/47313728/1e10a2f0-aeef-44a2-af1b-ea18ff7cb114)

![image](https://github.com/qaswarh/AWS-via-WSL2/assets/47313728/872ad8db-ab7a-41c1-9328-4afadd8aa488)




