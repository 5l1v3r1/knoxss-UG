** Quick Start...**

1. Go to [KnoXSS site] (https://knoxss.me/pro) and login

2. Download the FF plugin

3. Keep your account logged in at all times in FF

4. Now start the XPI plugin and switch to ON for the target site

5. It's ideal to pass your XPI requests through Burp or ZAP to ensure the XPI is actually behaving in an intended way (headers not truncated or misplaced etc)

6. If not successful through XPI to get a XSS popup, try with the [Pro] (https://knoxss.me/pro) directly and try out some trial and error Extra Data (this depends on what is being used by the application towards Auth Data)

 
# knoXSS User Guide

***KnoXSS is an automated XSS scanner with PoC response by @brutelogic. This documentation is a User Guide for KnoXSS***

***Special thanks to @Random_Robbie for his inputs***



**Bought KnoXSS, Now What:**

I'm assuming you've procured the pro license - This seems to be the best bet just like Burp Suite Pro, 'cos your very first XSS using this tool might be your ROI

However, if you're still thinking about procuring KnoXSS, first go to [KnoXSS] (https://knoxss.me) and register for a free account.. Using the free version will give you a good idea of how you can use the online tool effectively... It's a mostly self-explanatory **point and click** type of tool

You can try some [sample sites] (http://brutelogic.com.br/knoxss.html) and see whether KnoXSS finds any XSSes there... Once you're satisfied, may be you wanna' get the pro?

Once you've got Pro:



**Testing the Waters:**

1. Go to [KnoXSS] (https://knoxss.me/pro) and login if prompted

2. You can return back to the [test pages] (http://brutelogic.com.br/knoxss.html) to get yourselves acclamatized... Please be aware that the [test pages] (http://brutelogic.com.br/knoxss.html) are a work in progress...  

3. Paste the provided sample URLs into the [KnoXSS] (https://knoxss.me/pro) site



**Using the XPI - Firefox Extension**

1. Go to [KnoXSS site] (https://knoxss.me/pro) and login

2. Download the FF plugin

3. Keep your account logged in at all times in FF

4. Now start the XPI plugin and switch to ON for the target site

5. It's ideal to pass your XPI requests through Burp or ZAP to ensure the XPI is actually behaving in an intended way (headers not truncated or misplaced etc)

6. If not successful through XPI to get a XSS popup, try with the [Pro] (https://knoxss.me/pro) directly and try out some trial and error Extra Data (this depends on what is being used by the application towards Auth Data)





**FUQs: (Frequently Unanswered Questions): **

***ONE:*** What should be in "Extra Data" for POST requests or How to handle POST requests?

Let's say we want to scan **http://someurl.com** for XSS using [KnoXSS tool] (https://knoxss.me/pro)... Let's say this is a POST request with the following as the full request:

***Start***

```
POST /app/core.security.login.event HTTP/1.1
Host: someurl.com
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:45.0) Gecko/20100101 Firefox/45.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: https://someurl.com/app/login.jsp?TYPE=33554433&REALMOID=06-00045ffb-9d34-1d53-ba41-024a0a174072&GUID=&SMAUTHREASON=0&METHOD=GET&SMAGENTNAME=-SM-c0YcVaq2Y%2fJgCFwUxzl%2bFjGUYRdw1odmO6FnFo8ALHEWVne0mzqAGJ5gcfrpupN1&TARGET=-SM-https%3a%2f%2fs2b%2esomeurl%2ecom%2fapp%2fcore%2ehomepage%2eshow%2eevent
Cookie: BD1=14846538758084658965091235329142; BD2=14846538758095410991436877103468; javax.servlet.http.Cookie@61466146=""; javax.servlet.http.Cookie@61a661a6=""; JSESSIONID=00012Fj5NP0q15MeH_T179VoQ9o:14bth2u81; WB_LANG=en; ak_bmsc=CA80C1C75F6B260FE672C9CA252C24FB3A1AB98B512B00006FA280585449566C~pl3yxbQlcdDrg0GYKOfEm4TgyyUM9KkeHpL2ktmiK8+6EFPThPTWbf2pQKhSzCZWLO2evhKPTjyfhYjTXddIv+tyUEn1k7Xvab2/yGIeGmBBTB1VCyQ5HjiT17iFebKSQ3nIP8QjWir217JCpydqyP/j3MzuZfChHZ0qqHoF2be8uYdyNRKQEoJ9tWNzwWI1z7B+yF4nEkOXZ9oolI0hCiwaH1/atMeWWYFaCJwvHPrZE=
Connection: close
Content-Type: application/x-www-form-urlencoded
Content-Length: 34
 
_gid=groupkk&_uid=userkk&langid=en
```
***End***

For the above example, when I click on the *Extra Data* button, this is what I would need to paste:

***POST Data:***

```
_gid=groupkk&_uid=userkk&langid=en
```
***AUTH Data:***
The ***Cookie: and Referer: headers*** to be pasted here, so in our case, it will be:
```
Referer: https://someurl.com/app/login.jsp?TYPE=33554433&REALMOID=06-00045ffb-9d34-1d53-ba41-024a0a174072&GUID=&SMAUTHREASON=0&METHOD=GET&SMAGENTNAME=-SM-c0YcVaq2Y%2fJgCFwUxzl%2bFjGUYRdw1odmO6FnFo8ALHEWVne0mzqAGJ5gcfrpupN1&TARGET=-SM-https%3a%2f%2fs2b%2esomeurl%2ecom%2fapp%2fcore%2ehomepage%2eshow%2eevent
Cookie: BD1=14846538758084658965091235329142; BD2=14846538758095410991436877103468; javax.servlet.http.Cookie@61466146=""; javax.servlet.http.Cookie@61a661a6=""; JSESSIONID=00012Fj5NP0q15MeH_T179VoQ9o:14bth2u81; WB_LANG=en; ak_bmsc=CA80C1C75F6B260FE672C9CA252C24FB3A1AB98B512B00006FA280585449566C~pl3yxbQlcdDrg0GYKOfEm4TgyyUM9KkeHpL2ktmiK8+6EFPThPTWbf2pQKhSzCZWLO2evhKPTjyfhYjTXddIv+tyUEn1k7Xvab2/yGIeGmBBTB1VCyQ5HjiT17iFebKSQ3nIP8QjWir217JCpydqyP/j3MzuZfChHZ0qqHoF2be8uYdyNRKQEoJ9tWNzwWI1z7B+yF4nEkOXZ9oolI0hCiwaH1/atMeWWYFaCJwvHPrZE=
```
* If in doubt, paste the entire HTTP header into the AUTH Data field and check again

* I personally feel that this window needs to be closed with a Save button rather than just clicking on the X at the top... However, please note clicking on the X does make the pasted values remain persistent

***TWO:*** But how do I capture the POST request to paste into *Extra Data* fields, in the first place?

Easiest way is to use any interception proxy such as [Burp Suite] (https://portswigger.net/burp/download.html) or [Fiddler] (https://www.telerik.com/download/fiddler), intercept the request and paste that data into the fields

***THREE:*** Is there some way to know how many requests are being made by ***KnoXSS Pro***? I dont see any log, hence the question - this is especially important when the result says no XSS found

Tool author @brutelogic's comment: A log feature is being implemented, it will not contain this info in the first release but will come in future developments. To be sure there's no XSS, you can check target manually 

You can always see the requests with burp or which ever proxy you use this is handy to see what response knoxss has provided.

***FOUR:*** What happens when the number of users performing the scans go up?

Server will hang if the CPU reaches 100% for sustained periods (several seconds). Currently it doesn't pass 30% even with the heaviest concurrent load. 

***FIVE:*** When I asked @brutelogic " I tried using KnoXSS on some of the sites which have been shown as vulnerable on the [Open Bug Bounty] (https://openbugbounty.org) site, but Knoxss was unable to detect them... So want to know what mistake I was doing

**My Meeting With Robbie**

Please ask @RandomRobbie, several of his findings with KNOXSS ended up as submissions there. You might be doing something wrong, KNOXSS can find almost all the simple cases featuring in openbubounty.org

I sent out a request to @RandomRobbie to help out at his convenience and you know what, I received more than I asked for, all within the next 2 minutes!! Wow, the infosec community never ceases to surprise me... Everyone is so eager to share and have so much to as well!! 

Inputs from @RandomRobbie: **Always check the full paremeters have been sent via knoxss plugin if not re test the site and ensure you provide knoxss with the cookies and the CRSF tokens if there are any. **

Some more inputs from him during our discussion: (Pasted straight from Twitter DM)

- One main thing I do with knoxss is ensure **it's ran via burp** so i can see the response from knoxss as sometimes knoxss does flake out with a 404 if the url has too many parameters or is taking ages to respond

- Another one with knoxss is if the firefox plugin does not detect any thing, **a manual check on the main page is always advised and ensuring cookies and CSRF tokens are put in**

- I have found in the past that some sites really dont like KnoXSS and thats something i am trying to work on

- If you put a manual XSS in that did not fire, the extension will fire this to knoxss and fail due to the WAF

- The way I have it set up is my firefox goes via burp and you can see the requests from knoxss plugin

- **sometimes you need to sign in to knoxss as the addon isnt always working**

- The firefox plugin is just doing a POST to the knoxss website


***SIX:*** You say there's some challenge the author of KnoXSS is facing with the Firefox Add-on (the XPI file)... If everything is working fine in Pro version shouldn't it also work the same on the XPI?

Tool author @brutelogic's concern: The Add-on is currently facing several implementation challenges due to Mozilla's API. Even if using the Add-on to just send targets to KNOXSS to test them, it's advised to (re)test using the main interface. 

This git is a work in progress and things will keep changing with the tool's maturity... So dont forget to Star and Watch

