# AWS IoT Console utility

This is a command line utility that helps you create IoT Things, ThingType and assign existing certificate in AWS. It can be use to easily provision your IoT device in AWS IoT.

## Requirements
- Python 3+
- PIP Package Manager
- AWS account

You need to have an existing aws config file in the machine you are running the tool. In linux systems, it can be found at ~/.aws/config. The content of the file looks something like this.


``` python
[profile main-profile]
region = ap-southeast-2
aws_access_key_id = AAAAAAAAAAAAAAAAAAAA
ws_secret_access_key = BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB
output = json 
```

```python
[profile development]
source_profile=main-profile
role_arn=arn:aws:iam::12345678999:role/Admin
region = us-east-1
output = json
s3 = signature_version = s3v4
```

### Setup

> $ pip install awsiot

#### Create new thing
```python
$ awsiot newthing MyNewThing -a /path_to_attribute/attribute.json
```
Note that AWS has a limit of 3 attributes for a thing. If you need more than 3, you need to define a ThingType and inherit from it. 
#### Create new thing type
```python
$ awsiot newthingtype MyNewThingType -a /path_to_attribute/attribute.json
```
#### Create new thing based on a thing type
```python
$ awsiot newthing MyNewThing2 -t MyNewThingType -a /path_to_attribute/attribute.json
```
#### Attach a certificate to a thing
```python
$ awsiot attachcert MyNewThing2 certificateARN
```