# Deploying a WordPress site into an AWS EC2 instance

![Wordpress AWS Header Image](https://github.com/Manny-D/Deploy-WordPress-in-AWS-EC2/assets/99146530/28db9df8-07bc-487c-864b-8ae72d97e433)

<br>

## Description

In this project, we will Install Apache, PHP, MySQL server and Wordpress in an EC2 Linux instance, and make it available publicly for all users on the internet.

<br>

## Create an Amazon Web Services Account

If you already have an AWS Account, skip to the next part. If not, expand <b>Details</b> below to see more.
<details>
<summary>Details</summary>
 
<br>  

If you do not already have an AWS account, navigate to the following page to create one [https://aws.amazon.com/free](https://aws.amazon.com/free) and click on either Complete Signup or Create a Free Account.

![AWS Sign Up](https://github.com/Manny-D/Virtual-Private-Cloud-VPC/assets/99146530/60c3c592-9e8a-44d5-a7c8-74284d8cdc30)

When on the <b>Contact Information</b> page, select <b>Personal</b> for the Account type.
 
![Account Type](https://github.com/Manny-D/Virtual-Private-Cloud-VPC/assets/99146530/feaadbb9-de42-4ebb-b6c0-6901c0337891)

<b>Note</b>: you will be prompted to enter in credit card info. This is for identity verification and the card will only be charged if you exceed the Free Tier limits.

![CC](https://github.com/Manny-D/Virtual-Private-Cloud-VPC/assets/99146530/d31dd4ae-82db-4079-bdd0-c69649451c52)

Next you will be prompted to confirm your identity via a SMS code, then will be taken to the <b>Select a support plan</b> page, leave it at <b>Basic support - Free</b> and click <b>Complete sign up</b>.

![Free Tier](https://github.com/Manny-D/Virtual-Private-Cloud-VPC/assets/99146530/81256aff-4cfc-4697-8334-2cef1eef592c)

Sign up completed! Click on <b>Go to the AWS Management Console</b>.

![Sign up congrats](https://github.com/Manny-D/Virtual-Private-Cloud-VPC/assets/99146530/d60ae22b-4e1d-4235-9b3d-f30a36ec67aa)

Login to the AWS Management Console using the (default) <b>Root user</b> option. 

![Root user](https://github.com/Manny-D/Virtual-Private-Cloud-VPC/assets/99146530/f25d606b-96dd-42d9-85b3-a845951d3244)
</details>

<br>

## Create an Elastic Cloud Compute instance
<details>
<summary>Details</summary>
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
- Under <b>Architecture</b>: (leave the default of <b>64-bit (x86)</b>)

<br>

Under <b>Instance type</b>, leave it at the default of <b>t2.micro</b>

![Instance type](https://github.com/Manny-D/Virtual-Private-Cloud-VPC/assets/99146530/c915c310-54e4-4c6f-82de-a4387f5a0073)

Under <b>Key pair (login)</b>, click on <b>Create new key pair</b> 

![Key pair](https://github.com/Manny-D/Virtual-Private-Cloud-VPC/assets/99146530/83fe3e3f-8788-4d33-a220-9c38f0752e66)

In the <b>Create key pair</b> popup, do the following: 

![Create Key Pair](https://github.com/Manny-D/Deploy-WordPress-in-AWS-EC2/assets/99146530/abe4238f-a055-4da3-8690-be8f2dc99c93)

- <b>Name</b>: (enter in something you'll remember - eg. <b>masterkp</b>)
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

Once completed, a similar page should load.

![View all instances](https://github.com/Manny-D/Virtual-Private-Cloud-VPC/assets/99146530/6405186e-cea1-49c3-8956-e6732a267138)

Click <b>View all instances</b> to see the EC2 instances list.

![Instances](https://github.com/Manny-D/Deploy-WordPress-in-AWS-EC2/assets/99146530/012ffc84-24a9-4b39-bcad-f1d421901892)

Click on the <b>Instance ID</b> to see it in more detail.

![Instances summary](https://github.com/Manny-D/Deploy-WordPress-in-AWS-EC2/assets/99146530/8738ac30-b70e-4750-8e7c-d427808b8a2b)

Great! Our AWS EC2 instance is now ready to install the various software for the project.

<b>Note</b>: copy both the <b>Public IPv4 address</b> and <b>Public IPv4 DNS</b> URL, as well be using them shortly!

<br>
</details>

## Installing Apache Webserver

The following steps will be done via a command line. As I am on a MAC, the following screenshot will be of iTerm. If you are on Windows, utilize Command Prompt.

Navigate to where you downloaded the .pem key pair file earlier. Mine defaulted to the Downloads folder, so I will enter the following:

```
cd Downloads
```

![Downloads](https://github.com/Manny-D/Deploy-WordPress-in-AWS-EC2/assets/99146530/1285669b-00bd-46b5-8050-cc392cc62bf7)

<br>

Let's ssh into the Apache Webserver now, using the following:

```
ssh -i "yourkeypairfilename.pem" ubuntu@yourPublicIPv4address
```

![Ubuntu SSH](https://github.com/Manny-D/Deploy-WordPress-in-AWS-EC2/assets/99146530/d07e8a08-ae8d-4ce6-a290-3cccecd632d3)

Type <b>yes</b> here and press Enter.

<br>

You may receive an error similar to this:

![SSH Error](https://github.com/Manny-D/Deploy-WordPress-in-AWS-EC2/assets/99146530/f569d8cc-bc5d-4a36-ac2f-1b8f52477a5a)

This is usually because the .pem key is publicly visible - eg. on your Desktop or Downloads folder, so it's denied access as a security precaution.

<br>

To address this, we have to modify the .pem file permissions using either CHMOD 400 (read only) or 600 (read and write).

```
chmod 600 /Users/mymac/Downloads/masterKP.pem
```

Nothing will return to show it was successful, but if you try so <b>ssh</b> again, you will connect.  

![CHMOD](https://github.com/Manny-D/Deploy-WordPress-in-AWS-EC2/assets/99146530/37af217a-98df-4718-8aa7-ea9381c9b477)

Now that were inside Linux, let's install an AWS package that will allow us to connect via a web browser called <b>Instance Connect</b>. 

<br>

First, we need to update and upgrade the Linux instance packages via the following commands:

<b>Note</b>: these may take some time to complete and if prompted, type <b>Y</b> to continue

```
sudo apt-get update
```
then
```
sudo apt-get upgrade
```

<br>

To install <b>Instance Connect</b>, type:

```
sudo apt-get install ec2-instance-connect
```

<br>

Now to install the first piece of software to help host our <b>Wordpress</b> website, the <b>Apache Web Server</b>. If prompted, type <b>Y</b> to continue:

```
sudo apt-get install apache2
```

<br>

To confirm <b>Apache Web Server</b> was installed successfully, open a new web browser or tab in your current browser and enter the <b>Public IPv4 DNS</b> URL. 

You should see the following page load:

![Apache](https://github.com/Manny-D/Deploy-WordPress-in-AWS-EC2/assets/99146530/31ff7427-926f-44d2-9698-d63f11bf58f5)

Amazing.. it works!!

<br>

