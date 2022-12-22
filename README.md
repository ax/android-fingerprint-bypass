# android-fingerprint-bypass

Updated Android biometric bypass script (from Kamil Breński, Krzysztof Pranczk and Mateusz Fruba, August 2019).

This script will bypass authentication when the crypto object is not used. The authentication implementation relies on the callback onAuthenticationSucceded being called.

:new: The code resolves `BiometricPrompt$AuthenticationResult` constructor args at runtime. :new: 

It should work with any Android version.

## Usage

```
$ frida --codeshare ax/universal-android-biometric-bypass -f YOUR_BINARY
```

## References 

https://labs.withsecure.com/publications/how-secure-is-your-android-keystore-authentication
