---
date: '2025-07-04T00:00:00Z'
title: What is a "Strong" Password?
draft: false
layout: 'post'
---

## Intro
You hear all the time that you should be using "Strong Passwords", but what does that mean, exactly? Do I need a complex password, a long one, both? How do password strength meters work? In this article I hope to shed some light on these topics.

For this article, we will define a strong password as follows:

*A strong password is one that is difficult for an adversary to guess, whether by brute force, educated speculation, or specific intelligence.*

Lets break that down.

## Difficult for an adversary to guess
This means you and only you should control who has this password. There should not be a way for someone other than you to have the password without you giving it to them, or them stealing it from you. (Securing password storage is an important topic, but outside the scope of this article.)
The adversary or attacker is some other party who is attempting to use your password without your consent. These terms are preferable to "hacker" because they are more generic and less loaded.

## Brute force
In simple terms, this means the attacker guesses every possible permutation of a password until they find yours. With modern computing power, anything 8 characters or less is relatively trivial to break with this method (Presuming the attacker does not have a limited number of attempts.)

## Educated Speculation
In essence this part means that if the attacker is able to guess how you made the password, that should not give them enough of an advantage to be able to break the password. In other words, the security of the password should not depend on obscuring its method of creation.
Security through obscurity is only as secure as it is obscure, and will only remain obscure for a finite period. It is far more reliable to have a password that is mathematically secure even when the adversary knows exactly how you made it.

## Specific Intelligence
The essence of this criterion is there should not be a piece of information available to an attacker targeting you which would reveal the password or make it significantly easier to guess. 
Do not use any personally identifiable info in your password, such as birthdays, pets names, or anything else of the sort in your passwords. Anyone could easily find this information on Facebook, Instagram, and other social media sites where you have revealed this, or from public records and various data broker sites where you don't even have control over what gets shared. As a sidenote, this is why security questions to recover accounts are generally considered to be highly insecure. If you are forced to use them, give gibberish answers and write those down in a safe place rather than using the truth. The answers to those questions can usually be found for free, without much effort, if someone decides to look.

Secondly, and more importantly, don't use duplicate passwords. If you do, no matter how strong the password, as soon as one account with the password is hacked, all of your accounts with that password are in the same boat. Once one password is leaked or stolen, attackers will try that email and password combination on any site they want. If you reused the password, they now have easy access to multiple of your online accounts, not just one.

## Calculating password strength

Before we calculate password strength, a fundamental rule must be understood. When expressing the randomness of a password in terms of bits of entropy, this is really expressing the randomness of the *method* of password creation, rather than of the final password. In other words, the randomness of a password generation method is proportional to the number of possible passwords it could create.

It is for this reason that passwords which one simply comes up with are to be avoided. While the password itself may be *strong* enough, whether it is or not isn't mathematically verifiable. Using a specific method of generation (or algorithm, you could say), whether by a computer program or with dice and alist of words, provides a much greater assurance of the security provided by the password.

Now, how do we calculate the entropy (randomness) of our password generation algorithm?
log_2(a^c) is the equation to calculate entropy, where `a` is a number representing the total alphabet of selectable characters and `c` is the number of characters selected.

So, if we have a 10-character password `(c=10)` selected from all lowercase English letters `(a=26)`, our equasion will be as follows:
```math
log_2(26^10) = 47
```
Our entropy value is 47 bits

This is not a secure password. As of 2025, roughly 90 bits is considered pretty secure. To up the entropy of our password, we can add length (more from our alphabet or character set) or complexity (add more characters to our character set). For example:

A 10-character password with uppercase and lowercase letters, numbers, and this set of special characters: `!@#$%^&*()?;` 
```math
log_2(74^10) = 62.095
```

Better, but what happens if we change the length instead?

```math
log_2(26^20) = 94
```

That's significantly better! As you can see from the example, upping the length has *far* more effect on the strength of the password than complexity does. We doubled the length while only using the lowercase alphabet, and ended up with a pretty good password. This is why, in the latest revision of NIST Special Publication 800-63B (A document by the US government standards body, outlining best practices for passwords and other digital identity guidelines), NIST recommends removing all password complexity requirements and focusing only on password length. Complexity requirements do not help much, as demonstrated, often make passwords more difficult to remember, and lead people to adapt their passwords to the requirements in very predicatble ways (further undermining any aid they gave against password cracking attacks). NIST requires at least 8 characters for every password, and recommends 12 characters. If security is your objective, make your passwords as long as you can reasonably use (though anything above 32 characters when randomly generated is somewhat uneccessary.)

But how do we remember passwords that are so long? This is where the idea of a *passphrase* comes in. Instead of a string of characters, a passphrase is a string of words, such as *correct horse battery staple*. Diceware is a particular method of generating passphrases, which uses a set of 7776 words, from which a number of words are selected to form a phrase. Other wordlist sizes also exist, but this is the most common.

To calculate the entropy of a passphrase, we can think of the wordlist as our alphabet. Instead of 26 characters to form a pass*word*, we choose from 7776 words to form a pass*phrase*. This brings two advantages: `correct horse battery staple eggnog berry` is a lot easier to remember than `pkihzwukndeykmdkmdtq` and is nearly as strong. If we need something better, we can increase the number of words or pick a larger wordlist.

## What about my phone/bank/etc PIN?
In short, though these are cryptographically weak due to the limited alphabet and length, they are secure enough because there are other measures preventing many password attempts or securing the data through other factors.

## Conclusion
If you take nothing else away from this article, remember this: Use unique, randomly generated passwords for every account, and store them somewhere safe like a password manager. If you're choosing one to use, evaluate password managers based on their handling of sensitive data, transparency with regular third-party audits, cryptography, and competency in response to security incidents when they happen.

When choosing a password, generate it randomly, and remember length is more important than complexity.

And lastly, I hope you learned something interesting!

## Links

[useapassphrase.com](https://www.useapassphrase.com)

[xkcd 936 (comic illustrating passphrase advantages)](https://xkcd.com/936/)

[Don't pass on the new NIST password guidelines](https://auth0.com/blog/dont-pass-on-the-new-nist-password-guidelines/)

[NIST SP800-63B Passwords Section](https://pages.nist.gov/800-63-4/sp800-63b/passwords/)

[Article from 2012 on password strength checkers](https://dropbox.tech/security/zxcvbn-realistic-password-strength-estimation)

[Diceware](https://theworld.com/~reinhold/diceware.html)

[EFF Dice-Generated Passphrase](https://www.eff.org/dice)

[Don't use LastPass: Analysis of their awful response to multiple breaches](https://palant.info/2022/12/26/whats-in-a-pr-statement-lastpass-breach-explained/) 

[Post by security researcher on LastPass](https://infosec.exchange/@epixoip/109585049354200263).

[Electronic Frontier Foundation on Password Managers](https://ssd.eff.org/module/animated-overview-using-password-managers-stay-safe-online)

[Interesting article on the downsides of password manager browser extensions](https://lock.cmpxchg8b.com/passmgrs.html)
