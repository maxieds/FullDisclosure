# Key new features and development tasks

A semi-comprehensive listing and description of roughly grouped feature sets I 
want in my new roll-your-own Android OS before I can officially get bored again 
and maintain code. These are some pretty interesting, and in some cases novel, 
features that I think will make the project stand out -- and in particular, will 
make it worth my time to use it. There are roughly three or four main components 
that must be added to make it a sane beta, and the rest, like picking which commandline 
security software should be included on a small-sized binary distribution can, again, 
in principle be worked out by collaborators who like my customizations and decide to 
come on board. Let's get started with some obvious improvements to the vanilla 
Android OS, and then some smaller ways to remove pet peeves I have absorbed in learning 
to cope with the layered API and feature sets on this platform. 

## A native GOOD, god yes very good, NFC stack with gossipy radio-level hardware


I have decided that while this freedom is excellent, and enlightening, I'm not even 
going to touch the default mechanisms for GooglePay et. al. It is true that after every 
five or so $6.5 coffee beverages at Starbucks I am ought another free Caramel Macchiato, 
I would feel far too slimey to let something like that slip because *their AID and general 
protcols are now subsumed under my usage of my hardware*. Granted, this is lovely for 
sniffing out the door readers and other card-related entertainment to be had with a phone 
minoring in DESFire, but the former abuse is for lack of better wording *wrong*. 
The list of enticing known AID codes (TODO), of which these damn door readers will only publish one 
-- along with their unconventional, security by obsurity use of NTAG over APDU codes -- 
is acceptable. In the name of pissing off the housing faculty that yelled at me for taking 
down my smoke detector and threatened my cat -- there shall be maps made available like the 
hacker manuals some elitist schools pass around. New age NFC geo-caching with 
Benito Mussolini's head on a stick amuses me on this night.

The existing libraries (TODO, X3) need to be supplmented with a database of 1) default key configurations 
for different tags; and 2) better formatted versions of the verbose return and status codes I included 
in the [Chameleon Mini Live Debugger]() application. The "naughty" lists of AID codes which are supposed 
to be guarded by proprietary systems should also be good fare to /usr/share documents to draw on. 
Similarly, there are lengthy lists of (udev for one) and LIDs USB device mappings that can be used to 
identify new devices plugged into the system. 


OS / SDK / phone hardware "fingerprinting" profiles for fun; 



## More structured logging features for varied events



## A nicer, functionally useable Linux-like desktop arrangement



## A restructured "new" settings application

