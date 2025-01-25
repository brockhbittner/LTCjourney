# Learn to Cloud Challenge - Brock Bittner

My name is Brock Bittner, I am an aspiring IT Support Specialist at the moment and an aspiring Cloud Engineer in the long term! 

You can find me on linkedin: https://www.linkedin.com/in/brock-bittner-657020198/

These are my notes that I take on my journey to learn to cloud! Thank you so much to @madebygps and @rishabkumar7 for all your hard work in setting this up. I am so grateful for the chance to work through these phases.


## Day 1:

Getting familiar with GitHub and how it works is difficult, to say the least. I am thankful that I have had at least some experience in the command line from my Google IT Support Specialist certification. Part of the problem was the technical difficulties that I encountered. Here is a description of how I worked through some of these problems:

> First, GitHub Desktop was wanting me to use ATOM as my text editor, which I learned through some research was incompatible as it was sunsetted by Git a couple years back. 

> Then, I discovered VSCode and got that installed. However, the changes I was making were not showing up in GitHub for me to commit and push. After some reasearch I discovered the problem was that autosave was turned off. So in the VSCode settings I turned autosave to "on Focus Change." Now, whenever I click off VSCode to GitHub desktop, it automatically recognizes the changes that I have made. So problem solved! 

> But not so fast! I then went to continue working through [Topic 1: Version Control](https://learntocloud.guide/phase1/versioncontrol) and I copied `"git clone https://github.com/rishabkumar7/ltc-labs"` into VSCode and received the following error:
>```markdown
xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), 
missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun
``` 
> So I did some research on this and found that I needed to install some command line tools. I researched the command to initiate the download and copied it into VSCode: `xcode-select --install`

> Viola! 

I was able to read through the [Microsoft document about Markdown](https://learn.microsoft.com/en-us/training/modules/communicate-using-markdown/2-what-is-markdown), which was really helpful. I tried to implement some of it here just to get some familiarity with it. I am going to stop here for now and pick back up later to continue working on [Topic 2: Cloud CLI Setup](https://learntocloud.guide/phase1/cli) another time. I already have an AWS account, so that gives me a good start on that!

## Day 2:

I learned a lot from reading the [Command Line for Beginners article](https://www.freecodecamp.org/news/command-line-for-beginners/). I also got the AWS CLI downloaded, which means I am on to [Topic 3: Infrastructre as Code](https://learntocloud.guide/phase1/iac)!

I tried installing Terraform but was unable to. The CLI was not recognizing the `brew` command, so I did some research and found that I needed to download [Homebrew](https://brew.sh/) -- a mac(os) or Linux package manager. I then installed it using the CLI by copying: 
```markdown
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
``` 

I was then able to copy the following Terraform download command into the CLI and download it:
```markdown
brew tap hashicorp/tap 
brew install hashicorp/tap/terraform
```




