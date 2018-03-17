# Postgre
I am creating this repository as a guide for postgre installation on my Mac machine

As the first step to install postgre on my machine, I was directed towards Homebrew which landed me to github and finally I ended up writing this

#Step 1: Installing homebrew on my mac through writing the below command on terminal
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
Rest of the installation is self guiding

My homebrew installation was successful

#Step 2: Installing Postgresql

brew install postgres

I got an error stating that the brew link setup did not complete because the target already existed, as a resolution i decided to overwrite the file which existed but before doing that I cheked which file was to be overwriiten, this was checked with the below command

brew link --overwrite --dry-run postgresql

And finally executed the overwrite with the below command

brew link --overwrite postgresql

This gave the result Linking /usr/local/Cellar/postgresql/10.3... 377 symlinks created

But, I do not know what this means so I decide to create a database using the below command

#Step 3: Creating a database
initdb /usr/local/var/postgres -E utf8

Now I am installing lunchy to make the start and stop process of postgresql smooth 

#Step 4: Install lunchy
gem install lunchy

However, while installing lunchy, I did not have the write permissions to alter apple's ruby I think I could still avoid it through sudo path but why bother and take the risk of changing something you have no idea how to tackle. So instead i started my server therough below command

#Step 5: Start postgre server
pg_ctl -D /usr/local/var/postgres -l logfile start

And just to be sure that postgre is running you can check it with 

ps auxwww|grep postgres
