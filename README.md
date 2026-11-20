# Network Log Analysis

I built this to practise spotting suspicious activity in network traffic. It uses Python and pandas in Google Colab to look through a practice log of network connections.

The log shows when each connection happened, which computer started it, where it went, which port it used and how much data it sent.

## What I did

I started by counting how many connections each computer made. One was busier than the rest, but nothing looked unusual on that alone.

Then I added up how much data each computer sent, and one stood out straight away. The device 10.0.1.23 had sent hundreds of millions of bytes, far more than anything else on the network.

When I filtered the log down to just that computer, three things looked wrong. The big transfers started around 3am, when nobody would normally be working. All of that data went to one address, 45.33.12.9, which sits outside the network. And by the morning, its traffic had gone back to looking normal.

Put together, that looks like data exfiltration: a compromised machine quietly sending data out overnight.

## What I took from it

The biggest lesson was that a number on its own doesn't tell you much. Thirty connections or a million bytes might be normal for one machine and a red flag for another. What made this device stand out was the timing, where the data went, and how different it was from its usual behaviour.

Next, I want to work out what normal looks like for each device and flag anything that breaks the pattern automatically, rather than spotting it by eye.
