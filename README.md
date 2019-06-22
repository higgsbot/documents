## What is HiggsBot?
HiggsBot is a bot to run small code snippets in a Discord chat. You give the bot some code, it will run it, and return the output to the chat.
Due to the nature of such a project, some extra security and anti-abuse efforts will be required over a typical Discord bot.
This is however a week hack-a-thon type project for Discord Hack Week 2019, so the bot won't actually, really be that secure. More of a proof of concept.

## Securing the execution of arbitrary code
Ideally, you'd do something like KVM or DigitalOcean Droplet, with no internet connection (or, just enough for the bot to connect).
For the purposes of this project though, we will be using simple chroots, since time and money are major constraints and the project doesn't have to be super public.
Each language (Python, C/CPP, ASM, etc.) will have it's own container (chroot, in this case), and each snippet will be run in a fresh container.

## Securing against fork bombs, CPU hogs, etc.
The primary defence against an abusive program will be CodeTokens, which will gave a finite amount of execution time per CodeToken. 
A limit on the number of CodeTokens the user can have will prevent a user from obtaining a bunch and overusing resources for too long.
No, these CodeTokens cannot be bought with real currency (at least, on our version - any forks by others might be different).
A code snippet should ideally be limited in CPU usage and RAM as well, but this is again a hack-a-thon style project.