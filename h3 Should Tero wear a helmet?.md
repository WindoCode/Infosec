h3.md



# Braiterman et al 2020: Threat modeling manifesto

Threat modeling is a structured approach used in cybersecurity and software development to identify and manage potential security threats and vulnerabilities in a system, application, or environment.

In general, when threat modeling is done, one has to ask four key questions:

What are we working on? 
What can go wrong?
What are we going to do about it?
Did we do a good enough job?

## Why threat modelling?

Threat modeling is a structured approach to understand what could go wrong in a system. It helps pinpoint problems in design and implementation that need to be addressed, whether it's early on or later in the system's life. The output of a threat model, called threats, guides decisions in how to build, test, and secure the system.

## Who should threat model?

Everyone! Or anyone who is concerned about privacy, safety, and security of their software,hardware, you name it.


## How should you use threat modelling manifesto?

The authors of the manifesto wants the user to take ideas from the manifesto and not treat is as a how-to guide. The Threat Modeling Manifesto follows a format by identifying the two following guidelines:

1. Values: In threat modeling value refers to the relative worth, merit, or importance of different elements. Sometimes one needs to prioritize items on the left over items on the right.

2. Principles: In threat modeling principles describe its fundamental truths. There are three types of principles. (I) fundamental, primary, or general truths that enable successful threat modeling, (II) patterns that are highly recommended, and (III) anti-patterns that should be avoided.

One example of threat modeling principle is that the best use of threat modelling is to improve security and privacy of a system through early and frequent analysis.

One good example of recomended pattern is by systematic approach. It is considered good to apply security and privacy knowledge in a structured manner. This way you can achieve thoroughness and reproducibility.

Great example of anti-pattern in threat modelling is to overanalyze your problem: Admiration for the problem. You should try to reach practical and relevant solutions, when a problem is found.


# Shostack 2014: Chapter 1 - Dive In and Threat Model! 

For this I try to bring some core ideas from the videos! (Ideas numbered by points, not videos)

1. Why threat model? To anticipate problems when its still inexpensive to deal with them. (when still on drawing board).

2. The four question framework for threat modelling. What are we doing? What could go wrong? What we gonna do about it? Did we do a good job? For these questions we can use structrues or models to get more consistent and in-depth answers.

3. What are we working on? The best way to start thinking about this question is sketching. By writing or drawing the possible idea we find a starting point to the idea. Through collaboration we can refine and find the answer to the question.

4. When modeling an idea or a product it is important to keep records of your modeling work. This helps to go in detail and answer to the question: What could go wrong?.

5. Data flow diagrams. This is good model when thinking about the questions of threat modeling. Diagram uses five elements. 

External entities, represented with sharp corners, to remind us what is not under our control. 
Processes: Round corners to remind that it is under our control. This can be in example a code.
Data flows: Arrows to connect diffrent parts.
Drums: Represent where data is stored.
Trust boundaries: Line around elements what is our control.

6. What could go wrong? We want to ask the question and pay attention the the answers. If we need consistency, we can use models like STRIDE or kill chain to find more detailed answers.

7. STRIDE is a fundamental building block for threat modeling to create consistency. These problems happen on everything, ranging from software to cloud. Finding problem that fits to every problem listed under, adds security!

Spoofing
Tampering
Repudiation
Information Disclosure
Denial Of Service
Elevation Of Privleges.

a.k.a STRIDE.

8. What we gonna do about it? Risk management. If we put problems on a line, on the other end we fix them and on other side we won't fix them. Risk management sits at the middle and decides, which problems are severe or probable. If problem is going to happen certainly and is severe to software. It is going to be fixed.

9. Did we do a good job? If people feel around threat modelling was worthwhile and they would recommend it to collegues. You did a good job. If the answer is no, you didnt do every step well enough.




## OWASP CheatSheets Series Team 2021: Threat Modeling Cheat Sheet

Threat modeling is a critical process within the realm of cybersecurity, providing a structured approach to identifying and prioritizing potential threats to a system. It serves as a proactive measure, enabling organizations to assess the security of their software, systems, or applications. By systematically examining how data flows through a system and identifying trust boundaries, threat modeling unveils vulnerable points where an attack might occur. This comprehensive approach not only helps in understanding the potential risks but also allows for the documentation of security controls that can mitigate these threats.

