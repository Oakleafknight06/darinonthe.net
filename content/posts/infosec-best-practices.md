---
date: '2025-06-05T00:00:00Z'
draft: true
layout: 'post'
title: General Information Security Best Practices
---

# Information Security Best Practices Compilation
Updated 06 June 2025


This document is aimed towards regular computer users, especially those who want security but don't know much about it. It's essentially a written version of what the resident tech person (i.e. yours truly) would tell the people in their life who consult them on (almost) any tech thing. It is not intended to be for companies, people with high security needs, or people who already know what they're talking about.

## Recommendations

1. **Use 2FA (Two-Factor Authentication):**
Time-based One Time Password (TOTP, the one with 6 numbers that rotate on a timer) is the most common standard. If something says it supports Google Authenticator or Authy this is what it supports. Only use SMS for two factor when there is no other option. 
[Authy](https://www.authy.com) or [Microsoft Authenticator](https://support.microsoft.com/en-us/account-billing/download-microsoft-authenticator-351498fc-850a-45da-b7b6-27e523b8702a) are proprietary solutions with good cloud sync/backup, but without an export function should you need it. [Raivo](https://raivo-otp.com/) for iOS and [Aegis](https://getaegis.app/) for Android are both open-source applications with good data portability, but you will have to manage the backups yourself (which is very important, as you will lose access to your accounts if you don't have these or the recovery codes.) 
> Many password managers also support storing this in their password vault, which makes using and deciding to use this easier, but makes a small compromise in security in that were someone to obtain access to your password vault, they would have *everything*. (Add article about the pros and cons)

2. **Use a (secure) password manager:**
    Avoid password reuse and use strong passwords. Password reuse is perhaps the #1 cause of hacked accounts. If you reuse passwords, all your accounts are as vulnerable as whichever website stores your password with the least security. Use a strong password which you memorize for your password manager especially—you won't need to remember any of the others, so make this one count.
    *But why not just write them down in a book? Isn't it more secure to not be on a computer?* 
    Because books do not have easy tools to generate random passwords, nor are they as easy to use with all your computer things as something on a computer. Inconvenience and laziness which accompanies it are the enemies of good security. If you truly want to, you could write all your passwords down in a book, use diceware to randomly generate passwords, and type them all manually every time you use them. 
    ### Recommended Applications/Services
    - [Bitwarden](https://bitwarden.com)
    Free and Open-Source software, regular audits and is very well respected. Current top recommendation. Free with paid options.
    - [1Password](https://1password.com) 
    Not FOSS, but has regular audits and works closely with password cracking community. Starts at $4 a month, with a free trial but no free tier.
    - [Proton Pass](https://proton.me/pass)
    FOSS, and from the people behind Proton Mail. Very new, but independently audited. Free with paid options.
    - KeePass 
        FOSS, longstanding good reputation, data control. KeePass is more of a format than a particular app or service. There are multiple clients which can all open the encrypted password database file, which you create and manage yourself. For some this is a great feature, for others it's simply an opportunity to lose all their passwords more easily. Most people will be better off with Bitwarden. Here are the recommended clients:
        1. [KeePass](https://keepass.info) The original, Windows only. Use version 2. (Free)
        2. [KeePass XC](https://keepassxc.org/) Windows/macOS/Linux. Independently audited in 2023. (Free)
	    3. [KeePass DX](https://www.keepassdx.com/) Android (free)
	    4. [KeePassium](https://keepassium.com/) iOS, independently audited in 2024. (paid, but the free tier is plenty for most use cases)
    - Don't use LastPass — too many data security issues
        - While it used to be recommended, LastPass has proven itself unable to cope with the security issues it has faced recently.
        - [Tom's Guide on the repercussions of the breach](https://www.tomsguide.com/computing/password-managers/millions-stolen-from-lastpass-users-in-massive-hack-attack-what-you-need-to-know)
        - [Blog post](https://palant.info/2022/12/26/whats-in-a-pr-statement-lastpass-breach-explained/) 
        - [Mastodon post](https://infosec.exchange/@epixoip/109585049354200263)

    - Evaluate password managers based on their handling of sensitive data, transparency with regular third-party audits, cryptography, and competency in response to security incidents when they happen. (These guidelines are also helpful when evaluating VPNs).


4. **If you don’t need it, don’t install it.  If you’re not using it, uninstall it.  If you did not ask for it, don’t click on it.**

5. **Don't use browser extensions (Or at least heavily limit the ones you use):**
    When you install a browser extension, you give it access to almost everything in the browser. Most permissions are far more far-reaching than they appear. A malicious browser extension can do a lot (add blog post about this). Furthermore, their presence can limit built-in browser security by running untested code on web pages and connecting things that didn't need to be connected (more potential attack vectors).

6. **Run up-to-date software:**
Install operating system and application updates in a timely manner. Run the most up-to-date OS your hardware supports, and consider switching operating systems or upgrading your hardware when that is no longer possible. If an application (particularly anything which touches the internet) is no longer being maintained, consider using an alternative.

7. **VPNs:** VPNs are not a general-purpose security or privacy tool. They are for circumventing censorship, or other network restrictions. 
Most VPN marketing is lying to you. If you've seen a VPN ad in a YouTube video, you probably don't want to use that VPN. ([Video](https://youtu.be/WVDQEoe6ZWY) about VPN marketing details.) A VPN will not protect you from malicious websites or other danger on the internet.
VPNs *can* be useful tools, however. [Mullvad](https://mullvad.net/en/) is one of the best, in both privacy and security of their service and utility in evading censorship. Astrill VPN is second-best for censorship, particularly in China. Otherwise they operate like most other VPN companies. [ProtonVPN](https://protonvpn.com) is a good option if all you need is protection from public airport WiFi, but it can't evade state level censorship. 

8. **Google Voice:** 
Yes, they’ll harvest your data, but you might trust them more than your cell provider and you can prevent someone else from getting your cell number by bribing an underpaid cell service employee. Chances are your Google account is better secured than your cell provider account, which is especially useful for things like Signal. One caveat is many services which require SMS verification or SMS for 2FA don't allow the use of [VoIP](https://en.wikipedia.org/wiki/Voice_over_IP) numbers, so the utility in that area is limited.

9. **Secure open-source text/voice messaging:**
Use [Signal](https://signal.org) or [Session](https://getsession.org)
Signal is preferred, and widely regarded as the most secure option out there. Session was derived from Signal, with the main difference being Session does not require a phone number (or any verification) to set up an account.
But why not just use text messaging? SMS is one of the least secure forms of online communication available. Thus it should not be trusted with anything sensitive. In many cases, not using two-factor authentication at all would be more secure. Refer to this [podcast episode](https://malicious.life/episode/episode-204/) for some more information on sim swap attacks. For communication purposes, it is fine to use but is unencrypted and any information sent through it should be treated as publicly available.

10. **Any recovery method is an attack vector:**
An attacker need only break the weakest link in the chain. This is particularly relevant in the case of a password hint or security questions. There is no good reason to use a password hint, you should be using a password manager instead. Security questions based on real facts about you are very insecure, because much of that information is freely available or not hard to find. If you are required to use security questions, treat them as another password field and store the secrets in your password manager.
     Secondly, if an account can be recovered via email or SMS without knowing the password and/or having access to a 2FA device, the security of the account is only the security of the email or SMS.
     When setting up 2FA you will get recovery codes of some sort. Store these safely, as again they are a recovery method by which an attacker could gain access to your account. (They are also how you gain access if you forget your login details or lose your second factor device, so be sure you can get them if you need them.)

11. **Use [Full volume encryption](https://ssd.eff.org/glossary/full-disk-encryption) on your devices:**
In macOS you can use FileVault (built in), on Windows Bitlocker (also built in, but only on Windows 10/11 Pro), on Linux LUKS (must be done at install time.) Encryption is enabled by default in iOS. For Android, as of Android 7, the emphasis is File Based Encryption (which is enabled by default in reputable devices). As of Android 10 it is required for all devices running Android.

12. **Use secure DNS on your routers and devices:**
Cloudflare's 1.1.1.1 is good, as is [Control D](https://controld.com). Use [DNS-over-HTTPS](https://www.cloudflare.com/learning/dns/dns-over-tls/) where available.

13. **Use a secure email address from a provider for whom you are not the product:**
[ProtonMail](https://mail.proton.me), [Tutanota](https://mail.tutanota.com), and [Fastmail](https://www.fastmail.com) are all good options.

14. **Monitor your accounts to see when (not if) they get compromised:**

	- [HaveIBeenPwned](https://haveibeenpwned.com/)  

	- A Firefox account & [Firefox Monitor](https://monitor.firefox.com/) makes this easier.

## Explainers and how-tos for the above
- **2FA/MFA: What they are and how to use them**

    - [EFF article](https://ssd.eff.org/module/how-enable-two-factor-authentication)

    - [Tom Scott video](https://www.youtube.com/watch?v=hGRii5f_uSc)

    - [How to: Enable Two-factor Authentication](https://ssd.eff.org/module/how-enable-two-factor-authentication)

- **Passphrase**

    - [https://www.useapassphrase.com](https://www.useapassphrase.com)

    - [xkcd 936](https://xkcd.com/936/)

    - [Don't pass on the new NIST password guidelines](https://auth0.com/blog/dont-pass-on-the-new-nist-password-guidelines/)

    - [Diceware](https://theworld.com/~reinhold/diceware.html)

    - [EFF Dice-Generated Passphrase](https://www.eff.org/dice)

- **Password Managers**
    - [EFF](https://ssd.eff.org/module/animated-overview-using-password-managers-stay-safe-online)

    - [https://lock.cmpxchg8b.com/passmgrs.html](https://lock.cmpxchg8b.com/passmgrs.html)

## Miscellaneous useful resources

- [How to encrypt your life in less than an hour](https://www.freecodecamp.org/news/tor-signal-and-beyond-a-law-abiding-citizens-guide-to-privacy-1a593f2104c3/)

- From ProtonMail

	- [For individuals](https://proton.me/support/new-account-owner-security-checklist?utm_campaign=ww-en-2c-generic-coms_email-monthly_newsletter&utm_source=proton_users&utm_medium=link&utm_content=2021_-_feb)

	- [For businesses](https://proton.me/business/security-guide?utm_campaign=ww-en-2c-generic-coms_email-monthly_newsletter&utm_source=proton_users&utm_medium=link&utm_content=2021_-_feb)

- Why weak encryption or giving governments a backdoor to WhatsApp (Or Signal or any other secure communication) is a *very* bad idea: [Why The Government Shouldn't Break WhatsApp](https://www.youtube.com/watch?v=CINVwWHlzTY)

- [Even if you're paying for the product, you're still the product](https://pluralistic.net/2022/11/14/luxury-surveillance/#liar-liar)

- ["I had ice cream today"](https://twitter.com/SwiftOnSecurity/status/1584119842562457600) - Why somebody will get mad about anything you say online

- [Tom Scott - Why Electronic Voting Is Still A Bad Idea](https://www.youtube.com/watch?v=LkH2r-sNjQs)
