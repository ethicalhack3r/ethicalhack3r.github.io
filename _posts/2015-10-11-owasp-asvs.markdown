---
layout: post
status: publish
published: true
title: OWASP Application Security Verification Standard (ASVS)
excerpt: "A few days ago (October, 2015) the OWASP Application Security Verification Standard (ASVS) version 3.0 was released which I had the opportunity to contribute to in a small way by helping review some of the draft documents before the official release.
/r/n/r/n
I became aware of the OWASP ASVS as a growing number of my clients started asking if I used it. At the time I didn't use it but I decided to invest some time into finding out what it was. This blog post's intention is to bring some attention to the OWASP ASVS project for those unaware of it."
---

A few days ago (October, 2015) the [OWASP Application Security Verification Standard (ASVS)](https://www.owasp.org/index.php/Category:OWASP_Application_Security_Verification_Standard_Project) version 3.0 was released which I had the opportunity to contribute to in a small way by helping review some of the draft documents before the official release.

I became aware of the OWASP ASVS as a growing number of my clients started asking if I used it. At the time I didn't use it but I decided to invest some time into finding out what it was. This blog post's intention is to bring some attention to the OWASP ASVS project for those unaware of it.

##What is the OWASP ASVS?

The first version, version 1.0, was released in 2009.

According to the official project page.

> The primary aim of the OWASP Application Security Verification Standard (ASVS) Project is to normalize the range in the coverage and level of rigor available in the market when it comes to performing Web application security verification using a commercially-workable open standard. The standard provides a basis for testing application technical security controls, as well as any technical security controls in the environment, that are relied on to protect against vulnerabilities such as Cross-Site Scripting (XSS) and SQL injection. This standard can be used to establish a level of confidence in the security of Web applications.

OWASP also offer some use cases.

- Use as a metric - Provide application developers and application owners with a yardstick with which to assess the degree of trust that can be placed in their Web applications,

- Use as guidance - Provide guidance to security control developers as to what to build into security controls in order to satisfy application security requirements, and

- Use during procurement - Provide a basis for specifying application security verification requirements in contracts.

In a nutshell the OWASP ASVS is three separate checklists, level 1, 2 and 3, of what should be covered in an application security test. Each level, from 1 to 3, increases the complexity and amount of tests that should be carried out. Each level is targeted at specific types of applications and the level of security they are likely to need, or risk they are likely to accept.

I'm a big fan of checklists during testing as I believe they allow me to produce consistent, quality testing, for every engagement. If you need further information on why checklists are great I would recommend [David Rook's](https://twitter.com/davidrook) (ex-SecurityNinja) blog posts on the subject, [A checklist approach to security code reviews](https://www.securityninja.co.uk/application-security/a-checklist-approach-to-security-code-reviews/)

According to the [OWASP ASVS 3.0](https://www.owasp.org/images/6/67/OWASPApplicationSecurityVerificationStandard3.0.pdf) document, the verification levels are defined as:

- ASVS Level 1 (opportunistic) is meant for all software.

- ASVS Level 2 (standard) is for applications that contain sensitive data, which requires protection.

- ASVS Level 3 (advanced) is for the most critical applications - applications that perform high value transactions, contain sensitive medical data, or any application that requires the highest level of trust.

It is important to note that not all levels can be achieved with black box testing. Level 1 should be achievable through black box testing. Level 2 will require both black box and white box testing. Level 3 will require both black box and white box testing as well as other non penetration testing exsersises such as threat modelling and others. Level 3 is not achiveable purely through penetration testing.

From my experience, in the UK, most application tests are black box tests and as level 1 is meant for all software, I predict that the majority of the time ASVS Level 1 will be used in the UK. However, from my experience, in the US, a lot of application tests are black and white box tests. So in the US level 2 may be used more often than in the UK.

I think that companies are less likely to hand over source code in the UK for security audits for reasons unknown to me. Maybe to protect their Intellectual Property (IP), or maybe security companies are not proactively selling white box tests enough, who knows.

Lets take a look at two authentication requiremets as examples as to what level they fit in and if they require white or black box testing:

> 2.9. Verify that the changing password functionality includes the old password, the new password, and a password confirmation.

This requirement spans across all 3 levels and is achievable through black box testing.

Whereas the following requirement;

> 2.13. Verify that account passwords make use of a sufficient strength encryption routine and that it withstands brute force attack against the encryption routine.

This requirement spans across levels 2 and 3 and would usually require a white box test as it would be difficult to predict how the application encrypts its passwords from an outsider's perspective (unless they're not encrypting their passwords at all!).

##What's new in version 3.0?

Version 3.0 contains some new sections which include Configuration, Web Services and Client based (JavaScript) applications, mappings to Common Weakness and Enumeration (CWE) dictionary, a ton of new checks and lots of existing checks improved.

I should also note that the OWASP ASVS does not only apply to web applications, it also applys to mobile applications and has a small additional verification section which should be done additionally when conducting mobile security assessments.

##How can it be used?

If you have been purchasing or conducting penetration tests or vulnerability assessments for any significant amount time you will soon realise that not every test is equal.

Some companies obviously will do a better or worse job at delivering on their promises.

Testers are not always equal either, some are more experienced than others and all have their individual strengths and weaknesses. One tester may a whizz at client side attacks such as Cross-Site Scripting (XSS), where another may be a whizz in server side attacks such as SQL Injection. The tester who is more confident with XSS may do some XSS based check which the other doesn't and vice versa.

For that reason I think the ASVS is a great tool for both the security service buyer and seller to agree on what an application test will entail.

It can give some level of confidence about what it is you're buying and what is being sold.

Of course every company has their own testing methodologies which are based on industry standards such as the [Penetration Testing Execution Standard (PTES)](http://www.pentest-standard.org/index.php/Main_Page) and others.

The OWASP ASVS is application specific and defines a granular checklist of what tests are expected to be done.

##How can I contribute?

Nothing is ever perfect or 'finished' so you may notice a spelling mistake which was missed during the review process, or have some ideas of some other tests which should be included in the next OWASP ASVS version.

If you are able to help translate the OWASP ASVS into other languages besides English, I'm sure that would be very much appreciated too.

The best place to start is the [OWASP ASVS Mailing List](https://lists.owasp.org/mailman/listinfo/owasp-application-security-verification-standard).
