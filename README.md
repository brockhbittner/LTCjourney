# LTCChallengejourney
Learn to Cloud Challenge Journey

I am so grateful for the chance to work through these phases to learn to cloud! 

Notes along the way: 

Day 1: 
Getting familiar with Git and how it works was difficult, to say the least. Part of the problem was the technical difficulties that I encountered. 

First, Github Desktop was wanting me to use ATOM as my text editor, which I learned through some research was incompatible as it was sunsetted by Git a couple years back. 

Then, I discovered VSCode and got that installed. However, the changes I was making were not showing up in Github for me to commit and push. After some reasearch I discovered the problem was that autosave was turned off. So in the VSCode settings I turned autosave to "on Focus Change." Now, whenever I click off VSCode to GitHub desktop, it automatically recognizes the changes that I have made. So problem solved! 

But not too fast! I then went to continue working through Topic 1: Version Control and I copied "git clone https://github.com/rishabkumar7/ltc-labs" into VSCode and received the following error: "xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun" 

So I did some research on this and found that I needed to install some command line tools. I researched the command to initiate the download and copied it into VSCode: xcode-select --install 

Viola! 