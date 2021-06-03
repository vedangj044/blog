+++
title = "GSOC, Drogue IoT & the Community"
date = 2021-06-01
category = "GSOC"

[extra]
author = "Vedang Joshi"

[taxonomies]
tags = ["GSOC", "DrogueIoT", "IoT", "Github", "Open source"]
+++

This year, I got an opportunity to work as a Google summer of code student at [Drogue IoT](https://github.com/drogue-iot), which is a part of the JBoss community ( Red Hat or IBM ).

### Understanding the project

While looking for organizations on the GSOC website, I came across the idea list of the JBoss community. It had only 3 ideas all from an organization named Drogue IoT. I read those, but barely comprehended any, but I was curious so I went to their Github, blog, and matrix channel. To help myself understand what their project is, I started reading some of their earliest [blogs](https://blog.drogue.io/first-steps-in-iot/). I read that, and one line just clicked me, which was

> "Plus, given it's a known problem domain with at least one known solution to me, I can concentrate on the implementation, not on the specification and design."

So, It's okay to do everything by hand when we have one device. But we can't do this at scale. There needs to be a system that sits in between devices and applications, to handle everything, from configuring devices to sending them commands. This is what  Drogue Cloud does,

> Device <-> Drogue Cloud <-> Applications.

I loved this idea. Something more fascinating was the tech stack - Rust, Knative, Kafka, etc. I introduced myself on the community channel. I worked to understand each component of the tech stack. I started to play around and learn Rust, the best resource to do so is undoubtedly [The Rust Book](https://doc.rust-lang.org/book/). Everything was new to me, so I was extremely happy to get to know so much. 

Drogue IoT also focuses on the device side of things. Drogue device brings reusable components to the embedded side, this is done by an async actor framework written in Rust. I don't understand much of it but I want to learn more and contribute to it at some point, maybe after GSOC. ;-)

### Community bonding and contributions

When I came across this organization around mid-January, I was interested in a "Hey Rodney" project, which is based on using voice commands to control Kubernetes. I researched about it but soon my interest faded. I came across a repository named [DRG](https://github.com/drogue-iot/drg). It is a command-line client to communicate with Drogue Cloud API, which helps us manage devices and apps. I discovered some issues which I could solve, so I started right away.

I love the community and the people at the organization. Everyone is immensely experienced, and an inspiration. I think it is a privilege to get an opportunity to work with such amazing people, that too sitting at home.

I contributed to some patches in DRG, working with Jean-Baptiste Trystram. He was very supportive and guided me with my PRs.  I think this experience is larger and better than any internship I may have got, and this is the beauty of Open-source.

I look forward to contributing and giving my best in the GSOC period and later too.

### My project

I would write a separate blog entirely focused on my project, but here is a little glimpse of it. My project is about facilitating a DRG user with the ability to create X.509 certificates for a device, and a Trust Anchor ( root CA ) for the apps.

> Apps: Applications are isolated containers for a collection of devices.

> Devices: Devices ideally map to a physical device, and are owned by exactly one application.

Now, these devices can be authenticated using Username and password combinations, but it is not a good idea to do this at scale. The solution lies in the trust anchor flow.
An app ( which owns the device ) has its root certificate and a private key. This key is used to sign the certificate flashed on the device. Whenever the device connects, it presents its certificate which is cryptographically verified with the App's public key. 

This helps establish a One-to-Many mapping and provides a secure authentication mechanism for any number of devices.

Drogue cloud already has the support for X.509 certs. DRG can abstract away many parts of this process. So, this is what we have to do.

More blog to come on this topic, and as always

Thanks for reading.