---
slides: example
url_pdf: ""
title: Intrusion Detection System For Home Networks
summary: ""
url_video: ""
date: 2016-04-27T00:00:00.000Z
categories:
  - Tech
  - Cyber_Security
  - Development
external_link: ""
url_slides: ""
subtitle: A cost effective solution for the security of home networks by
  monitoring and detecting potential threats using Suricata Intrusion Detection
  System and Elastic Search , Logstash , Kibana for visualization and reporting.
tags:
  - Cyber_Security
links:
  - url: https://docs.google.com/presentation/d/1n8OcMsegMK0wrCqM6DqOOri1Ud5AHyEp/edit#slide=id.gdb70e5b088_0_91
    name: Slides
image:
  caption: ""
  focal_point: Smart
  filename: featured.jpg
url_code: ""
---

Since electronic devices are becoming cheaper by the day, it is
very easy to own one by the common man. From buying clothes to
ordering food, applications on our phone take of our needs in our
daily lives. These applications on our phones have a variety of
payment methods, some of them store card information, some are
directly linked to our bank accounts and at the click of a button we
can send and receive money.
For example, a cyber security researcher found out that a certain
smart fridge from a reputable company had been infected with
malware and was being used as part of a botnet which had been
deployed in millions of homes. These malwares could lie dormant
in many of these devices and would be difficult to detect and
manage by the common user. By connecting our devices such as
cell phones and corporate devices we are allowing the spread of
harmful viruses on the network to our devices. For example, an
application such as a keylogger, if installed on a person’s phone
would render all forms of authentication useless as it can read all
the one time passwords as well as RSA tokens from different
applications and causes harm to the entire organization.
The current solutions which are based on the cloud are complex to
implement and difficult for a common user to understand and
implement. The nature of cloud also makes managing the service
difficult and expensive and can be done only by professionals who
have experience with the deployment and maintenance of these
applications. Various anti-virus software’s are expensive and most
of the end users will not have them installed or renewed on their personal devices as they rely on their vendor who provides updates
only up to two to three years. Hence if an attack occurs in a home
network there are very little chances that an end user will be able
to identify, analyse and take effective measures to mitigate the
threat.
The solution discussed in this project helps the common man
understand what is happening on their network without the need to
understand the networking infrastructure. It provides a high level
of abstraction by displaying easy to read dashboards with alerts
which then can be easily identified and appropriate action can be
taken. All the data passing through the network is collected by
various tools such as Wireshark and is continuously sent to the
intrusion detections and prevention system and the ELK stack to
be analysed. The entire solution is deployed on a simple one-click
command install which takes maximum of five minutes to
implement. Since we have deployed the solution on a docker
container, the image provides us with a stable, up to date version
of the software which can be packaged, maintained and replicated
easily.
Various intrusion detection tools have crowd sourced signature
detection of latest malwares being updated frequently which
allows it to detect malicious traffic with ease. This ensures that the
end user can is aware of the network performance and malicious
traffic in an easy to understand way. Hence our project provides a
simple, easy to use and maintainable solution to manage cyber
threats at an affordable cost for the common user. These
dashboards can also be shared to various cybercrime departments
for further analysis and also this data can be used by machine
leaning algorithms to help identify the patterns of attacks and
predict the occurrence of new ones.