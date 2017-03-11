---
title: "Book review: Rails Security Audit"
layout: post
tags:
- book
- rails
---
[Rails Security Audit](http://peepcode.com/products/rails-security-audit-pdf) is an straight-talking introduction to the techniques for keeping your Rails app secure.  Over the course of 47 pages, [Aaron Bedra](http://aaronbedra.com) tackles the security audit process, common security-related bugs, essential server lockdown tactics, and an approach for assessing the severity of the issues you find.

Rails offers sound solutions for keeping your application safe from the likes of SQL injection, Cross-Site Scripting (XSS), Cross-Site Request Forgery (CSRF), and the perils of mass assignment, but are you sure you're using those solutions?  Without a proper understanding of these exploits, it's unlikely that a developer would safely navigate past those issues entirely.  Aaron provides easy-to-follow examples of each exploit, shows the consequences of ignoring them, and introduces the tools and techniques for identifying and avoiding those problems.

Going beyond Rails-specific security, Aaron covers a handful of guidelines for ensuring good server hygiene.  As a developer (read: *not* a system administrator), I personally couldn't tell you which ports should be open on a server and which ones are an invitation for trouble.  Aaron remedies that situation by demonstrating the tools for determining how well your server is currently secured and providing scripts and instructions for getting you to where you need to be.

The book closes out the discussion on server security with additional recommendations for restricting access to your servers, but it stops short of providing any direction for doing so.  While a quick round of Googling would likely locate a decent tutorial, I'd rather have seen the information included in the book (even if it just took the form of pointers to recommended tutorials).

Once you've identified the security issues in your app, Aaron offers honest, no-nonsense advice regarding the next step:  "I guarantee at some point you will audit an application and find something in the form of a security hole.  Your job as an auditor is to present the vulnerability, period."  Translation: security audits aren't about sugar-coating your findings or pulling punches.  He then pragmatically explains that anything other than the quick fixes will likely warrant further exploration of the actual risk posed by the issue, and provides a step-by-step walkthrough of a sample risk analysis effort.

If you're even the least bit uncertain about any of the topics discussed above, you owe it to yourself to check out Aaron's highly-approachable guide to assessing the state of security in your Rails app.

**Full disclosure**: Aaron and I work together at Relevance, and his potential for hacking into my laptop inspires great fear in me.  Nevertheless, I stand by the comments above even in the face of that adversity.
