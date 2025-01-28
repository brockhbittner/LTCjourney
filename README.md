# Learn to Cloud Challenge - Brock Bittner

My name is Brock Bittner, I am an aspiring IT Support Specialist at the moment and an aspiring Cloud Engineer in the long term! 

You can find me on linkedin: https://www.linkedin.com/in/brock-bittner-657020198/

These are my notes that I take on my journey to learn to cloud! Thank you so much to @madebygps and @rishabkumar7 for all your hard work in setting this up. I am so grateful for the chance to work through these phases.


## Day 1:

Getting familiar with GitHub and how it works is difficult, to say the least. I am thankful that I have had at least some experience in the command line from my Google IT Support Specialist certification. Part of the problem was the technical difficulties that I encountered. Here are the ways I worked through diagnosing and solving some of these problems:

First, GitHub Desktop was wanting me to use ATOM as my text editor, which I learned through some research was incompatible as it was sunsetted by Git a couple years back. 

Then, I discovered VSCode and got that installed. However, the changes I was making were not showing up in GitHub for me to commit and push. After some reasearch I discovered the problem was that autosave was turned off. So in the VSCode settings I turned autosave to "on Focus Change." Now, whenever I click off VSCode to GitHub desktop, it automatically recognizes the changes that I have made. So problem solved! 

But not so fast! I then went to continue working through [Topic 1: Version Control](https://learntocloud.guide/phase1/versioncontrol) and I copied `"git clone https://github.com/rishabkumar7/ltc-labs"` into VSCode and received the following error:
```
xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), 
missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun
```     

So I did some research on this and found that I needed to install some command line tools. I researched the command to initiate the download and copied it into VSCode: `xcode-select --install`

Viola! 

I then read through the [Microsoft document about Markdown](https://learn.microsoft.com/en-us/training/modules/communicate-using-markdown/2-what-is-markdown), which was really helpful. I tried to implement some of it here just to get some familiarity with it. I am going to stop here for now and pick back up later to continue working on [Topic 2: Cloud CLI Setup](https://learntocloud.guide/phase1/cli) another time. I already have an AWS account, so that gives me a good start on that!

## Day 2:

I learned a lot from reading the [Command Line for Beginners article](https://www.freecodecamp.org/news/command-line-for-beginners/). I also got the AWS CLI downloaded, which means I am on to [Topic 3: Infrastructre as Code](https://learntocloud.guide/phase1/iac)!

I tried installing Terraform but was unable to. The CLI was not recognizing the `brew` command, so I did some research and found that I needed to download [Homebrew](https://brew.sh/) -- a mac(os) or Linux package manager. I then installed it using the CLI by copying: 
```markdown
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
``` 

I then ran the following commands as instructed: 
- Run these commands in your terminal to add Homebrew to your PATH:
    ```markdown
    echo >> /Users/brockbittner/.zprofile
    echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/brockbittner/.zprofile
    eval "$(/opt/homebrew/bin/brew shellenv)"
    ```
- Run `brew help` to get started

I was then able to copy the following Terraform download command into the CLI and download it:
```markdown
brew tap hashicorp/tap 
brew install hashicorp/tap/terraform
```

Next time I will press on to [Topic 4: SSH](https://learntocloud.guide/phase1/ssh)!


## Day 3: 

Man [this SSH exercise](https://learn.microsoft.com/en-us/training/modules/develop-on-remote-machine/) was a doozy to figure out! I had a hard time figuring out how to correctly describe the file path to the .pem file so that it could check the public and private key. Eventually I was able to use the `pwd` command to find the correct path and then append the .pem file name to it and it worked! This took me a lot longer than it should have, but honestly I learned a lot so I am grateful for the time it took! We often remember things best when we have to wrestle to figure out the conclusion rather than having the answer handed to us. 

On to the [Linux Command Line CTF Challenge](https://learntocloud.guide/phase1/ctf)!

Or so I thought... lol! I discovered after probably way too long that I had not configured my AWS CLI properly back in the [second topic](https://learntocloud.guide/phase1/cli). I am trying to get this fixed, but I will have to resume tomorrow. I am getting this error: 
```Markdown
An error occurred (InvalidAccessKeyId) when calling the ListBuckets operation: 
The AWS Access Key Id you provided does not exist in our records.
```
I am not sure why considering I followed all the directions: I went into IAM, set up a new user, and created an access key which generated an access key and a secret key. I then typed `aws configure` and copied and pasted the keys that I had just created, put  `us-east-2` for the default region name and `json` for the default output format. And yet I still received this error. I will have to try again tomorrow and figure out what is going on!

## Day 4: 

Thankfully I was able to figure out the problem! All I needed to do was restart VS Code and it allowed my credentials to work! Sometimes it really is that simple lol! I then faced a number of permission denied errors when trying to run the `terraform apply` but I was able to sort those out in IAM by applying some full access policies to my user. 

So now the challenges begin! As a preface, Microsoft Copilot was very helpful in this and taught me a lot about how to navigate and solve these problems. 

### Challenge 1: Find a hidden file

In order to find the hidden file in the directory I used the `ls -a` command to list all the files including hidden ones, and I was able to find `.hidden_flag` which containted `CTF{hidden_files_revealed}`! 

### Challenge 2: Locate a file with "secret" in its name

For this I used `find -name "*secret*"` to find `very secret_file.txt`. However, since the CTF file is called  `CTF{grep_is_your_friend}`, the grep version of this would be `find | grep "secret"`. 

### Challenge 3: Find the largest file in a specific directory

For this I did `du -ah /home/ctf_user | sort -rh`. The output showed me a list of files and directories and their corresponding file sizes. `-a` shows all and `-h` puts the file sizes in a human readable format. Then I piped the results through `sort` to arrange then in reverse order (`-r`) and again in human readable format (`-h`). 

### Challenge 4: Identify a user with a specific UID

I used the `cd /etc` command to find the `passwd` file which I opened and found that the 1002 user is `flag_user`. I then did `sudo -i -u flag_user` and input the password for the ctf_user account. Then I did the `ls` command and found `flag.txt` in which was `CTF{user_detective}`!

