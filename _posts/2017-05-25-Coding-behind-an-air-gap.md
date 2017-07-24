---
published: false
---
Since July 2016, I've been developing software behind an air gap. After 20 years of the Internet being more and more ubiquitous, being dropped in a situation where access to the web is so strictly controlled in and outside of work was certainly a jarring experience. Here are some things that most software developers take for granted while coding that I've learned to appreciate now that they've been taken from me (or made so much more difficult).

## Looking stuff up
I don't _just_ develop behind an air gap - I also have very limited access to internet as well. The device we use to look stuff up on the internet is an [NComputing](https://www.ncomputing.com/) device, which is basically a bare-bone machine that can RDP or VNC into a central server. The internet is also based on a white-list, meaning we can only access sites that are meant for software development (Google, StackOverflow, etc.) and other sites through Google web cache.

I wasn't the biggest fan of `Ctrl+C, Ctrl+V` method of coding, but with this gap it has become simply impossible. For certain snippets of code, e.g., getting started with a new tool, I find my self manually copying code between my monitors. For any, *ehem*, "unsanctioned" binary data (like a profile picture for our internal [Confluence](https://www.atlassian.com/software/confluence) instance), we fall back to the good old BNP, which stands for Base64 Nogada Protocol. (Nogada<노가다> is a Korean term for busy work.) Basically, we hand copy a base 64 string.

## Lack of updates
Recently, we jumped the gap and brought in an offline installer for Visual Studio 2017. To our dismay, we found that failed to install on all of our Windows 7 workstations. The reason? VS2017 only supports Windows 7 _SP1_, and without Windows Update and isolated from the dangers of the internet, we just never found the reason to jump the gap with updates.

Lack of updates also brings unique problems during development that nobody has experienced for years. For instance, I recently was testing a Windows kernel driver on Windows 7 x64, properly signed and everything... which just wouldn't work. After a lot of Googling, I found in the deep depths of MSDN [an article](https://msdn.microsoft.com/en-us/windows/hardware/drivers/install/appendix-4--driver-signing-issues) telling me that there was a bug in Windows 7 that would reject drivers signed with a SHA256 certificate. This bug was [fixed](https://technet.microsoft.com/en-us/library/security/2949927.aspx) in 2014 which made it even more difficult for me trying to figure this out in 2016.

## Jumping the gap
Updates to software aren't the only reason we jump the gap. We also jump it (using good ole' CD-Rs) to bring in **libraries**. We have schedules and are short on time just like every other software developer out there... if we did not have the ability to bring in external libraries, we simply would not get anything done. (How am I supposed to write C# unit tests without [xUnit](https://xunit.github.io/) and [NSubstitute](http://nsubstitute.github.io/)? We write unit tests... we aren't savages, you know ;-) ) The only problem is that there are, as expected, a lot of red tape to cut through to jump the gap - if it were easy, why have the gap in the first place?

## If life gives you lemons...
The intranet we use for development is used by about 20 developers. We work on many different projects and have different needs. As I said above, jumping the gap is difficult and not commonplace, but if we had it our way, we would be bringing in a different library every other day. Since it's just not feasible, we settled for the next best thing: **mirror everything.** We have an intranet mirror of npm, NuGet, PyPi - you name it. This allows us to go about our business *almost* as if we were connected to the internet, saving us the pain of having to jump the gap every time we fancy a new library.

-----

I can't wait to go back to developing software on an internet-connected device, but to be honest I've actually become quite accustomed to the air gap. Besides, I can definitely see the bright side of having been put in this setting - for one, I am now much more *aware* of networking configurations now that we have to manage this intranet ourselves. Besides, I'm sure this will make a good story to tell the young 'uns once I'm an old, shriveled-up developer in 30 years.
