## How web works & Internet
 The connection between the customer to server is called internet. let's imagine that the internet is a road. On one end of the road is the client, which is like your house. On the other end of the road is the server, which is like a shop you want to buy something from.
 These have the many function such as,
  - Server - IP - HTTPS - DNS

 ## Functions detail
  # Server
   - Servers are computers that store webpages, sites, or apps. When a client wants to access a webpage, a copy of the webpage code is downloaded from the server to the client machine, where it is rendered by the browser and displayed to the user.
  # IP (Internet protocol)  
   - Internet Protocol (TCP/IP) are communication protocols that define how data should travel across the internet. This is like the transport mechanisms that let you place an order, go to the shop, and buy your goods.
   - In our example, this is like a car or a bike (or however else you might travel along the road)
  # HTTPS (Hypertext Transfer Protocol)
   - (HTTP) is an application protocol that defines a language for clients and servers to speak to each other. This is like the language you use to order your goods. See HTTP basics below.
  # DNS (Domain Name System)
   - This system uses special servers that match up a web address you type into your browser (like mozilla.org) to the website's real (IP) address. Large websites are commonly made available on multiple servers, so that they load efficiently for different users worldwide. As a result, the IP address may vary depending on where you are.
   - You can use a DNS lookup tool to find the IP addresses of a website. For example, go to the NsLookup.io DNS lookup tool, type in developer.mozilla.org, and press the button.

 ## So what happens, exactly?
  When you type a web address (which is technically part of a URL) into your browser address bar, the following steps occur:

- The browser goes to the DNS server and finds the real address of the server that the website lives on.
- The browser sends an HTTP request message to the server, asking it to send a copy of the website to the client. This message, and all other data sent between the client and the server, is sent across your internet connection using TCP/IP.
- If the server approves the client's request, the server sends the client a "200 OK" message, which means "Of course you can look at that website! Here it is", and then starts sending the website's files to the browser as a series of small chunks called packets.
- The browser assembles the small chunks into a complete web page and displays it to you.

  -[How the internet works (page)] (https://developer.mozilla.org/en-US/docs/Learn_web_development/Howto/Web_mechanics/How_does_the_Internet_work)
  -[How the internet works (video)] (https://www.youtube.com/watch?v=hlkAuFXHFWM)
