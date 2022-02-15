# SecureStack Web Vulnerability Analysis GitHub Action

A GitHub Action that analyses your web application for security and availability issues.
When you add this to GitHub Actions we will analyze your web app everytime you deploy to a 
public endpoint and let you know if what you've just deployed is secure and meets your 
requirements.  See below for what types of issues this action scans for.

```
name: Example Workflow Using SecureStack Web Vulnerability Exposure Action
on: push
jobs:
  security:
    runs-on: ubuntu-latest
    steps:
      - name: Web Vulnerability Exposure Analysis Step
        id: exposure
        uses: SecureStackCo/actions-exposure@v0.1.3
        with:
          securestack_api_key: ${{ secrets.SECURESTACK_API_KEY }}
          securestack_app_id: ${{ secrets.SECURESTACK_APP_ID }}
          severity: critical
          flags: '--dom -r'
```

NOTE - to understand possible values for the action input `flags`, run the SecureStack cli locally:

`$ bloodhound-cli recon --help`

## Create your SecureStack API Key as GitHub Secret

1. Create a [SecureStack](https://app.securestack.com) account using your GitHub credentials.  You get 20 scans for free and you don't need to add a credit card.
2. Once you are logged in go to "Profile" in the black drawer on the left, and then -> GENERATE KEY tab.
3. Generate an API key and copy the value.
4. Go to Settings for your GitHub repository and click on Secrets -> Actions at the bottom left.
5. Create a new secret named SECURESTACK_API_KEY and paste the value from step 2 into the field.

## Retreiving your SecureStack Application ID

1. Log in to [SecureStack](https://app.securestack.com).
2. Open the application you wish to analyse.  If you haven't created a managed application you can follow the directions in this [VIDEO](https://youtu.be/mapgawLMVKg) to create one.  
3. Copy the value of the application id on the View Application screen.
4. Go to Settings for your GitHub repository and click on Secrets -> Actions at the bottom left.
5. Create a new secret named SECURESTACK_APP_ID and paste the value from step 3 into the field.

## Watch this video to learn how to setup your first GitHub Action with SecureStack
[![IMAGE ALT TEXT](http://img.youtube.com/vi/0sYXsCmY2es/0.jpg)](http://www.youtube.com/watch?v=0sYXsCmY2es "Video Title")

## What vulnerabilities do we find?
1. Scans web application for out of date and vulnerable application components
2. Identifies whether basic security controls like WAF, firewalls, and security headers are being used
3. Finds all public facing assets & helps you understand your application attack surface
4. Identifies misconfigurations in existing WAF or CDN
5. Identifies if app is using CSP or security headers and whether they're working
6. Finds WAF bypass attacks for Akamai, Cloudflare & Imperva

## Check out our other GitHub Actions:
1. [SecureStack Secrets Analysis](https://github.com/marketplace/actions/securestack-secrets-analysis) - Scan your application for embedded api keys, credentials and senstive data.
2. [SecureStack Software Composition Analysis (SCA)](https://github.com/marketplace/actions/securestack-application-composition-analysis) - Scan your application for vulnerable third-party and open source libraries.
3. [SecureStack Log4j Analysis](https://github.com/marketplace/actions/securestack-log4j-vulnerability-analysis) - Scan your application for Log4j/Log4Shell vulnerabilities.

## Learn more about SecureStack with our YouTube Channel:
https://www.youtube.com/watch?v=YrPITQNy9UM&list=PL_8Xjyi5rInxzhpQkDRipipmaj0lT6pJ8 

Made with 💜  by [SecureStack](https://securestack.com)
