---
title: '"Potential Security Risk" error'
taxonomy:
  category:
    - docs
visible: true
---

<img src="https://cdn.adguard.com/public/Adguard/kb/en/certificate/cert_error_en.png" style="border: 1px solid #efefef; padding: 2px; max-width: 700px;" />

The "Potential security risk ahead" error is most commonly encountered in Firefox-based browsers like Mozilla Firefox, PaleMoon, Waterfox and such.

Starting with v68, under certain conditions Firefox normally trusts certificates from the system storage. However, sometimes for reasons outside of our control the trust mechanism faults, which leads to the "Connection is untrusted" error. To fix it, it's necessary to download AdGuard certificate and install it to Firefox's local storage manually. To do so, follow these steps:

> This instruction is for Firefox browser. Names of buttons and menu items may differ in other Firefox-based browsers.

1. Run AdGuard.

2. Go to [http://local.adguard.org/cert](http://local.adguard.org/cert) and click the _Download_ button. The browser should start downloading **cert.cer** file.

> You can also open the download page by clicking on the link via the AdGuard app at _Settings - Network - HTTPS filtering_.

<img src="https://cdn.adguard.com/public/Adguard/kb/en/certificate/cert_win_en.png" style="border: 1px solid #efefef; padding: 2px; max-width: 500px;" />

3. Open your browser and then open _Settings_.

4. Go to _Privacy & Security_ tab.

5. Scroll down to _Certificates_ and click on the _View Certificates_ button.

<img src="https://cdn.adguard.com/public/Adguard/kb/en/certificate/cert_settings_en.png" style="border: 1px solid #efefef; padding: 2px; max-width: 700px;" />

6. Select _Authorities_ tab.

7. Click _Import..._.

<img src="https://cdn.adguard.com/public/Adguard/kb/en/certificate/cert_import_en.png" style="border: 1px solid #efefef; padding: 2px; max-width: 500px;" />

8. Browse the downloaded **cert.cer** file and click _Open_.

9. Click _OK_.

You've successfully installed AdGuard certificate. Restart the browser and the error should go away.
