# In answer to https://nhoya.github.io/post/why-windows-over-linux-desktop/

Dear Francesco,
I read your rant about moving on Windows, and what I want to ticke some of the point you make.

# “Linux distributions are malware-proof”

This is an old discussion.
Linux was never malware-proof, but thanks to his way to distribute software trought a centralized and verified systesm, is much more secure than downloading exe from random websites.
You may argue you can download random deb/rpm, but reality is the mechanism in place to avoit that is way better in most Linux distributions.
It is true Microsoft did a great step forward with releasing its store, but unfortunately is still promoting third party exe installation by banning common software like Firefox and Chrome.
Once again the thirst for market control is ruining a genuine good implementation, and show the real heart of the company.

# "The new CoC is sh*t"

I agree and disagree.
I belive the real issue started with the Linux Foundation basically killing the user opinion by granting only one vote for the community.
The new CoC is at least controversial, but you really believe the CoC from Microsoft is better? Just in March varius article emerged about the ambient at Microsoft is toxic and arrassing for woman, so essentially what is the lesser evil? A company that even now is getting sued from the antitrust for illegal market practise?
Even with the new CoC, it is pretty clear who is the lesser evil.

# “Microsoft is spying on us!”

I find really funny how you has people to point out for resources but i clear how you>
- dont give a way to comment/PR on the article
- didnt make a basic search by yourself
Since you ask for resource, especially here in EU we habe TONS of lawsuit even from different governament against Microsoft.
That is only 3 articles taken from the first page of a goolge research for "microsoft illegal data collection", and are all article have less than 3 years.
So yes, “Microsoft is spying on us!”, and there is no doubt.

https://www.theinquirer.net/inquirer/news/3019164/microsofts-intrusive-data-collection-in-windows-10-breaks-dutch-privacy-laws - microsoft founf guilty that the firm "does not clearly inform users about the type of data it uses, and for which purpose".

https://www.pcworld.com/article/3098038/windows/windows-10-personal-data-collection-is-excessive-french-privacy-watchdog-warns.html - The French National Data Protection Commission say Windows 10 personal data collection is excessive and has given Microsoft three months to comply with its order or face fines that could top $1.66 million.

https://www.waonews.com/news/16659-Brazil_sued_Microsoft_Win10_for_illegal_collection_of_data_for_a_fine_of_2_million_870_thousand.html - Brazil sued Microsoft Win10 for illegal collection of data

# "Xorg and Wayland"

those are very real point you are making.
Unfortunately is not a fair comparison; while is true those issue rely on the architecture of the system, we have no real access to windows internal to know how stuff are structurated (well, probably someone find it out, but its not something Microsoft developer write article about).
So you are confusing a secure system with security through obscurity. If you want an example of similar issue extremly hard to patch in win10, look up for "AtomBombing"

On the other end, did you know if you set up a full disk encryption with windows, by default "Windows Device Encryption", the key are sent to microsoft server (that also mean you need a Microsoft account). Oh but don't worry, this is a "feature, not a bug".

# "The issue with distributions system"

Very true, fragmentation is not only an issue for mainteinance of package but also for the development of feature, bug fix, and coordination.
But that is also a strenght, as if your current distro does not satisfy you, you have chooses.
Stick to main distribution, and remeber the problem is not to be violated, but how you respond to such violation.
And yet again the packet manager system in Linux distro make much easier to be sure your whole system is updated; and there is no doubt the windows update system is feared by most people, I'm also wondering wht is windows doing during its update when I can literally install a full Ubuntu in the same time.

# “Everyone can read the source code of Linux so it’s more secure”

You are confusing MORE with "perfect".
You are right that being open does NOT mean it is safe, but it has POTENTIAL to be more safe.
After all, even Apple open sources their crypt library, and almost immediatelly the infamous ssl goto bug was found.
But if we want to see at the hard data, despite being harder to analize, Microsoft product have much more and worse vulnerability, you can see for yourself the CVSS scores: https://www.cvedetails.com/top-50-vendor-cvssscore-distribution.php

# "Interesting Security Features in Windows 10"

I agree win 10 has increased a lot on security, with windows defender, the windows store and I'm sure some more.

## VBS

not sure what it is, pass

## Controlled Folder access

oh, just like the SElinux or AppArmor? Cute.
Andoroid pushed the concept even furter with periferical access and making it by default.
Snappy and Flatcpack are pushing to make iy by default even on desktop.

## Secure Boot

Very good, unfortunately not really useful unless with a fully encrypted disk, and this is payinful in Windows.
I personally use BitLocker to encrypt folders, and there is no way for simple stuff like automatically mount the encrypted partition, 
lets not talk about mount and descrypt at login.
Want to use a private key? you have to generate it yourself with 3rd part tool.
Want to use an external HW wallet? your mileage will vary and probably need a 3rd party tool.
All those security feature feels like second class citizen in Win10, while on most distro is easy as checking a flag on the installation setup.

# Conclusion

Is not my intention to stop you.
Actually is better, way better if you go and try and see by yourself.
The beauty to buy any printer and know it will work with minimal installation required (windows) and the beauty to make updates without fear (linux distro).
The smoot gaming using full performance of your device (windows) and the excitement to see a new big title on linux.
Using the cool new CAD that will draw for you and make coffe, and the beauty to use your your package manager to install something without bullshit (linux distro).
There are many reason to choose one OS over the other, just keep it real :)

If instead you are someone that come from the Windows side and want to experiment a bit with linux, I can suggest you to play with the following (just use them "live" from a USB stick!):
- Ubuntu
- Fedora
- Neon
- Solus
