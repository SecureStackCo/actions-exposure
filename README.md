# SecureStack GitHub Actions

A GitHub Action that analyses your web application for security and availability issues.
When you add this to GitHub Actions we will analyze your web app everytime you deploy to a 
public endpoint and let you know if what you've just deployed is secure and meets your 
requirements.

```
name: Example Workflow Using SecureStack Web Vulnerability Exposure Action
on: push
jobs:
  security:
    runs-on: ubuntu-latest
    steps:
      - name: Web Vulnerability Exposure Analysis Step
        id: exposure
        uses: SecureStackCo/actions-exposure@v0.1.2
        with:
          securestack_api_key: ${{ secrets.SECURESTACK_API_KEY_SECRET }}
          securestack_app_id: <Application Id>
          severity: critical
          flags: '--dom -r'
```

NOTE - to understand possible values for the action input `flags`, run the SecureStack cli locally:

`$ bloodhound-cli recon --help`

## Getting your SecureStack API Key

1. Log in to [SecureStack](https://app.securestack.com) and go to the Profile -> GENERATE KEY screen.
2. Generate an API key and copy the value.
3. Paste into the value of a secret called SECURESTACK_API_KEY_SECRET in the GitHub repo settings.

## Getting your SecureStack Application ID

1. Log in to [SecureStack](https://app.securestack.com).
2. Open the application you wish to analyse.
3. Copy the value of the application id on the View Application screen.
4. Paste into the value of the `securestack_app_id` action input for the step using the SecureStack action in your workflow.


Made with 💜 by [SecureStack](https://securestack.com)
