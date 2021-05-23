+++
title = "Hello World!"
date = 2021-04-14
category = "Other"

[extra]
author = "Vedang Joshi"

[taxonomies]
tags = ["Arduino", "ESP", "other"]
+++

It was a summer afternoon, back in 2014. I was restless, pacing around the hallway of the school corridor, I looked at the clock and then at my friend - Aniruddha. The prize distribution ceremony was about to begin, we rushed our way downstairs, looking for seats. The ceremony had started, I was nervous, the names of the winners were called out one after the other. Now it was time for our “Theme”, and suddenly Aniruddha’s name was called, he secured 3rd position, I was happy for him. One more name who secured 2nd position was called which was not me. I could hear my heart beating now. It was a moment longer than usual, Anirudhda returned after collecting his prize and sat beside me, I had my eyes closed, my leg shaking.  

> “Vedang Joshi for Automation of warehouse systems” the anchor called.  

Suddenly, all anxiety vanished. I had won this state-level science exhibition, all the talent and sweat I put into my project has fructified now. I shook hands with Aniruddha and went to collect my prize.  

This was the first time I had achieved something out of my comfort zone. This project is not on my resume but in retrospect, this incident has always encouraged me to work hard and choose challenging tasks.  

Let’s get to technology now, I would tell you what was the idea of this project.

### Automation of Warehouse

The idea was pretty simple: We paste RF-ID tags on each product stored in a warehouse. A robot equipped with an RF-ID reader would scan that tag, pick up that product and hand it over to us. Thus, we get a completely automatic warehouse.

I started with a toy JCB and connected it to a motor driver ( L293D ) and then to an Arduino UNO. I played out with this setup for a while. I now had to control this over the internet ( or local wifi for the demo ). I plugged in an ESP-01, and using AT commands, initiated a local server. Now, I should be able to send commands from chrome to this server, but unfortunately, it didn’t work. I debugged it and found ESP’s server turned down the moment I requested it from my browser, good people on the Arduino forum told me it was because of the low current from Arduino.  

I bought a simple 3.3v regulator and plugged the ESP directly into a battery, it still didn't work. I tried a few more things before I gave up on ESP. :grinning:	
I switched to the HC-05 Bluetooth module and it was pretty awesome, I found an app on the play store - Bluetooth terminal, it was just a serial monitor but over Bluetooth. It’s time for the RF-id sensor now,  I bought a few plastic boxes and pasted RF-ids on them, these would resemble the products in the warehouse. Soon, I realized I was using the RF-tags working on a different frequency than the reader ( MFRC522 ). I had to change that.  

Now, somehow with tons of patchwork, everything seemed to be working. It’s time to learn JAVA and create an Android app. The purpose of the app was pretty simple, you see a list of products, you choose any product that interests you, and click on “Order”. This sends a signal to the toy JCB, which scans and looks for the proper RD-id, picks up the right product, and gets it to you. I had no idea of what databases are, so for the 10 products I had, I created a long chain of if-else statements.  

Now the main challenge was to send a signal to the Arduino which required knowledge of Bluetooth, which was obviously out of my league. So, I went back to my favorite app - Bluetooth terminal extracted its apk, unboxed it to dex files, and converted it to dex2jar. Thus reverse engineering my way, I was able to simply copy and paste the code in my app.  After hours of pain, everything was working and I was ready for the demo.  

Hopefully, this was just the beginning of my computer science journey.  
