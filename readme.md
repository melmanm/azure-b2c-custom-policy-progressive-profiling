# Azure B2C progressive profilinig sample

## Files

`TrustFrameworkBase.xml`, `TrustFrameworkExtensions.xml` and `TrustFrameworkLocalization.xml` originates from Azure cusom policy samples repository.
https://github.com/Azure-Samples/active-directory-b2c-custom-policy-starterpack. They are foundation for progressive profilinig policy.
Following TrustFrameworkPolicies implement progressive profiling features
1. `ProgressiveProfile_TrustFrameworkBase`  defines base claims and technical profile to handle progressive profiling and exchange claims with AAD and handle user input.
2. `ProgressiveProfile_TrustFrameworkExtensions` defines claims impementation specific claims which will gathered from user in progressive profiling flow. Implements UserJourney.
3. `progressive_signup_signin` defines `RelyingParty` which specifies final token claims.

## How to start
1. Replace `yourtenant.onmicrosoft.com` with target tenant name in all files.
2. In `ProgressiveProfileTrustFrameworkBase.xml` replace `fill-in-b2c-extensions-app-ClientId` and `fill-in-b2c-extensions-app-ApplicationObjectId` with ApplicationObjectId and ClientId of b2c-extensions-app (which is created by default in B2C tenant)
3. Add following user custom properties:
    * extension_PPCounter
    * extension_FavoriteIde
    * extension_FavoriteProgrammingLanguage
