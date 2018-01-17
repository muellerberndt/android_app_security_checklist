# Android App Security Checklist

A checklist with security considerations for designing, testing, and releasing secure Android apps. It is based on the [OWASP Mobile Application Security Verification Standard](https://github.com/OWASP/owasp-masvs/) and [Mobile Security Testing Guide](https://github.com/OWASP/owasp-mstg/). Follow the links on each checklist item for detailed instructions and recommendations.

------------------------------------------------------------------------------
## Data Storage

- [ ] [The Keystore is used to store sensitive data, such as user credentials or cryptographic keys.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#testing-local-storage-for-sensitive-data)
- [ ] [No sensitive data is written to application logs.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#testing-logs-for-sensitive-data)
- [ ] [No sensitive data is shared with third parties unless it is a necessary part of the architecture.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#determining-whether-sensitive-data-is-sent-to-third-parties)
- [ ] [The keyboard cache is disabled on text inputs that process sensitive data.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#determining-whether-the-keyboard-cache-is-disabled-for-text-input-fields)
- [ ] [The clipboard is deactivated on text fields that may contain sensitive data.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#finding-sensitive-data-on-the-clipboard)
- [ ] [No sensitive data is exposed via IPC mechanisms.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#determining-whether-sensitive-stored-data-has-been-exposed-via-ipc-mechanisms)
- [ ] [No sensitive data, such as passwords or pins, is exposed through the user interface.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#checking-for-sensitive-data-disclosure-through-the-user-interface)

## Platform Interaction

- [ ] [The app only requests the minimum set of permissions necessary.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05h-Testing-Platform-Interaction.md#testing-app-permissions)
- [ ] [All inputs from external sources and the user are validated and if necessary sanitized. This includes data received via the UI, IPC mechanisms such as intents, custom URLs, and network sources.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04h-Testing-Code-Quality.md#testing-code-quality)
- [ ] [The app does not export sensitive functionality via custom URL schemes without proper protection.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05h-Testing-Platform-Interaction.md#testing-custom-url-schemes)
- [ ] [The app does not export sensitive functionality through IPC facilities without proper protection.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05h-Testing-Platform-Interaction.md#testing-for-sensitive-functionality-exposure-through-ipc)
- [ ] [JavaScript is disabled in WebViews unless explicitly required.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05h-Testing-Platform-Interaction.md#testing-javascript-execution-in-webviews)
- [ ] [WebViews are configured to allow only the minimum set of protocol handlers required (ideally, only https is supported). Potentially dangerous handlers, such as file, tel and app-id, are disabled.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05h-Testing-Platform-Interaction.md#testing-webview-protocol-handlers)
- [ ] [If native methods of the app are exposed to a WebView, that WebView only renders JavaScript contained within the app package](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05h-Testing-Platform-Interaction.md#testing-whether-java-objects-are-exposed-through-webviews).
- [ ] [Object serialization, if any, is implemented using safe serialization APIs.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05h-Testing-Platform-Interaction.md#user-content-testing-object-persistence)

## Cryptography

- [ ] [The app does not rely on symmetric cryptography with hardcoded keys as a sole method of encryption.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04g-Testing-Cryptography.md#user-content-testing-for-misuse-and-misconfiguration-of-cryptography)
- [ ] [The app uses proven implementations of cryptographic primitives.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04g-Testing-Cryptography.md#user-content-testing-for-misuse-and-misconfiguration-of-cryptography)
- [ ] [The app uses cryptographic primitives that are appropriate for the particular use-case, configured with parameters that adhere to industry best practices.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04g-Testing-Cryptography.md#user-content-testing-for-misuse-and-misconfiguration-of-cryptography)
- [ ] [The app does not use cryptographic protocols or algorithms that are widely considered depreciated for security purposes.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04g-Testing-Cryptography.md#user-content-testing-for-insecure-andor-deprecated-cryptographic-algorithms)
- [ ] [All random values are generated using a sufficiently secure random number generator.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05e-Testing-Cryptography.md#user-content-testing-random-number-generation)
- [ ] The app doesn't re-use the same cryptographic key for multiple purposes.

## Authentication

- [ ] [If the app provides users with access to a remote service, an acceptable form of authentication such as username/password authentication is performed at the remote endpoint.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#user-content-testing-authentication-on-the-back-end)
- [ ] [A password policy exists and is enforced at the remote endpoint.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#user-content-testing-the-password-policy)
- [ ] [The remote endpoint implements an exponential back-off, or temporarily locks the user account, when incorrect authentication credentials are submitted an excessive number of times.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#user-content-testing-excessive-login-attempts)
- [ ] [If stateful session management is used, the remote endpoint uses randomly generated session identifiers to authenticate client requests without sending the user's credentials.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#user-content-testing-stateful-session-management)
- [ ] [If stateless token-based authentication is used, the server provides a token signed using a secure algorithm.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#user-content-testing-stateless-token-based-authentication)
- [ ] [The remote endpoint terminates the existing stateful session or invalidates the stateless session token when the user logs out.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#user-content-testing-user-logout)
- [ ] [Biometric authentication, if any, is not event-bound (i.e. using an API that simply returns "true" or "false"). Instead, it is based on unlocking the Keystore.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05f-Testing-Local-Authentication.md#testing-biometric-authentication)

## Network

- [ ] [Data is encrypted on the network using TLS. The secure channel is used consistently throughout the app.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04f-Testing-Network-Communication.md#testing-for-unencrypted-sensitive-data-on-the-network)
- [ ] [The TLS settings are in line with current best practices, or as close as possible if the mobile operating system does not support the recommended standards.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04f-Testing-Network-Communication.md#testing-for-unencrypted-sensitive-data-on-the-network#verifying-the-tls-settings)
- [ ] [The app verifies the X.509 certificate of the remote endpoint when the secure channel is established. Only certificates signed by a trusted CA are accepted.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05g-Testing-Network-Communication.md#testing-endpoint-identify-verification)

## Code Quality

- [ ] [The app is signed and provisioned with valid certificate.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05i-Testing-Code-Quality-and-Build-Settings.md#verifying-that-the-app-is-properly-signed)
- [ ] [The app has been built in release mode, with settings appropriate for a release build (e.g. non-debuggable).](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05i-Testing-Code-Quality-and-Build-Settings.md#testing-if-the-app-is-debuggable)
- [ ] [Debugging symbols have been removed from native binaries.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05i-Testing-Code-Quality-and-Build-Settings.md#testing-for-debugging-symbols)
- [ ] [Debugging code has been removed, and the app does not log verbose errors or debugging messages.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05i-Testing-Code-Quality-and-Build-Settings.md#testing-for-debugging-code-and-verbose-error-logging)
- [ ] [The app catches and handles possible exceptions.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05i-Testing-Code-Quality-and-Build-Settings.md#testing-exception-handling)
- [ ] [Error handling logic in security controls denies access by default.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05i-Testing-Code-Quality-and-Build-Settings.md#testing-exception-handling)
- [ ] [In unmanaged code, memory is allocated, freed and used securely.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04h-Testing-Code-Quality.md##user-content-testing-for-memory-corruption-bugs-in-native-code)
- [ ] [Free security features offered by the toolchain, such as byte-code minification, stack protection, PIE support and automatic reference counting, are activated.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05i-Testing-Code-Quality-and-Build-Settings.md#user-content-verify-that-free-security-features-are-activated)

## Defense-in-Depth

- [ ] [No sensitive data is included in backups generated by the mobile operating system.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#testing-for-sensitive-data-in-backups)
- [ ] [The app removes sensitive data from views when backgrounded.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#testing-for-sensitive-information-in-auto-generated-screenshots)
- [ ] [The app does not hold sensitive data in memory longer than necessary, and memory is cleared explicitly after use.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#testing-for-sensitive-data-in-memory)
- [ ] [The app enforces a minimum device-access-security policy, such as requiring the user to set a device passcode.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#testing-the-device-access-security-policy)
- [ ] [The app educates the user about the types of personally identifiable information.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#testing-the-device-access-security-policy)
- [ ] [A second factor of authentication exists at the remote endpoint and the 2FA requirement is consistently enforced.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#user-content-testing-2-factor-authentication-and-step-up-authentication)
- [ ] [Step-up authentication is required to enable actions that deal with sensitive data or transactions.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#user-content-testing-2-factor-authentication-and-step-up-authentication)
- [ ] [Sessions and access tokens are invalidated at the remote endpoint after a predefined period of inactivity.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04e-Testing-Authentication-and-Session-Management.md#user-content-testing-the-session-timeout)
- [ ] The app informs the user of all login activities with his or her account. Users are able view a list of devices used to access the account, and to block specific devices.
- [ ] [The app either uses its own certificate store, or pins the endpoint certificate or public key, and subsequently does not establish connections with endpoints that offer a different certificate or key, even if signed by a trusted CA.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05g-Testing-Network-Communication.md#user-content-testing-custom-certificate-stores-and-ssl-pinning)
- [ ] [The app doesn't rely on a single insecure communication channel (email or SMS) for critical operations, such as enrollments and account recovery.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x04f-Testing-Network-Communication.md#verifying-that-critical-operations-use-secure-communication-channels)
- [ ] [The app detects whether it is being executed on a rooted device. Depending on the business requirement, users are warned, or the app is terminated if the device is rooted.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05j-Testing-Resiliency-Against-Reverse-Engineering.md#user-content-testing-root-detection)
