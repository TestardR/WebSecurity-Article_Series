This article was done using my notes from a speech made by Dominik Kundel at JSunconf 2018.

<sub>Kundel D. (2018). "Introduction to Web Security, JSUnconf 2018, https://www.youtube.com/watch?v=-vYak5hEGrY</sub>

## 1. Use HTTPOnly Cookies 

```
res.cookie('authToken', jwt, {
	httpOnly; true,
	signed: true,
	secure: true
});
```

### What to remember ?

If there is no reason for your cookie to be accessible in Javascript, make it HTTPOnly. Furthermore, make also sure that cookies are signed, so that nobody can temper with them. Finally, cookies have to be secured, meaning it would only be transfered via a secure connection. 


## 2. Don't treat JWT as the single source of truth

```
const jwt = require('jsonwebtoken');

jwt.verify(token, secret, { algorithms: ['HS256']}, (err, payload) => {
	if(err) {
	console.log('Invalid token!');
	return;
	}

	console.log('Valid token!')
});
```
### What to remember ?
Stay up to date and go for safe JWT implementations. Good implementations should offer to whitelist algorithms, meaning it has to specify the only algorithms that are supported. Furthermore, if you try to verify a JWT without signature and with a secret, it should simply fail. Be consistent.

## 3. Protect yourself from target blank links

```
window.opener.location = 'http://my-evil-website.com';
```
The problem with blank links is that the new page has access to the previous page using window.opener. It allows for redirection to any page from a website. An attacker would use them to redirect users to fishing pages, looking alike your previous page. 

### Noopener and Noreferrer on the rescue 

Fortunately, we have two properties to protect ourselves from this.
Use 'noopener', it forbids the access to window.opener. Use 'noreferrer' for browsers that do not support noopener, so that they will not access referrer links. 

```
<!-- Target page has acess to window.opener -->
<a href="http://example.com/" target="_blank">Dangerous Link</a>

<!-- Target page does NOT have access to window.opener -->
<a href="http://example.com" target="_blank" rel="noopener noreferrer">Safe Link</a>
```

## 4. Use CSRF tokens 

To protect yourself from CSRF attacks, it is fairly straightforward. You have to produce a CSRF token, a unique token that we would set as a cookie and also set it on the page as a hidden input field. When we do POST requests, instead of just submitting the cookie, we would also manually send this value as a header or even as a request body or parameter. 

```
const csrf = require('csurf')({cookie: true});

app.get('/post', csrf, (req, res, next) => {
	// pass csrf to front-end via _csrf cookie or
	// req.csrfToken() in template
})

app.post('/post', csrf, (req, res, next) +> {
	// only valid if one of these is the same as the cookie:
	// req.body._csrf
	// req.query._csrf
	// req.headers['csrf-token']
	// req.headers['xsrf-token']
	// req.headers['x-csrf-token']
	// req.headers['x-xsrf-token']
});
```

### What to remember ?

CSRF tokens work. Even though attackers can access the cookie with a CSRF token inside it, it can only be read in the user specific domain. 

## 5. Blocking XSS attacks is not trivial

Let's take a basic example on how to do an XSS attack. In this case, we could write the following line of codes:

```
<script>alert('hello')</script>

[Click Me](javascript:alert('Hello')) --> this is how you create a link in markdown

[Click Me](javascript&#58;alert('Hello'&#41;) --> same : => &#58; and ) => &#47;

[Click Me](javascript&#58this;alert('Hello'&#41;) --> same and might often work. 

Why ? We inserted a 'this' before the semi-colon ';', the browser decides to help and 
finish the sentence &#58... "ah... and here goes your semi-colon ';'.". We inserted 'this' as 
it is a valid javascript value. 
```

### What to remember ?

As a reminder, never trust user inputs. Be as skeptical as you can. I would add to not use blacklist to avoid specific javascript formulas as eval() or scripts. Javascript can be written in many differents languages, such as Hebrew. Blacklists can be easily circumvent. Go for whitelists instead.

## 6. Other things to look out for 

1. Avoid clickjacking by disallowing framing using X-FrameOptions: deny,
2. Check out libraries like helmet for essential HTTP headers,
3. Don't show versions of front-end libraries or server,
4. Check for types of input, which can cause injections, such as NoSQL. 

## 7. Other things to do while you are at it...

1. Consider Security Audits, 
2. Stay up to date with versions (Greenkeeper),
3. Use tools to detect secucrity vulnerabilites (NSP, Snyk).