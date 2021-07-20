# Hybrid Flow Sample and Test

**Version:** 1.1.16

[![Build Status](https://dev.azure.com/osieng/engineering/_apis/build/status/product-readiness/OCS/osisoft.sample-ocs-authentication_hybrid-dotnet?repoName=osisoft%2Fsample-ocs-authentication_hybrid-dotnet&branchName=main)](https://dev.azure.com/osieng/engineering/_build/latest?definitionId=3091&repoName=osisoft%2Fsample-ocs-authentication_hybrid-dotnet&branchName=main)

This client uses the OIDC Hybrid Flow to obtain an access token. See the main OCS Authentication samples page [README](https://github.com/osisoft/OSI-Samples-OCS/blob/main/docs/AUTHENTICATION_README.md) for more information about this flow.

## Requirements

- .NET 5.0 or later
  - Note: Visual Studio 16.8 or later is required for development against .NET 5.0
- Web Browser with Javascript enabled
  - You will need Google Chrome if you want to run the automated test

1. The sample is configured using the file [appsettings.placeholder.json](HybridFlow/appsettings.placeholder.json). Before editing, rename this file to `appsettings.json`. This repository's `.gitignore` rules should prevent the file from ever being checked in to any fork or branch, to ensure credentials are not compromised.
1. Replace the placeholders in the `appsettings.json` file with your Tenant Id, Client Id and Client Secret
1. Ensure that this client was created to allow Refresh Tokens
   - If this client does not allow refresh tokens, no refresh token will be issued upon authentication
1. Ensure that the client contains \$"{RedirectHost}:{RedirectPort}/{RedirectPath}" in the list of RedirectUris
   - Default value from config is: `https://127.0.0.1:54567/signin-oidc`
   - You can change the values to match your preferences

## Running the sample

### Prerequisites

- Register a Hybrid client in OCS and ensure that the registered client in OCS contains `https://127.0.0.1:54567/signin-oidc` in the list of RedirectUris.

- Replace the placeholders in the `appsettings.json` file with your Tenant Id, Client Id, and Client Secret obtained from registration.

### Using Visual Studio

1. Load the .csproj in this directory
2. Rebuild project
3. Run it
   - If you want to see the token and other outputs from the program, put a breakpoint at the end of the main method and run in debug mode
4. Follow the prompts in the web browser to log in
   - Keep in mind that if you are already logged in with the same Account in the browser, you will not have to log in again
5. Return to the application after having been authenticated in the browser

### Using Command Line

- Make sure you have the install location of dotnet added to your path
- Run the following command from the location of this project:

```shell
dotnet run
```

- Follow the prompts in the web browser to log in
- Return to the application after having been authenticated in the browser

## Running the automated test

### Test Prerequisites

- Make sure Google Chrome is the default browser on your test system.
- Download the ChromeDriver version from `http://chromedriver.storage.googleapis.com/index.html` corresponding to the version of Google Chrome that is installed. Set the environmental variable ChromeWebDriver to the directory containing the Chrome Driver executable.
- Update the `appsettings.json` with the username and password for the Microsoft account that will be used to log in. The test is only written to work with a personal Microsoft account and must only prompt for only username followed by password (no Two-Factor authentication or other consent or informational prompts). Also if the location of the sample application has been modified then change the RedirectHost and/or RedirectPort.

### Test Using Visual Studio

- Load the .csproj from the HybridFlowTest directory above this in Visual Studio
- Rebuild project
- Open Test Explorer and make sure there is one test called Test1 showing
- Run the test

### Test Using Command Line

- Make sure you have the install location of dotnet added to your path
- Run the following command from the location of the HybridFlowTest project (you may need to run as Administrator for the test to use the Chrome Driver):

```shell
dotnet test
```

---

Tested against DotNet 5.0

For the main OCS Authentication samples page [ReadMe](https://github.com/osisoft/OSI-Samples-OCS/blob/main/docs/AUTHENTICATION_README.md)  
For the main OCS samples page [ReadMe](https://github.com/osisoft/OSI-Samples-OCS)  
For the main OSIsoft samples page [ReadMe](https://github.com/osisoft/OSI-Samples)
