# android-fingerprint-bypass

Updated Android biometric bypass script (from Kamil Breński, Krzysztof Pranczk and Mateusz Fruba, August 2019).

This script will bypass authentication when the crypto object is not used. The authentication implementation relies on the callback onAuthenticationSucceded being called.

:new: The code resolves `BiometricPrompt$AuthenticationResult` constructor args at runtime. :new: 

It should work with any Android version.

## Usage

```
frida --codeshare ax/universal-android-biometric-bypass -f YOUR_BINARY
```
```
frida -U -f YOUR_BINARY --no-pause -l fingerprint-bypass.js
```
```
frida -U -F YOUR_BINARY --no-pause -l fingerprint-bypass.js
```
When using frida gadget with the `script` interaction type, add the following code to print to logcat the console.log output.

```js
var android_log_write = new NativeFunction(
    Module.getExportByName(null, '__android_log_write'),
    'int',
    ['int', 'pointer', 'pointer']
);
var tag = Memory.allocUtf8String("[frida-script][ax]");
console.log = function(str) {
    android_log_write(3, tag, Memory.allocUtf8String(str));
}

```


## References 

https://labs.withsecure.com/publications/how-secure-is-your-android-keystore-authentication
