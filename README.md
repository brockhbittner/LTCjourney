# Learn to Cloud Challenge

My name is Brock Bittner, I am an aspiring IT Support Specialist and Cloud Engineer! 

You can find me on linkedin: https://www.linkedin.com/in/brock-bittner-657020198/

These are my notes that I take on my journey to learn to cloud! Thank you so much to @madebygps and @rishabkumar7 for all your hard work in setting this up. I am so grateful for the chance to work through these phases.


## Day 1:

I got everything installed and setup, which was fun and challening to figure out! The [Microsoft document about Markdown](https://learn.microsoft.com/en-us/training/modules/communicate-using-markdown/2-what-is-markdown) was really helpful to get me acquainted with how Github works. I tried to implement some of it here just to get some familiarity with it. I am going to stop here for now and pick back up later to continue working on [Topic 2: Cloud CLI Setup](https://learntocloud.guide/phase1/cli) another time. I already have an AWS account, so that gives me a good start on that!

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

So now the challenges begin! As a preface, Microsoft Copilot was very helpful in this and taught me a lot about how to navigate and solve these problems. I won't list the solutions to these problems, but instead I will describe some important things that I learned or practiced in each of them as well as the skills needed to accomplish the challenge. 

### Beginner Level

#### Challenge 1: Find a hidden file

>**Skills:** Basic file listing, hidden files concept

>This one was relatively simple, since it required basic commands and flags for navigating the directories. 

#### Challenge 2: Locate a file with "secret" in its name

>**Skills:** File searching, directory navigation

>This one was a good refresher and I learned about how to search for words in a file name instead of just words contained in files. 

### Intermediate Level

#### Challenge 3: Find the largest file in a specific directory

>**Skills:** File size analysis, sorting, log navigation

>This one was a little bit tricky as it required piping commands together. I played around with it some to get a better grasp of different flags and how that affects the way information is displayed. I learned a lot from this!

#### Challenge 4: Identify a user with a specific UID

>**Skills:** User management, system files, permissions

>This one was harder! I was not very familiar with how to accomplish this challenge, so it was helpful to do my best to navigate to the relevant directories and files to find the information I needed. Copilot was helpful here and I feel like I am much more comfortable with User Management from the CLI now. 

