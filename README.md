# aws-metadata-json

## What it does
- Query the metadata of an ec2 instance within AWS and provide a json formatted output. 
- Retrieve the value of a particular data key.

## How to install
- [Create an EC2 Linux instance on AWS](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html)
- [SSH into the instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html)
- Install Python 3 and git on your ec2 instance 
    - `sudo yum install python3 git`
- Clone this repository in your ec2 instance
  - `git clone https://github.com/bluprince13/aws-metadata-json`
- Install pipenv in your ec2 instance
  - `sudo pip3 install pipenv`
  - `sudo pip3 install requests`
- Open the repository on your instance
  - `cd get-aws-metadata`
- Install project dependancies
  - `pipenv install`


## How to run
- Open the `src` folder
  - `cd get-aws-metadata/src`
- Run whichever script you need:
  - `python3 get_metadata.py`
  - `python3 get_key.py` : this will ask which metadata key you want to retrieve.
  - example fields to provide as input are ami-id
ami-launch-index
ami-manifest-path
block-device-mapping/
events/
hostname
iam/
instance-action
instance-id
instance-life-cycle
instance-type
local-hostname
local-ipv4
mac
metrics/
network/
placement/
profile
public-hostname
public-ipv4
public-keys/
reservation-id
security-groups
services/

## How it works
- It makes use of the http://169.254.169.254/latest/meta-data link-local address. Instance metatada is provided at this link, but only when you visit it from a running instance.
- A few simple Python scripts are used to extract the required information using the above API.
- See [AWS user guide](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html) for more info on the instance metadata API.
