+++
title = "c. SSH into an EC2 instance"
weight = 90
tags = ["tutorial", "cloud9", "s3"]
+++

The operating system of your local computer determines the options that you have to connect from your local computer to your Linux instance. Here are directions to connect from Windows Using PuTTY or OpenSSH, From Linux & MacOS-X using ssh client and from Windows Subsystem for Linux (WSL) using ssh client.




**Connecting from Windows using PuTTY**

We will now use the private **.ppk** file of the key pair generated earlier to open a SSH session to the EC2 instance.

1.  Start the PuTTY application.

2.  Enter in the IP address of the EC2 instance in the **Host Name (or IP address)** field.

3.  To save the session (so we dont have to repeat the configuration everytime) provide a name in the **Saved Sessions** field.

4.  In the left navigation pane under **Connections** clickon **SSH** and next click on **Auth**.

5.  In the **Private key file for authentication** field click **Browse** and browse in the **.ppk** file downloaded when creating the key pair earlier.

6.  Next in the left navigation pane click on **Session** (**scroll up if you need to**) and and further click on **Save** to save the session.

7.  Next click on **Open** to start the SSH session.

8.  PuTTy will now attempt to start an SSH Session.

**NOTE**: You will get a security Alert **The Servers host key is not cached in the registry**, click on **Yes** to continue.

9.  You will now be presented with the **login as** prompt.

10. At the **login as** prompt type **ec2-user** and hit enter.

You would have now logged into the EC2 instance on AWS.


--------------

**Connecting from Windows using Windows Subsystem for Linux**

We will now use the private **.pem** file of the key pair generated earlier to open a SSH session to the EC2 instance.

1.  Copy the private key from Windows to WSL - In a WSL terminal window, copy the .pem file (for the key pair that you specified when you launched the instance) from Windows to WSL. Note the fully-qualified path to the .pem file on WSL to use when connecting to your instance.

```bash
cp /mnt/<Windows drive letter>/path/my-key-pair.pem ~/WSL-path/my-key-pair.pem
```

2.  In a terminal window, use the ssh command to connect to the instance. You specify the path and file name of the private key (.pem), the user name for your instance, and the public DNS name or IP Address.

**NOTE**: Username to be used here is **ec2-user**.

```bash
sudo ssh -i /path/my-key-pair.pem ec2-user@<ip-address>
```

You will see the following response:

```bash
The authenticity of host '<ip-address>'
can't be established.
RSA key fingerprint is 1f:51:ae:28:bf:89:e9:d8:1f:25:5d:37:2d:7d:b8:ca:9f:f5:f1:6f.
Are you sure you want to continue connecting (yes/no)?
```

3.  Enter **Yes**

you will now be logged into the EC2 Instance.


-------------



**Connecting  using SSH on Linux & MacOS and OpenSSH on Windows**

We will now use the private **.pem** file of the key pair generated earlier to open a SSH session to the EC2 instance.

1.  In a terminal window, use the ssh command to connect to the instance. You specify the path and file name of the private key (.pem), the user name for your instance, and the public DNS name or IP Address of your instance.

```bash
ssh -i /path/my-key-pair.pem ec2-user@<ip-address>
```

You see a response like the following:

```bash
The authenticity of host 'ec2-198-51-100-1.compute-1.amazonaws.com (198-51-100-1)' can't be established.
ECDSA key fingerprint is l4UB/neBad9tvkgJf1QZWxheQmR59WgrgzEimCG6kZY.
Are you sure you want to continue connecting (yes/no)?
```

2.  Enter **Yes**

You will now be logged into the Instance.

**NOTE**: You might need to change the permissions of the key file by running the chmod command as follows
```bash
chmod 600 /path/my-key-pair.pem
```

For detailed directions on these please have a look at the following links:

[PuTTY](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html),
[Windows Susbsystem for Linux](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/WSL.html),
[MacOS-X ssh Client](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html),
[Linux ssh client](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html)
