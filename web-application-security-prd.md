# Web Application Security Guide: Ready-to-Use Prompts for Developers

## Overview

This guide provides a comprehensive set of security prompts that developers can use with AI tools to implement best practices for web application security. The prompts are organized in priority order and can be copied directly for use with tools like Claude, GPT, or other AI assistants.

Each prompt is designed to help implement specific security features while maintaining application functionality. Use these prompts as a starting point and customize them for your specific technology stack and requirements.

## Common Variables Reference

Before using the prompts, identify the values for these common variables that appear throughout the guide. You can define these once and use them across all prompts:

| Variable | Description | Example Values |
|----------|-------------|----------------|
| [YOUR_FRAMEWORK] | The frontend framework or library you're using | React, Angular, Vue, Svelte |
| [YOUR_HOSTING_PLATFORM] | Where your application is deployed | Firebase Hosting, AWS, Vercel, Netlify |
| [LIST_TECHNOLOGIES] | Major technologies in your stack | React, Firebase, Tailwind CSS |
| [LIST_DOMAINS_IF_APPLICABLE] | External domains your app interacts with | google.com, stripe.com, amazonaws.com |
| [LIST_EXTERNAL_SOURCES] | External script/resource sources | cdnjs.cloudflare.com, unpkg.com |
| [TYPES_OF_SENSITIVE_DATA] | What sensitive data your app handles | user credentials, payment information, PII |
| [AUTHENTICATION/PREFERENCES/TRACKING] | How you use cookies | authentication, user preferences, analytics |
| [YOUR_AUTH_SYSTEM] | Authentication method used | Firebase Auth, Auth0, custom JWT |
| [SPECIFIC_AUTH_REQUIREMENTS] | Special auth needs | social login, MFA, passwordless |
| [TYPES_OF_FORMS] | Forms in your application | login, registration, payment, contact |
| [TYPES_OF_DATA] | Data collected by your forms | personal details, credit card info, feedback |
| [ALLOW/RESTRICT] | Cross-origin interaction needs | allow, restrict |
| [PREFERRED_MONITORING_TOOLS] | Tools for monitoring | Sentry, LogRocket, Firebase Crashlytics |
| [PREFERRED_CHANNELS] | Alert notification methods | email, Slack, PagerDuty |
| [YOUR_CICD_PLATFORM] | CI/CD system used | GitHub Actions, CircleCI, GitLab CI |
| [YOUR_HOSTING_ENVIRONMENT] | Production environment | Firebase, AWS, GCP, Azure |
| [YOUR_FRONTEND_STACK] | Frontend technologies | React/Next.js, Vue/Nuxt, etc. |
| [TYPE_OF_APPLICATION] | Application category | SaaS, e-commerce, blog, dashboard |
| [YOUR_TECHNOLOGY_STACK] | Complete tech stack | MERN, LAMP, JAMstack, etc. |
| [YOUR_PREFERRED_LANGUAGE] | Language for tooling | JavaScript, Python, Go, Rust |

Example setup for a typical React application on Firebase:
```
YOUR_FRAMEWORK: React
YOUR_HOSTING_PLATFORM: Firebase Hosting
LIST_TECHNOLOGIES: React, Firebase, Tailwind CSS
LIST_DOMAINS_IF_APPLICABLE: firebaseapp.com, googleapis.com, cloudflare.com
LIST_EXTERNAL_SOURCES: unpkg.com, cdnjs.cloudflare.com
TYPES_OF_SENSITIVE_DATA: user authentication data, profile information
YOUR_AUTH_SYSTEM: Firebase Authentication
YOUR_CICD_PLATFORM: GitHub Actions
YOUR_PREFERRED_LANGUAGE: JavaScript
```

## Security Implementation Prompts

### Prompt 1: Essential Security Headers

