# Azure B2C progressive profilinig sample

## Files

`TrustFrameworkBase.xml`, `TrustFrameworkExtensions.xml` and `TrustFrameworkLocalization.xml` originates from Azure cusom policy samples repository.
https://github.com/Azure-Samples/active-directory-b2c-custom-policy-starterpack. They are foundation for progressive profilinig policy.
Following TrustFrameworkPolicies implement progressive profiling features
1. `ProgressiveProfile_TrustFrameworkBase`  defines base claims and technical profile to handle progressive profiling and exchange claims with AAD and handle user input.
2. `ProgressiveProfile_TrustFrameworkExtensions` defines claims impementation specific claims which will gathered from user in progressive profiling flow. Implements UserJourney.
3. `B2C_1A_ProgressiveProfile_SignUpOrSignIn` defines `RelyingParty` which specifies final token claims.

## How to start
1. Create Azure B2C tenant
2. Create Application Registration
    * Select Supported account types: Accounts in any identity provider or organizational directory
    * Specify RedirectURI (https://jwt.ms/ to see output token in the browser)
3. After Apllication is registered navigate to API permissiong in application properties and Grant admin consent for Microsoft Graph permission.

4. Replace `yourtenant.onmicrosoft.com` with target tenant name in all xml policy files.
5. In `ProgressiveProfileTrustFrameworkBase.xml` replace `fill-in-b2c-extensions-app-ClientId` and `fill-in-b2c-extensions-app-ApplicationObjectId` with ApplicationObjectId and ClientId of b2c-extensions-app (which is created by default in B2C tenant)
6. Add following user custom properties:
    * extension_PPCounter
    * extension_PreferedTraining
    * extension_PreferedExcercises
7. Upload xml policies file using Identity Experience Framework blade in Azure B2C tenant
8. Click on `B2C_1A_ProgressiveProfile_SignUpOrSignIn`
9. Rigt menu should show up. Under Select Applcication select created Applicaiton Registration
10. Click Run Now
11. Sign up or Create user in Azure B2C tenant Users blade
12. Try to sing-in 3 times. Progressive profiling form will be displayed.