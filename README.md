# Packer Recipe for a Docker-Capable Amazon EC2 AMI

This is a very minimal AMI that has Docker installed, on Ubuntu (HVM).

It uses the official Ubuntu Docker (lxc-docker) packages.

## Usage

This is a [Packer](https://packer.io/) template. Install the latest version of
Packer, then:

    packer build \
      -var docker_version=1.6.2 \
      -var source_ami=ami-d05e75b8 \
      -var aws_region=$AWS_REGION \
      -var aws_access_key=$AWS_ACCESS_KEY_ID \
      -var aws_secret_key=$AWS_SECRET_ACCESS_KEY \
      docker-ami.json

For VPC:

    packer build \
      -var docker_version=1.6.2 \
      -var source_ami=ami-<id> \
      -var instance_type=m3.medium \
      -var aws_region=$AWS_REGION \
      -var aws_access_key=$AWS_ACCESS_KEY_ID \
      -var aws_secret_key=$AWS_SECRET_ACCESS_KEY \
      -var vpc_id=vpc-<id> \
      -var subnet_id=subnet-<id> \
      docker-ami-vpc.json


This will chew for a bit and finally output the AMI ID.