```
Implement essential security headers for my web application, including:
- Content-Security-Policy with safe directives (no unsafe-inline or unsafe-eval)
- Set default-src to 'none' with appropriate exceptions
- X-Frame-Options set to SAMEORIGIN or implemented via CSP frame-ancestors
- X-Content-Type-Options set to nosniff
- Referrer-Policy set to no-referrer, same-origin, strict-origin, or strict-origin-when-cross-origin
- Permissions-Policy to restrict browser features
- Cross-Origin-Resource-Policy (CORP) header implementation

My application uses [YOUR_FRAMEWORK] and is hosted on [YOUR_HOSTING_PLATFORM]. Provide specific configurations for these headers with explanations for each header's purpose and value.
```

### Prompt 2: Content Security Policy Optimization

```
Create a strict but functional Content Security Policy for my web application that:
- Sets default-src to 'none' with appropriate exceptions for required resources
- Avoids unsafe-inline and unsafe-eval directives
- Properly restricts script-src, object-src, and all other relevant directives
- Uses nonces or hashes where inline scripts are necessary
- Implements frame-ancestors instead of X-Frame-Options where supported
- Supports necessary third-party resources
- Works with [YOUR_FRAMEWORK]
- Includes reporting configuration for violations

My application uses [LIST_TECHNOLOGIES] and needs to include resources from [LIST_DOMAINS_IF_APPLICABLE].
```

### Prompt 3: HTTPS and Transport Security

```
Implement comprehensive HTTPS and transport security for my web application:
- Strict Transport Security (HSTS) with a minimum six-month duration (15768000)
- Consider HSTS preloading with includeSubDomains directive and one-year duration (31536000)
- Proper redirect configuration from HTTP to HTTPS
- Secure TLS configuration with modern protocols and ciphers
- Certificate management and renewal strategy
- Mixed content prevention

My application is deployed to [YOUR_HOSTING_PLATFORM] and needs to maintain secure connections at all times.
```

### Prompt 4: Subresource Integrity and External Resources

```
Implement Subresource Integrity (SRI) and secure handling of external resources:
- Add integrity attributes to all external scripts and stylesheets
- Process for generating and updating SRI hashes
- Fallback mechanisms for critical resources
- Cross-Origin Resource Sharing (CORS) configuration review
- Strategy for handling third-party resources securely
- Management of CDN-delivered resources

My application uses external scripts from [LIST_EXTERNAL_SOURCES] and needs to maintain security while using these resources.
```

### Prompt 5: API and Sensitive Data Protection

```
Implement best practices for protecting API keys and sensitive data in my front-end application:
- Secure authentication configuration
- Environment variable handling for development vs. production
- Proper CORS implementation
- Server-side proxy for sensitive API calls
- Secure handling of user data and tokens
- Prevention of API key exposure in client-side code

My application is built with [YOUR_STACK] and handles [TYPES_OF_SENSITIVE_DATA].
```

### Prompt 6: Cookie Security and Management

```
Implement secure cookie handling for my web application:
- Set appropriate cookie attributes (Secure, HttpOnly, SameSite)
- Cookie scope and expiration best practices
- Implementation of necessary cookie consent mechanisms
- Minimization of cookie usage where possible
- Secure handling of session cookies
- Protection against cookie-based attacks

My application uses cookies for [AUTHENTICATION/PREFERENCES/TRACKING] and needs to implement best practices for each type.
```

### Prompt 7: Authentication and Authorization Security

```
Implement secure authentication and authorization practices for my web application:
- Secure login flows and session management
- CSRF protection mechanisms
- Proper JWT handling (if applicable)
- Role-based access controls
- Account recovery and password reset security
- Protection against common auth vulnerabilities
- Rate limiting for authentication attempts

My application uses [YOUR_AUTH_SYSTEM] and needs to support [SPECIFIC_AUTH_REQUIREMENTS].
```

### Prompt 8: Form Security and Input Validation

