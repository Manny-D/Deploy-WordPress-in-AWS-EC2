# Deploying a WordPress website in an AWS EC2 instance

![Wordpress AWS Header Image](https://github.com/Manny-D/Deploy-WordPress-in-AWS-EC2/assets/99146530/28db9df8-07bc-487c-864b-8ae72d97e433)

<br>

## Description

In this project, we will Install Apache, PHP and MySQL server in a Linux instance and perform all configurations.

Install Wordpress in a EC2 Linux instance and make it available publicly for all users on the internet.

By the end of this course, you will be able to have a WordPress website installed and publicly available.

It assumes the following:
- you already have an AWS account to use

<br>

## Create an Elastic Cloud Compute instance

In the search bar, type <b>ec2</b> and click on <b>EC2</b>.

![Search EC2](https://github.com/Manny-D/Virtual-Private-Cloud-VPC/assets/99146530/067326a9-fe4a-450b-902d-c72f1b8b6560)

From the EC2 Dashboard, click on <b>Launch instance</b>.

![Launch Instance](https://github.com/Manny-D/Virtual-Private-Cloud-VPC/assets/99146530/f1d05095-a5b4-4735-bedc-c3ae098dfed4)

### Launch an instance wizard
Under <b>Name and tags</b>, enter a <b>Name</b> something you'll remember - eg. <b>MyWebServer</b>

![Name and tags](https://github.com/Manny-D/Virtual-Private-Cloud-VPC/assets/99146530/c7b4284c-2b18-4c65-ac60-13d35b9f8c33)

Under <b>Application and OS Images (Amazon Machine Image)</b>, do the following: 

![App and OS](https://github.com/Manny-D/Deploy-WordPress-in-AWS-EC2/assets/99146530/b4f464ef-5f8d-4085-a419-d042c20fb198)

- Click <b>Ubuntu</b>
- Under <b>Amazon Machine Image (AMI)</b>: (leave the default of <b>Ubuntu Server 24.04 LTS (HVM), SSD Volume Type</b>)
- Under Architecture: (leave the default of <b>64-bit (x86)</b>)

<br>

Under <b>Instance type</b>, leave it at the default of <b>t2.micro</b>

![Instance type](https://github.com/Manny-D/Virtual-Private-Cloud-VPC/assets/99146530/c915c310-54e4-4c6f-82de-a4387f5a0073)

Under <b>Key pair (login)</b>, click on <b>Create new key pair</b> 

![Key pair](https://github.com/Manny-D/Virtual-Private-Cloud-VPC/assets/99146530/83fe3e3f-8788-4d33-a220-9c38f0752e66)

In the <b>Create key pair</b> popup, do the following: 

![Create Key Pair](https://github.com/Manny-D/Deploy-WordPress-in-AWS-EC2/assets/99146530/abe4238f-a055-4da3-8690-be8f2dc99c93)

- <b>Name</b>: (enter in something you'll remember - eg. <b>masterKP</b>)
- <b>Key pair type</b>: (leave the default setting <b>(RSA)</b>)
- <b>Private key file format</b>: (leave the default setting <b>(.pem)</b>)
- Click <b>Create key pair</b>
- <b>Note</b>: the file will be automatically downloaded via the browser your using

<br>

Under <b>Network settings</b>, to allow our WordPress site to be accessible on the interet by web browsers:
- check the box for <b>Allow HTTPS traffi from the internet</b> 
- check the box for <b>Allow HTTP traffic from the internet</b>

![Network settings](https://github.com/Manny-D/Deploy-WordPress-in-AWS-EC2/assets/99146530/52b06969-8144-4e2c-862e-50c4bd994405)

Leave the defaults for all the remaining settings, look to the right of the wizard and click <b>Launch instance</b>. 

A similar page should load. 

![View all instances](https://github.com/Manny-D/Virtual-Private-Cloud-VPC/assets/99146530/6405186e-cea1-49c3-8956-e6732a267138)

Click <b>View all instances</b> to see the EC2 instances list.

![Instances](https://github.com/Manny-D/Deploy-WordPress-in-AWS-EC2/assets/99146530/012ffc84-24a9-4b39-bcad-f1d421901892)

Click on the <b>Instance ID</b> to see it in more detail.

![Instances summary](https://github.com/Manny-D/Deploy-WordPress-in-AWS-EC2/assets/99146530/8738ac30-b70e-4750-8e7c-d427808b8a2b)

![Instance Summary](https://github.com/Manny-D/Virtual-Private-Cloud-VPC/assets/99146530/ea2705c8-1c93-41db-a202-35ce5d388f2e)

<br>
