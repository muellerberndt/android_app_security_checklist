# Android App Security Checklist

A checklist with security considerations for designing, testing, and releasing secure Android apps. It is based on the [OWASP Mobile Application Security Verification Standard](https://github.com/OWASP/owasp-masvs/), [Mobile Application Security Testing Guide](https://github.com/OWASP/owasp-mstg/) and others. Follow the links on each checklist item for detailed instructions and recommendations.

------------------------------------------------------------------------------
## Data Storage

- [ ] [The Keystore is used to store sensitive data, such as user credentials or cryptographic keys.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#keystore)
- [ ] [No sensitive data is written to application logs.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#logs)
- [ ] [No sensitive data is shared with third parties unless it is a necessary part of the architecture.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#determining-whether-sensitive-data-is-shared-with-third-parties-mstg-storage-4)
- [ ] [The keyboard cache is disabled on text inputs that process sensitive data.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#determining-whether-the-keyboard-cache-is-disabled-for-text-input-fields-mstg-storage-5)
- [ ] [No sensitive data is exposed via IPC mechanisms.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#determining-whether-sensitive-stored-data-has-been-exposed-via-ipc-mechanisms-mstg-storage-6)
- [ ] [No sensitive data, such as passwords or pins, is exposed through the user interface.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#checking-for-sensitive-data-disclosure-through-the-user-interface-mstg-storage-7)
- [ ] [No sensitive data is included in backups.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#testing-backups-for-sensitive-data-mstg-storage-8)
- [ ] [Sensitive data is removed from views when they're moved to the background.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#finding-sensitive-information-in-auto-generated-screenshots-mstg-storage-9)

## Platform Interaction

- [ ] [The app only requests the minimum set of permissions necessary.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05h-Testing-Platform-Interaction.md#testing-app-permissions-mstg-platform-1)
- [ ] [All inputs from external sources and the user are validated and if necessary sanitized. This includes data received via the UI, IPC mechanisms such as intents, custom URLs, and network sources.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05h-Testing-Platform-Interaction.md#testing-for-injection-flaws-mstg-platform-2)
- [ ] [The app does not export sensitive functionality via custom URL schemes without proper protection.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05h-Testing-Platform-Interaction.md#testing-deep-links-mstg-platform-3)
- [ ] [The app does not export sensitive functionality through IPC facilities without proper protection.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05h-Testing-Platform-Interaction.md#testing-for-sensitive-functionality-exposure-through-ipc-mstg-platform-4)
- [ ] [JavaScript is disabled in WebViews unless explicitly required.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05h-Testing-Platform-Interaction.md#testing-javascript-execution-in-webviews-mstg-platform-5)
- [ ] [WebViews are configured to allow only the minimum set of protocol handlers required (ideally, only https is supported). Potentially dangerous handlers, such as file, tel and app-id, are disabled.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05h-Testing-Platform-Interaction.md#testing-webview-protocol-handlers-mstg-platform-6)
- [ ] [If native methods of the app are exposed to a WebView, that WebView only renders JavaScript contained within the app package](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05h-Testing-Platform-Interaction.md#determining-whether-java-objects-are-exposed-through-webviews-mstg-platform-7).
- [ ] [Object serialization, if any, is implemented using safe serialization APIs.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05h-Testing-Platform-Interaction.md#testing-object-persistence-mstg-platform-8)

## Cryptography

- [ ] [The app does not rely on symmetric cryptography with hardcoded keys as a sole method of encryption.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05e-Testing-Cryptography.md#testing-symmetric-cryptography-mstg-crypto-1)
- [ ] [The app uses proven implementations of cryptographic primitives.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04g-Testing-Cryptography.md#cryptographic-apis-on-android-and-ios)
- [ ] [The app uses cryptographic primitives that are appropriate for the particular use-case, configured with parameters that adhere to industry best practices.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04g-Testing-Cryptography.md#common-configuration-issues-mstg-crypto-1-mstg-crypto-2-and-mstg-crypto-3)
- [ ] [The app does not use cryptographic protocols or algorithms that are widely considered depreciated for security purposes.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04g-Testing-Cryptography.md#identifying-insecure-andor-deprecated-cryptographic-algorithms-mstg-crypto-4)
- [ ] [All random values are generated using a sufficiently secure random number generator.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04g-Testing-Cryptography.md#weak-random-number-generators)
- [ ] The app doesn't re-use the same cryptographic key for multiple purposes.

## Authentication

- [ ] [If the app provides users with access to a remote service, an acceptable form of authentication such as username/password authentication is performed at the remote endpoint.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#verifying-that-appropriate-authentication-is-in-place-mstg-arch-2-and-mstg-auth-1)
- [ ] [A password policy exists and is enforced at the remote endpoint.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#testing-best-practices-for-passwords-mstg-auth-5-and-mstg-auth-6)
- [ ] [The remote endpoint implements an exponential back-off, or temporarily locks the user account, when incorrect authentication credentials are submitted an excessive number of times.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#login-throttling)
- [ ] [If stateful session management is used, the remote endpoint uses randomly generated session identifiers to authenticate client requests without sending the user's credentials.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#testing-stateful-session-management-mstg-auth-2)
- [ ] [If stateless token-based authentication is used, the server provides a token signed using a secure algorithm.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#testing-stateless-token-based-authentication-mstg-auth-3)
- [ ] [The remote endpoint terminates the existing stateful session or invalidates the stateless session token when the user logs out.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#testing-user-logout-mstg-auth-4)
- [ ] [Biometric authentication, if any, is not event-bound (i.e. using an API that simply returns "true" or "false"). Instead, it is based on unlocking the Keystore.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05f-Testing-Local-Authentication.md#testing-biometric-authentication-mstg-auth-8)

## WebViews

- [ ] [WebViews correctly validate incoming URLs.](https://blog.oversecured.com/Android-security-checklist-webview/#insufficient-url-validation)
- [ ] [The app sanitizes the JavaScript data when injected.](https://blog.oversecured.com/Android-security-checklist-webview/#javascript-code-injections)
- [ ] [WebViewClient sanitizes the Intent received from the URL before launching it.](https://blog.oversecured.com/Android-security-checklist-webview/#attacks-on-internal-url-handlers)

## Network

- [ ] [Data is encrypted on the network using TLS. The secure channel is used consistently throughout the app.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05g-Testing-Network-Communication.md#testing-data-encryption-on-the-network-mstg-network-1)
- [ ] [The TLS settings are in line with current best practices, or as close as possible if the mobile operating system does not support the recommended standards.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04f-Testing-Network-Communication.md#verifying-the-tls-settings-mstg-network-2)
- [ ] [The app verifies the X.509 certificate of the remote endpoint when the secure channel is established. Only certificates signed by a trusted CA are accepted.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05g-Testing-Network-Communication.md#testing-endpoint-identify-verification-mstg-network-3)

## Code Quality

- [ ] [The app is signed and provisioned with valid certificate.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05i-Testing-Code-Quality-and-Build-Settings.md#making-sure-that-the-app-is-properly-signed-mstg-code-1)
- [ ] [The app has been built in release mode, with settings appropriate for a release build (e.g. non-debuggable).](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05i-Testing-Code-Quality-and-Build-Settings.md#testing-whether-the-app-is-debuggable-mstg-code-2)
- [ ] [Debugging symbols have been removed from native binaries.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05i-Testing-Code-Quality-and-Build-Settings.md#testing-for-debugging-symbols-mstg-code-3)
- [ ] [Debugging code has been removed, and the app does not log verbose errors or debugging messages.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05i-Testing-Code-Quality-and-Build-Settings.md#testing-for-debugging-code-and-verbose-error-logging-mstg-code-4)
- [ ] [Third-party libraries have been checked for weaknesses](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05i-Testing-Code-Quality-and-Build-Settings.md#checking-for-weaknesses-in-third-party-libraries-mstg-code-5)
- [ ] [The app catches and handles possible exceptions.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05i-Testing-Code-Quality-and-Build-Settings.md#testing-exception-handling-mstg-code-6-and-mstg-code-7)
- [ ] [Error handling logic in security controls denies access by default.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05i-Testing-Code-Quality-and-Build-Settings.md#testing-exception-handling-mstg-code-6-and-mstg-code-7)
- [ ] [In unmanaged code, memory is allocated, freed and used securely.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05i-Testing-Code-Quality-and-Build-Settings.md#memory-corruption-bugs-mstg-code-8)
- [ ] [Free security features offered by the toolchain, such as byte-code minification, stack protection, PIE support and automatic reference counting, are activated.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05i-Testing-Code-Quality-and-Build-Settings.md#make-sure-that-free-security-features-are-activated-mstg-code-9)

## Defense-in-Depth

- [ ] [A second factor of authentication exists at the remote endpoint and the 2FA requirement is consistently enforced.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#testing-two-factor-authentication-and-step-up-authentication-mstg-auth-9-and-mstg-auth-10)
- [ ] [Sessions and access tokens are invalidated at the remote endpoint after a predefined period of inactivity.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#testing-session-timeout-mstg-auth-7)
- [ ] [The app does not hold sensitive data in memory longer than necessary, and memory is cleared explicitly after use.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#cleaning-out-key-material)
- [ ] [The app enforces a minimum device-access-security policy, such as requiring the user to set a device passcode.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#testing-the-device-access-security-policy-mstg-storage-11)
- [ ] [Step-up authentication is required to enable actions that deal with sensitive data or transactions.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#testing-two-factor-authentication-and-step-up-authentication-mstg-auth-9-and-mstg-auth-10)
- [ ] [The app either uses its own certificate store, or pins the endpoint certificate or public key, and subsequently does not establish connections with endpoints that offer a different certificate or key, even if signed by a trusted CA.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05g-Testing-Network-Communication.md#testing-custom-certificate-stores-and-certificate-pinning-mstg-network-4)
- [ ] [The app doesn't rely on a single insecure communication channel (email or SMS) for critical operations, such as enrollments and account recovery.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04f-Testing-Network-Communication.md#making-sure-that-critical-operations-use-secure-communication-channels-mstg-network-5)
- [ ] [The app detects whether it is being executed on a rooted device. Depending on the business requirement, users are warned, or the app is terminated if the device is rooted.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05j-Testing-Resiliency-Against-Reverse-Engineering.md#testing-root-detection-mstg-resilience-1)
- [ ] [The app informs the user of all login activities with his or her account. Users are able view a list of devices used to access the account, and to block specific devices.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#testing-login-activity-and-device-blocking-mstg-auth-11)
- [ ] [The app educates the user about the types of personally identifiable information.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04i-Testing-User-Privacy-Protection.md#testing-user-education-mstg-storage-12)