```
Implement comprehensive form security and input validation for my web application:
- Client-side and server-side validation strategies
- Protection against XSS in form inputs
- CSRF protection for all forms
- Secure file upload handling (if applicable)
- Proper error handling that doesn't expose sensitive information
- Rate limiting for form submissions

My application includes [TYPES_OF_FORMS] that collect [TYPES_OF_DATA].
```

### Prompt 9: Cross-Origin Protection and Framing Controls

```
Implement comprehensive cross-origin and framing protections:
- X-Frame-Options configuration or CSP frame-ancestors
- Cross-Origin Resource Sharing (CORS) policy implementation
- Cross-Origin Resource Policy (CORP) header implementation
- Cross-Origin Opener Policy (COOP) consideration
- Cross-Origin Embedder Policy (COEP) consideration
- Protection against clickjacking and UI redressing attacks

My application needs to [ALLOW/RESTRICT] specific cross-origin interactions with [LIST_DOMAINS_IF_APPLICABLE].
```

### Prompt 10: Security Monitoring and Incident Response

```
Implement security monitoring and incident response capabilities:
- Error logging and monitoring configuration
- Security event detection and alerting
- CSP violation reporting
- User activity auditing for suspicious behavior
- Response plan for potential security incidents
- Regular security scanning integration

My application should use [PREFERRED_MONITORING_TOOLS] and alert through [PREFERRED_CHANNELS].
```

### Prompt 11: Deployment and CI/CD Security

```
Implement security best practices for my deployment and CI/CD pipeline:
- Secure workflows for continuous integration/deployment
- Proper secret management in CI/CD
- Pre-deployment security scanning
- Dependency vulnerability checking
- Production build optimization for security
- Secure environment variable handling

My application uses [YOUR_CICD_PLATFORM] and deploys to [YOUR_HOSTING_ENVIRONMENT].
```

### Prompt 12: Performance Optimization with Security

```
Optimize my web application's performance while maintaining security:
- Secure resource caching strategies
- CDN configuration with appropriate security headers
- Lazy loading implementation that maintains CSP compliance
- Script loading optimizations with SRI
- Image and asset security with performance considerations

My application should maintain a balance between security controls and performance while using [YOUR_FRONTEND_STACK].
```

### Prompt 13: Regular Security Audit Preparation

```
Create a comprehensive security audit process for my web application:
- Automated scanning tools configuration
- Manual security testing checklist
- Regular dependency vulnerability checking
- User permission and access control auditing
- API security testing
- Front-end code security review
- Headers and transport security verification

My security audit should cover all aspects of my [TYPE_OF_APPLICATION] built with [YOUR_TECHNOLOGY_STACK].
```

## Implementing Security Testing

### Prompt for Setting Up Security Testing

```
Help me set up automated security testing for my web application:
- Recommend appropriate security scanning tools
- Provide configuration for integration with [YOUR_CICD_PLATFORM]
- Create a testing schedule and strategy
- Define security acceptance criteria
- Implement reporting for security test results
- Create a remediation workflow for identified issues

My application is built with [YOUR_TECHNOLOGY_STACK] and I need a practical implementation that balances thoroughness with development velocity.
```

## Security Headers Verification

### Prompt for Security Headers Verification Tool

```
Create a simple tool to verify security headers on my web application:
- Check for presence and correct values of all security headers
- Validate Content Security Policy configuration
- Test HTTPS and HSTS implementation
- Check for proper implementation of SRI
- Verify cookie security attributes
- Generate a report with findings and recommendations

The tool should be implemented in [YOUR_PREFERRED_LANGUAGE] and be easy to run as part of my CI/CD process.
```

## Recommended Security Testing Tools

Use the following tools to test and verify your web application's security implementation:

### Comprehensive Security Scanners

| Tool | Type | Focus | URL |
|------|------|-------|-----|
| OWASP ZAP | Free, open-source | Automated vulnerability scanning | https://www.zaproxy.org/ |
| Burp Suite Community | Free, limited features | Manual penetration testing | https://portswigger.net/burp/communitydownload |
| Nmap | Free, open-source | Network vulnerability scanning | https://nmap.org/ |
| Nikto | Free, open-source | Web server scanning | https://cirt.net/Nikto2 |