Not to replace the existing one, but rather to separate out the code base for easier 
integration later, when we are clearly going to need a configuration mechanism that is 
sane and structured for what I'm planning. 
Each installed application should be able to be inspected (similar to many APK and Manifest 
inspectors which glean intents from app metadata). Activities (and libraries for that matter) 
installed by any application can be called from userland and/or inserted into everyday utilities. 
As a part of this, the SharedPreferences treasured as private with every (system) app install 
should contain no secrets to our sudoer users that be. This has long been a source of annoyance 
to me with []() storing an intangible initial key which I purchased online, or for example, in 
finding ways to extract meaningful (ammo to help exhaust it's misery on my phone) data from the 
plethora of mSPY bullshit (pardon) that my phone was plowed with not so long ago. 
The idea here seems to me to boil down to responsible transparency: I am not going to include any 
obnoxiously skript kiddie level applications to be abused (my professors at the fine UIUC saw to it 
that every CS major of sufficient intellectual growth past the 200-level took an extensive reading 
class on ethical and professional issues that arise in computer science). This in the background, 
I personally am not going to be the one responsible for some abusive overbearing parents or some worse 
violent stalkerish behavior happening because I happen to hate the policies of a company I might one day 
have to work for. We shall be open, and free, but a key lesson in life's morality is that it is extremely 
important not to be an ASSHOLE when it is avoidable (cf. my LICENSE.md document). 

Ability to murder Google's annoying and pervasive AdMob API at the library level.
Ability to determine mobile data usage and traffic so one (class say) can generate a toll of their 
warez and analytics games about me through the phone services I (or someone dear) pays hard earned 
money for. Let me emphasize a bit of bitterness here that I think should be equalized from the snippets 
in the README:
```
<string name="should_download_over_metered_prompt">The selected language on your mobile device has an available dictionary.&lt;br/&gt; We recommend &lt;b&gt;downloading&lt;/b&gt; the %1$s dictionary to improve your typing experience.&lt;br/&gt; &lt;br/&gt; The download could take a minute or two over 3G. Charges may apply if you don\'t have an &lt;b&gt;unlimited data plan&lt;/b&gt;.&lt;br/&gt; If you are not sure which data plan you have, we recommend finding a Wi-Fi connection to start the download automatically.&lt;br/&gt; &lt;br/&gt; Tip: You can download and remove dictionaries by going to &lt;b&gt;Language &amp; input&lt;/b&gt; in the &lt;b&gt;Settings&lt;/b&gt; menu of your mobile device.</string>
```
Now, the makers of this abominal software know god damn good and well that in most cases the constant traffic 
from their covert service is going to incur the victim a monetary penalty. My father, for example when he was still 
stuck in a contract agreement with Verizon Wireless is owed several thousands of dollars in overages at the rate 
of $400-600 a month. However, prosecution is impossible without a federal US district judge and a British ambassador 
since the company that profits from the thinly veiled mSPY invasision are in Europe, not in the US. 
They choose to snake the issue as any 
good Luciferian lawyer might do, and justify it anyway. I may be of traditional ethnic something and sploiled, 
but I have seem the light *AND SOCIAL JUSTICE IS GOOD*! I sincerely hope that I'm not the one who has to work out 
the reverse engineering details to this hallelujah of our times, as surely I already have 2-3 tasks I can responsibly 
chug through on the weekends for this project. 


## Adding a few more permissions (ACL-type per-application of granular permissions)

Full control over so-called "system apps", which except for with easy malware, is an 
unattainable dream for well-intentioned applications that could actually make good use of it. 
This regime should in general be replaced by a much finer grained ACL-style permissions handling, 
but such apps are no longer special on **MY** angry enough Droid unless I deem them to be truly 
necessary. Some google music apps, Sprint carrier services when I'm on a different network, etc, 
should be, and will can be removed at will (after they are reverse engineered sufficiently to 
be dispensed of completely, of course). 
I also have an idea to use [apg]() in very small binary form at boot time to generate a sort of 
one time (single session long) key which we will use to help identify the *sudo* user that determines 
the rules. We could also boot into a substantially more or less priveleged system using securelevels 
(unless Android has stripped the Linux kernel to turing Java-only tricks). The one-time-key approach 
sounds like a sane way for me to approach me phone day to day. 

## Good ideas

system loggers (git)
system firewall (pf is nice)
chain of trust for the bad news policy that is the Google Play Store
tripwire (or whatever is most current now, and ability to set backup points -- for 
example, if a Google service were to be observed descrating my privacy, and I decided 
to forcefully kill it, we want to make sure there's a restore point that will yield a 
functional system with only one reboot ... ) 
a default ssh client throughtfully configured: For this I have in mind 
[SSHDroid]().
A windows-2000-era-like task manager for easily killing slow apps, seeing CPU / memory specs 
(probably should be loosely ``top`` based, in light that Linux's is better than on the Mac). 
Ability to insert randomized chaos into the work of the analytics devils that lurk on my system: 
Randomize mac address, hostname, device serial, Google ad ids, *anything* whatsoever that comes 
up when an application wants to abuse my IMEI data to identify me in aggregate databases and individually; 
Also, can randomize hotspot AP names, passwords, bluetooth hardware stuff, etc; 
Chrome -- or a less nosy replacment for it's function on my system -- should easily have the ability to 
print webpages to PDF (ala htmldoc). 
Ability to generate binary coredumps; Active memory scanning by privileged system profiling apps; 
Ability to set *any* application to the TEST_APP. This will poke at 'ol Google to reveal it's logs and 
intents, and as above, any precious memory it doesn't think I should see. There's a default android Instrumentation 
class to let non-sudoer users prod at suspicious apps. 
Need an anacron daemon to maintain sanity; 
Ability to set the data direction of USB (i.e., disable USB-C phone like bidirectional exchanges, and instead 
block the incoming (outgoing) side of the conversation. 
Adderall Beam signal (encrypted, and untraceable); 

### Pet peeves that will save my phone from the wall over time

The developer options enables USB (only!) debugging to initialize ADB connections with the target device. 
When, in principle, this does work, it will prefer and inextricably charge itself to 100% before feeling the 
need to exchange any actual data with the PC it is connected to. I think that >=85% is enough to sustain an 
APK upload, so this behavior should have an override setting. 


## Necessary mini-tools (Linux user creature comforts) 

Any one who takes up the argument of why said next utilities really ought be required is 
a Unix / Linux novice who will install bad-news security tools to piss off the technical 
karma that be. In other words, a fine tuned appreciation of these novelty comforts is 
a desired thing: figlet + cowsay + fortune-mod + [my math fortune mod]() + lucky numbers printed in the 
form of [OEIS sequence numbers and entries](). I have also expressed myself through artistic 
outlets instead of screaming and bitching too much [here](). The (extended) set of GEyes applets 
I have crafted for female, male, and other elite software users shall not be neglected as a 
desktop component in my project. 

### Smallish commandline tools that could be useful

zip, gzip, bzip, rar, color-grep, color-ls, flex / bison (see my NFC emulation ideas above), 
dd (see [this possibility]()); lsusb, lspci, ls*droidhardware; sed/awk (NO PERL, NO PYTHON); 
binutils (+strings), the binwalk reveng tool, etc; avr dude because Chameleon's are around; 
bash over sh; honeypot software (why not all things considering); 
The ascii middle finger as an /etc/issue file. 


## Things that would eventually be nice to include as features

dual boot of custom Android ROMs so I can actively deploy **AppUse** (which I take to heart on principle) 
manufactured by AppSec Labs. This, it seems to me takes away my initial thoughts on building in a sandbox or 
mock-data'ed up chroot setup to torture test and expose all the crap that comes on even the barebones Droid I 
picked out for myself. It's often best to leave it to the most inclined and skilled minds to torture test something 
even if it might have been a fun hobby for me to muse at trying to understand and develop. 


