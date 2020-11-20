Simple setting up python and Github on Amazon EC2 Linux instances

### connect AWS EC2 instance using SSH
: [AWS user guide for linux instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html) explains all details.
```
ssh -i /path where your aws key is located/["your aws key name"].pem ec2-user@xxx.amazonaws.com
```

### check python 
: check python version 
```
[ec2-user@xxx] python --version
python 2.x
```
install the latest version (python v.3.7), if you want to know more, please check [an article on stackoverflow](https://stackoverflow.com/questions/27669927/how-do-i-install-python-3-on-an-aws-ec2-instance) and also [Amazon Elastic Beanstalk depveloper guide](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install-linux.html). To install python v

```
[ec2-user@xxx] sudo yum install python37
```
: After installing python v.3.7, you configure it as the default interpreter with comments `python --version`. To alias python 3, find `.bashrc` file using comment `la -all` and then your `.bashrc` file and type `alias python=python3` on to a new line at the top of the file then save the file with `ctrl+o` and close the file with `ctrl+x`. The discussion can be found on [stackoverlow](https://stackoverflow.com/questions/41986507/unable-to-set-default-python-version-to-python3-in-ubuntu)

```
[ec2-user@xxx] nano ~/.bashrc
[ec2-user@xxx] source ~/.bashrc

```

install python package with a pip installer. First, we install pip. 
```
[ec2-user@xxx] curl -O https://bootstrap.pypa.io/get-pip.py
[ec2-user@xxx] python3 get-pip.py --user

```
after then, install packages you need
```
[ec2-user@xxx] python -m pip install --user numpy scipy matplotlib pandas scikit-learn
```
check them 
```
[ec2-user@xxx] pip list
```
Download and install git in AWS EC2 instance. The detailed explanation can be found in [the link](https://cloudaffaire.com/how-to-install-git-in-aws-ec2-instance/) and [here](https://www.altoros.com/blog/getting-started-with-a-cpu-enabled-tensorflow-instance-on-aws/)
```
[ec2-user@xxx] sudo yum update -y
[ec2-user@xxx] sudo yum install git -y
```
Then, check git version 
```
[ec2-user@xxx] git version
```
Now, set up git.
initialize git repository and input your information, user name and email address
```
[ec2-user@xxx] git init
[ec2-user@xxx] git config --global user.name "[your useranme]"
[ec2-user@xxx] git config --global user.email "[your email address]"
```

add yout file to your repository and then commit it
Then check the status

```
[ec2-user@xxx] git add .
[ec2-user@xxx] git commit -m "first commit"
[ec2-user@xxx] git status
```
add repository on github

```
[ec2-user@xxx] git remote add origin https://github.com/"[your github repository]".git
[ec2-user@xxx] git remote -v
```
then, you're all set. 
to test it, clone a repository and download python code. 
```
[ec2-user@xxx] git clone ....
```
Then, run it.
```
[ec2-user@xxx] python aws_ec2.py
```
Enjoy :)