### Security Headers Analysis

| Tool | Type | Focus | URL |
|------|------|-------|-----|
| Mozilla Observatory | Free web service | Security headers and configurations | https://observatory.mozilla.org/ |
| Security Headers | Free web service | HTTP response headers | https://securityheaders.com/ |
| Hardenize | Free web service | TLS, HTTPS, header analysis | https://www.hardenize.com/ |
| ImmuniWeb | Free, limited scans | Website security testing | https://www.immuniweb.com/websec/ |

### Content Security Policy Tools

| Tool | Type | Focus | URL |
|------|------|-------|-----|
| CSP Evaluator | Free web service | CSP analysis and validation | https://csp-evaluator.withgoogle.com/ |
| Report URI | Free/Paid | CSP reporting and monitoring | https://report-uri.com/ |
| CSP Builder | Free, open-source | CSP header generation | https://github.com/paragonie/csp-builder |

### Performance and Security

| Tool | Type | Focus | URL |
|------|------|-------|-----|
| Google PageSpeed Insights | Free web service | Performance and best practices | https://pagespeed.web.dev/ |
| GTmetrix | Free, limited features | Performance analysis | https://gtmetrix.com/ |
| WebPageTest | Free web service | Performance and security testing | https://www.webpagetest.org/ |

### API Security Testing

| Tool | Type | Focus | URL |
|------|------|-------|-----|
| OWASP API Security Project | Resources and guidance | API security best practices | https://owasp.org/www-project-api-security/ |
| API Fortress | Commercial | Automated API testing | https://apifortress.com/ |
| Postman | Free, limited features | API testing and security | https://www.postman.com/ |

### Specific Vulnerability Scanners

| Tool | Type | Focus | URL |
|------|------|-------|-----|
| Retire.js | Free, open-source | JavaScript library vulnerabilities | https://retirejs.github.io/retire.js/ |
| Snyk | Free, limited features | Dependency vulnerabilities | https://snyk.io/ |
| OWASP Dependency-Check | Free, open-source | Dependency vulnerabilities | https://owasp.org/www-project-dependency-check/ |
| Trufflehog | Free, open-source | Secret scanning | https://github.com/trufflesecurity/trufflehog |

### Compliance and Standards Testing

| Tool | Type | Focus | URL |
|------|------|-------|-----|
| OWASP ASVS | Framework | Application security verification | https://owasp.org/www-project-application-security-verification-standard/ |
| SSL Labs | Free web service | SSL/TLS configuration | https://www.ssllabs.com/ssltest/ |
| HSTS Preload | Free web service | HSTS preload list submission | https://hstspreload.org/ |

### Mobile Application Security

| Tool | Type | Focus | URL |
|------|------|-------|-----|
| MobSF | Free, open-source | Mobile app security testing | https://github.com/MobSF/Mobile-Security-Framework-MobSF |
| OWASP Mobile Security Testing Guide | Framework | Mobile security guidance | https://owasp.org/www-project-mobile-security-testing-guide/ |

Testing Best Practices:
1. Start with automated scanners for quick wins
2. Use multiple tools as each may find different issues
3. Perform regular scanning as part of your CI/CD pipeline
4. Combine automated testing with manual review
5. Test in both development and production environments (safely)
6. Prioritize fixing high-severity issues first

## Conclusion

These prompts provide a starting point for implementing comprehensive security measures in web applications. Remember to customize the placeholders (indicated by [SQUARE_BRACKETS]) with information specific to your application before using them.

Security is an ongoing process, not a one-time implementation. Regularly revisit these areas as your application evolves and new security best practices emerge.

For the most effective results, consider using these prompts with AI assistants that have knowledge of web security best practices and your specific technology stack.