Regardless of whether it's an existing system or a new development, incorporating threat modeling in the software development life cycle is highly advantageous. Early implementation of threat modeling, ideally during the design phase, proves especially valuable, saving substantial resources that might otherwise be required for retroactive risk mitigation. This strategic foresight equips developers, architects, and designers with a clear blueprint of the system's architecture, aiding them in making informed decisions about potential security measures.

The terminology surrounding threat modeling, encompassing terms such as threat agents, impact, likelihood, and controls, provides the necessary framework for a robust threat assessment. These concepts empower individuals to not only identify potential risks but also evaluate their severity and likelihood of occurrence. Through threat modeling, organizations can holistically understand their systems, fortify potential weak points, and establish a more resilient security posture. In this way, threat modeling transcends a mere security exercise, emerging as a fundamental aspect of designing and building secure and resilient applications and systems.


## Security hygiene. 
- Use diffrent passwords for diffrent accounts.
- Never give any one your password.
- Use 2-Factor Authentication.

Above average Joe, that I use:
- Using password manager for most accounts.
- Deleting accounts that I am not using
- GDPR remove data requests


## Make-belief boogie-man - a threat model for imaginary company.

What are we working on?

This diagram shows the infrastructure of our 10-person cloud development company, showcasing the key assets and their interrelationships.

At the center of the diagram is the "Cloud Development Company", which is pretty much our company. Surrounding it are various critical assests that collectively support our company's operations:

1. Source Code Repository:

This repository serves as the foundation of the company's intellectual property, housing the source code for its software solutions. It is a pivotal asset for ongoing development and business.

2. Customer Data Database (Cloud)

This database is dedicated to securely storing sensitive client information. It's a critical asset that demands robust security measures to ensure data confidentiality and integrity. This information is stored to 2 parts. Non-critical and critical. Non-critical information could be customer's own data, which is stored mainly on cloud side. Critical information, such as personal data, is stored on our private databases.

3. Development Environments:

This section encompasses servers, databases, and platforms used for coding, testing, and deploying applications. These environments are the operational backbone of the development process.

4. Private cloud

This cloud contains storage infrastucture, critical customer information, developement tools, RBAC, security and access controls, networking infrastucture.

![image](https://github.com/WindoCode/Infosec/assets/110290723/31826d32-1ad5-4a72-8275-ed26c6917754)


## STRIDE for diffrent company systems

### Internal systems

Threats against our own systems: Private cloud, HR-managment, Developement systems. 

Among the identified threats, the three most severe for company data are Spoofing, Tampering, and Information Disclosure. These threats have the potential to cause significant harm to the confidentiality, integrity, and availability of the company's data. Implementing robust authentication measures, data integrity checks, access controls, and encryption are crucial steps in mitigating these threats and safeguarding the company's valuable data assets. Additionally, regular security training and awareness programs can further enhance the overall security posture of the company.

Example case: If authentication measures are not robust enough, An attacker could impersonate a legitimate user to gain unauthorized access to our private cloud. How can we take measures against this? 

1. Multi-Factor Authentication (MFA): Enforce MFA for added security. 
2. Strong Password Policies: Require complex passwords. 
3. User Training: Educate on security best practices. 
4. Continuous Monitoring: Detect and respond to suspicious activity.

### External systems

Threats against our partners such as cloud provider: DoS

If our cloud provider, which hosts critical services and resources for our company, is potentially under a DoS attack, we could be under these kind of threats:

1. Service Disruption: The redundancy of our services and resources hosted on the cloud provider's infrastructure will be severely affected. This can lead to downtime for our customers and users.

2. Loss of revenue: Downtime may result in financial losses due to agreement penalties.

3. Reputational damage: Our customers may lose trust to our company to deliver the service. Also may lead to decreased customer satisfaction.

To tackle these potential risks and vulnerabilities we need to form a mitigation plan. To lower our dependancy of our external systems, we can:

Diverse the use of cloud providers: This comes at a cost, but by using multiple cloud providers we can make sure that our service level maintains a suitable level.

Monitor the incidents with transparency: Having incident response plans in place ensures a swift and effective response to any disruptions or security incidents. This proactive approach minimizes the potential impact and downtime caused by security breaches or incidents. 

Also keeping customers informed about the situation by addressing the issues.


## Did we do a good enough job?

I would like to hear feedback from you guys! What are the weaknesses of this plan? Did you manage to find blind spots while reading this text? Let me know in the comments or contact me during class!

**Extra: Last week inspired me to make my own PostgreSQL database using Docker and DBeaver. Check it out! [Link to GitHub](https://github.com/WindoCode/PostgresDocker)**
