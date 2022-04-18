# 4.3: Security

App security is an important aspect of anything that is on the internet. Depending on the type of application security could be a crucial aspect of the operation of an app.

## How secure is it?

There is no such thing as a perfectly secure web application. The most secure software application that can be made would be installed on an [air gapped computer](https://en.wikipedia.org/wiki/Air_gap_%28networking%29) in a hermetically sealed room. It would be difficult to even give input or get any output from this theoretical computer since every possible mode of interaction could introduce security vulnerabilities. \(A computer can be vulnerable if someone can simply [listen to a user typing on the computer](https://en.wikipedia.org/wiki/Acoustic_cryptanalysis)\).

Many security vulnerabilities will simply result from human behavior and for which there is no technical solution, e.g., users [writing their passwords](https://arstechnica.com/information-technology/2015/04/hacked-french-network-exposed-its-own-passwords-during-tv-interview/) on [post-its.](https://www.vice.com/en/article/qvwmx5/the-agency-that-messed-up-hawaiis-nuclear-alert-keeps-passwords-on-post-its-vgtrn)

## Making an App Secure

The process of making an application secure involves applying industry best-practices, some of which we have already covered, such as hashing passwords. These best practices would also include organizational processes, such as limiting employees' access to sensitive company data. We won't be able to cover every single best practice here, as it also depends on which features are included into an app.

There are many resources on the web for application security:

- [OWASP](https://owasp.org/www-project-top-ten/)
- [Ruby on Rails Security](https://guides.rubyonrails.org/security.html)
- [MDN](https://developer.mozilla.org/en-US/docs/Web/Security)

## Don't Trust User Input

The essential principle for security of web apps is: _**Don't Trust User Input**_. If this principle is followed when constructing any feature of the app then the attack surface will be reduced significantly. We'll define user input broadly as anything that the app receives in a request.

In the following examples we'll see some ways in which the user input was not treated as dangerous, which can lead to some wide-ranging consequences.

In general we'll also see that in order to exploit any security vulnerability the attacker must have comprehensive knowledge of how a web application system works, from HTTP to JavaScript, etc. That also means that in order to assure the security of an application, that person must also have a deep understanding of all levels of the application.

## Sample App

For all the examples we'll be using this deployed express app: [https://express-security-bootcamp.herokuapp.com/](https://express-security-bootcamp.herokuapp.com/)

The code for this app is here: [https://github.com/rocketacademy/express-security-bootcamp](https://github.com/rocketacademy/express-security-bootcamp)
