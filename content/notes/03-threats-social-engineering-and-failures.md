---
title: "03-threats-social-engineering-and-failures"
aliases: 
tags: 
- comp210
- lecture
sr-due: 2025-01-02
sr-interval: 521
sr-ease: 250
---

# News
- kiwis urged to get new passwords by government cybersecurity agency ("big password energy")
- ukraine cyber agency reports cyber attack surge
- plymouth households hit by clarion housing cyber attack
- facebook "unintentionally uploaded" 1.5 million peoples email contacts without their consent
- threat maps: https://threatmap.checkpoint.com/ThreatPortal/livemap.html

# Threats
events are circumstances that has the **potential** (risk) to adversely affect assets (reducing their value)
- e.g., possibility of text messages stop working -> phone loses value

# Attack
intentional or unintentional (e.g., lightning) **acts** that can damage or compromise assets.
- the actual act of attacking
- can be passive attack: e.g., stumble accross information accidentaly

# Exploits
- the **techniques** used

# Vulnerabilities
- the potential weaknesses in assets or in their defensive control systems
- e.g., try to find weakpoints in a castle

# Arms race
security is a never ending arms race. Security is improving but so are the number of potential exploits

# 12 groups of threats
![](https://i.imgur.com/d5i1wpA.png)

## Intellectual property
- creation ownership and control of original ideas
- common breaches include software priracy
- two organisatons investigate software abuse
	- software and information industry association (SIIA)
	- business software alliance (BSA)
- enforcement of copyright laws has been attempted with technical security mechanisms (e.g., watermark, you need an account, must register the software, etc)

## deviations in quality of service
- when a product is not delivered as expected
- info systems depend of successful operation of many interdependent support systems
- internet, communications, power irregularities, all affect the availability of information systems
- internet:
	- ISP failures can considerably undermine the availability of information
	- outsourced web hosting assumes responsibility for all internet service as well as for the hardware and the web site operaing system software. 
	- terms of service ensure that these services are guaranteed
- communication and other provider service issues include
	- other untilities: telephone, water, wastewater, garbage collection
	- these all affect the companies ability to function
- power irregularities
	- pwer exess, shortages, losses
	- sensitive equipment vulnerable to and easily damaged by fluctuations
	- controls can be applied to manage power quality e.g., UPS

## espionage or trespass 
- unauthorized attempts to gain illegal access to information
- competitive intelligence vs industrial espionage vs cyber terrorism
- shoulder surfing 
- controls mark the virtual boundaries of an organisations
	- controls oftentimes let trespassers know they are encroaching on an organizations cyberspace
	- hackers use skill, guile, or fraud, to bypass controls protecting others information
		- expert
			- develop scripts and exploits
			- master of many skills
			- of create software (malware etc) and share with others
			- minority
		- novice
			- script kiddies
			- more common
			- use scripts written by experts
			- do not understand the systems the are hacking
			- packet monkeys: script kiddies that use worms to overload systems
		- cracker
			- cracks or removes software protections designed to precent unauthorized duplication
			- also crack passwords
		- phreaker
			- hacks the public telephone system to make free calls or disrupt services
			- more specific
- also includes password attacks
	- brute force- tried all possible combinations
	- dictionary - include information related to the target user
	- rainbow tables - a hacker with access to encrypted password, they can find the corresponding plaintext in a dataset called a rainbow table
	- social engineering - e.g., attacks as posing at IT professionals to gain access toa systems information (normally by contacting other employees)

# Forces of nature
- fire, flood, lightening, earthquake, eruptions, etc.
- can use controls to protect against these
- very dynamic
- unpredicatble

# Human errors or failure
- actions performed without malicious intent or ignorance (by an authorised user)
- inexperience
- improper training
- incorrect assumptions
- employees are among the greatest threats to an organisations data
- e.g, 
	- accidental deletion
	- revelation of classified data
	- entry or erroneous data
	- storage in unprotected areas
	- failure to protect information
- can be prevented with training, ongoing awareness activites, and controls

# Social engineering
- using social skills to convince people to reveal access credentials or other valuable information to an attacker
- used for a broad range of malicious activities through human interactions

![kevin mitnick quote](https://i.imgur.com/Q7ChU37.png)

Developing trust is a powerful technique in social engineering
- people are naturally helpful and trusting
- ask during seemingly innocent conversations
	- slowly ask for increasingly imprtant information
- lean company lingo, names of people, names, servers etc
- cause a problem and subsequently offer your help to fix it
- talk negatively about common enemy
- talk positively about common hero

Inducing strong emotions
- you won a prize etc
- excitement 
- fear
- confusion

information overload technique
- reduce targets ability to sctrutinize arguments proposed by attacker
- trigger by
	- providing a lot of information
	- providing arguments from an unexpected angle, whicih forces the victim to analyse the situation from a new perspective which requires additional mental processing

Reciprocation
- technique that exploits our tendency to return a favour
- even if first favour was not requested
- even if the return favour is more valuable
- double disagreement
	- if the attacker created a double disagreement and gives in one, the victim will have the tendency to ive in the other
- expectation
	- if the victim is requested to give the first favour, they will believe that the attacker becomes a future ally

tendency to obey authority
- milgram experiement

dont be a commitment creep
- people have a tendency to follow commitments even when is might be unwise

information exortion is the practive of requesting a ransom for your valuable information
- ransomware

# Attacks
represent intentional or unintentional acts that can damage or compromise assets
- range from petty to vandalism to organized sabotage
- defacing
- threats are rising
- cyberterrorism/warfare is much more sinister form of hacking

## Types of attacks
- Virus - code segments that attach to existing program and take control of access to the targeted computer
- Worms - replicate themselves until they completely fill available resources like memory and hardrive space
- Tojan Horses - malware disguised as helpful, intersting or necessary pieces of software
- Polymorphic threat - actually evolves to elude detection
- Virus and worm hoaxes - nonexistent malware that employees waste time spreading awareness about
- back door - gain access to system or network using known or previously unknown/newly discovered access mechanism
- DoS - attacker sends a large number of connection or information requests to a target
	- target becomes overloaded and cannot respond to legitamate requests for service
	- may result in crach or inability to perform ordinary functions
- DDoS - coordinated stream of requresets is launched against a target from many locations
- Mail bombing (also a DoS - attacker routes large quantities of e-mail to a target to overwhelm them
- Spam (unusoliciited commercial e-mail) - more a nuisiance than an attack, is emerging as a vector for some attacks
- packet sniffer - monitors data traveling over network, can also be used for legit purposes, but can be used to steal data
- spoofing -> technique used to gain unauthorized access; intruder assumes a trusted IP address
- pharming - attacks browsers address bar to redirect users to a illegitamate site for the purpose of obtaining private information .e.g., DNS cache poisoning
	- make the DNS change to point to an illegitamate site instead of the real site
- man-in-the-middle - an attack monitors (sniffs) the network packes, modifies them, and inserts them back into the network.

# failure
> A failure occur when our security mechanisms (controls), hardware, or information systems have failed to protect our assets

Technical Hardware Failures (or Errors) occur when an equipment is distributed containing a unknown or known flaw 
- They can cause the system to perform outside of expected parameters, resulting in unreliable service or lack of availability. 
- Some errors are terminal and some are intermittent. 
	- Intel Pentium CPU failure – the floating point operation bug (loss over 475 million). 
	- Mean time between failure (or mean time to failure): measures the amount of time between hardware failures or to failure.

## Spectre & meltdown
https://meltdownattack.com/

![](https://i.imgur.com/SI9QzRv.png)

## Technical Software Failures or Errors 
- Large quantities of computer code are written, debugged, published, and sold before all bugs are detected and resolved. 
- Combinations of certain software and hardware can reveal new software bugs. 
- Entire Web sites are dedicated to documenting bugs. 
- Open Web Application Security Project (OWASP) is dedicated to helping organizations create/operate trustworthy software and publishes a list of top security risks.

## The Deadly Sins in Software Security 
- Buffer overruns 
- Catching exceptions 
- Command injection 
- Cross-site scripting (XSS) 
- Failure to handle errors 
- Failure to protect network traffic (e.g., by not using WPA in a local wifi) 
- Failure to store and protect data securely (e.g., access control) 
- Failure to use cryptographically strong random numbers 
- Format string problems 
- Neglecting change control
- Improper file access
- Improper use of Secure Sockets Layer (SSL)
- Information leakage
- Integer bugs (overflows/underflows)
- Race conditions
- SQL injection
- Trusting network address resolution
- Unauthenticated key exchange
- Use of magic URLs and hidden forms
- Use of weak password-based systems
- Poor usability

# Technological obsolescence
> when antiquated/outdated infrastructure can lead to security issues

- Proper managerial planning should prevent technology obsolescence.
- IT plays a large role

# Theft
occurs when taking of another’s physical, electronic or intellectual property
- Physical theft is controlled relatively easily
- Electronic theft is a more complex problem as the evidence of crime is not really apparent (e.g., you don’t notice the theft as you would for a physical object)

# what to do
- Don’t panic!
- Knowledge and Education are key.
- You make more progress by fixing the problem than by fixing the blame. (H.B. Wolfe)