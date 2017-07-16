# Android App Security Checklist

A checklist with security considerations for designing, testing, and releasing secure Android apps. It is based on the [OWASP Mobile Application Security Verification Standard](https://github.com/OWASP/owasp-masvs/) and [Mobile Security Testing Guide](https://github.com/OWASP/owasp-mstg/). Follow the links on each checklist item for detailed instructions and recommendations.

------------------------------------------------------------------------------
## Data Storage

- [ ] [The Keystore is used to store sensitive data, such as user credentials or cryptographic keys.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#testing-for-sensitive-data-in-local-storage)
- [ ] [No sensitive data is written to application logs.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#testing-for-sensitive-data-in-logs)
- [ ] [No sensitive data is shared with third parties unless it is a necessary part of the architecture.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#testing-whether-sensitive-data-is-sent-to-third-parties)
- [ ] [The keyboard cache is disabled on text inputs that process sensitive data.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#testing-whether-the-keyboard-cache-is-disabled-for-text-input-fields)
- [ ] [The clipboard is deactivated on text fields that may contain sensitive data.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#testing-for-sensitive-data-in-the-clipboard)
- [ ] [No sensitive data is exposed via IPC mechanisms.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#testing-whether-sensitive-data-is-exposed-via-ipc-mechanisms)
- [ ] [No sensitive data, such as passwords or pins, is exposed through the user interface.](https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#testing-for-sensitive-data-disclosure-through-the-user-interface)

## Platfom Interaction

- [ ] [The app only requests the minimum set of permissions 
