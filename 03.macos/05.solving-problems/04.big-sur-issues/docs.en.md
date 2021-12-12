---
title: "Issues specific to macOS 11 Big Sur"
taxonomy:
  category:
    - docs
visible: true
---

- [Currently existing problems (Big Sur 11.2)](#current)
  - [Compatibility with local proxies](#local-proxies)
    - [Configuring an upstream Shadowsocks proxy](#shadowsocks)
    - [Cofiguring an upstream Surge proxy](#surge)
  - [Compatibility with Cisco AnyConnect](#cisco)
  - [Compatibility with Flutter](#flutter)
  - [VPN apps with legacy API](#legacy-api)
- [Already fixed problems](#fixed)
  - [Compatibility with Little Snitch 5](#little-snitch)
- [Alternatives to Network Extension](#alternatives)
  - [Using "Automatic proxy" filtering mode](#automatic-proxy)
  - [Enabling Kernel Extension in Big Sur](#kernel-extension)

The newest version of macOS, **Big Sur**, has been released in late 2020. It introduces the new API, Network Extensions API to replace the old Kernel Extensions API. And it already causes some problems to many applications, AdGuard not being an exception. In this article we go over the known issues and possible ways to solve them.

<a id="current"></a>

## Currently existing problems (Big Sur 11.2)

These problems aren't fixed by Apple yet, or fixed only partially.

<a id="local-proxies"></a>

### Compatibility with local proxies

> Note: in Big Sur 11.1 (and newer macOS versions) AdGuard can filter local proxies (mostly) without any problems. If you encounter any issues in OS versions 11.1+, or if you're using Big Sur 11.0, remove the local proxy from System settings and configure an upstream proxy in AdGuard by following the instruction below.

> After Big Sur 11.3 update, the problems with local proxies came back. Apple will likely roll out a fix soon, and we're also working on a workaround. All required changes are already made to the [Nightly version](http://agrd.io/mac_nightly) of AdGuard for Mac.

To configure an upstream proxy in AdGuard for Mac in Big Sur, you need to go to _AdGuard menu -> Advanced -> Advanced Settings..._. Click on the _Value_ area of the `upstream.proxy` setting to configure a proxy.

<img src="https://cdn.adguard.com/public/Adguard/kb/BigSur/problems/proxy_en.png" style="max-width: 650px;">

Enter a string that looks like `scheme://user:password@host:port`, where

- `scheme` is either `http`, `https`, `socks4` or `socks5`, depending on your proxy type.

> If you use `socks5` proxy type, set the value of the `upstream.proxy.socks5udp` setting to `true` to make AdGuard route UDP traffic to the proxy server.

- `user` and `password` are corresponding username and password of your proxy (if needed). Ignore either or both when not applicable
- `host` is the IP address of your proxy server
- `port` is the desired port number to be used by the proxy server

> Example: `socks5://localhost:6322` will configure a SOCKS5 local proxy that listens to port 6322 and doesn't require a username or a password.

Click _Apply_ to make AdGuard route all traffic that went through it to the configured proxy server.

If you run into any problems, please contact our tech support: support@adguard.com.

<a id="shadowsocks"></a>

#### Example 1: Configuring an upstream Shadowsocks proxy

Here's an example of how to configure an upstream proxy for [Shadowsocks](https://shadowsocks.org/en/index.html).

First of all, you need a working server side for your proxy. Most likely, to set it up, you would use a JSON file like this (`server` and `password` values were chosen randomly here):

```
{
    "server":"111.222.333.444",
    "server_port":8388,
    "local_port":1080,
    "password":"barfoo!",
    "timeout":600,
    "method":"chacha20-ietf-poly1305"
}
```

> You can find more information about how to get started on [Shadowsocks website](https://shadowsocks.org/en/config/quick-guide.html).

Then you'd have to install Shadowsocks client on your Mac. Make sure that you select 'Manual Mode' or 'Auto Mode' in its settings! The configuration won't work if you select 'Global Mode' (or 'Auto Mode' in Big Sur versions prior to 11.1).

<img src="https://cdn.adguard.com/public/Adguard/kb/BigSur/problems/shadowsocks.png" style="max-width: 350px;">

Now go to _AdGuard menu -> Advanced -> Advanced Settings..._ and set the _Value_ area of the `upstream.proxy` setting to `socks5://localhost:1080`. Notice that you need to use "local_port" value from the JSON file here.

Because Shadowsocks uses SOCKS5, you also need to set the value of the `upstream.proxy.socks5udp` setting in AdGuard Advanced Settings to `true` to make AdGuard route UDP traffic to the proxy server.

<a id="surge"></a>

#### Example 2: Configuring an upstream Surge proxy

In Big Sur v11.1+, there are no known conflicts between AdGuard and Surge proxy. If you are using an older version of Big Sur (prior to 11.1), check that **System Proxy** in the bottom right corner is disabled. Otherwise, Surge won't work with AdGuard. On the other hand, **Enhanced Mode** can be enabled without causing a conflict in any Big Sur version.

<img src="https://cdn.adguard.com/public/Adguard/kb/BigSur/problems/surge.png" style="max-width: 800px;">

Now go to _AdGuard menu -> Advanced -> Advanced Settings..._ and set the _Value_ area of the `upstream.proxy` setting to `socks5://localhost:6153` or `http://localhost:6152`, depending on which type of proxy you want to use. Notice that you need to use **port** value that's indicated in the **Events** area of the **Activity** tab in your Surge client.

If you chose SOCKS5 protocol, you also need to set the value of the `upstream.proxy.socks5udp` setting in AdGuard Advanced Settings to `true` to make AdGuard route UDP traffic to the proxy server.

<a id="cisco"></a>

### Compatibility with Cisco AnyConnect

AdGuard will not work together with Cisco AnyConnect while in _Network Extension_ mode. You have to switch AdGuard to _Automatic Proxy_ mode. To do so, follow [this instruction](#automatic-proxy).

<a id="flutter"></a>

### Compatibility with Flutter

If you use Flutter alongside AdGuard in "Network Extension" mode (or any other "Transparent Proxy"-type app) in Big Sur, you will run into problems: projects won't open and Flutter will be effectively broken. We have already reported this bug to Apple. Meanwhile, you can use these temporary solutions:

1. Use AdGuard in [Automatic Proxy](#automatic-proxy) mode

2. Disable SIP and switch AdGuard to Kernel Extension mode as explained [here](#kernel-extension).

<a id="legacy-api"></a>

### VPN apps with legacy API

Despite AdGuard is displayed as a VPN in system settings, it shouldn't cause any conflicts when working alongside other VPN-based apps. However, if you're using a VPN-based app that was downloaded from outside AppStore, there's a chance it uses the old VPN API and you have to exclude it from filtering:

1. Open AdGuard's menu.
2. Select _Preferences..._.
3. Switch to the _Network_ tab.
4. Click the _Applications..._ button.
5. Find the app you want to exclude and uncheck the checkbox next to it.

<img src="https://cdn.adguard.com/public/Adguard/kb/BigSur/problems/legacy-api.png" style="max-width: 650px;">

<a id="fixed"></a>

## Already fixed problems

These problems have been fixed by Apple by now but can be encountered in the older versions of macOS Big Sur.

<a id="little-snitch"></a>

### Compatibility with Little Snitch 5

At this moment, Network Extension mode in AdGuard isn't compatible with [Little Snitch 5](https://obdev.at/products/littlesnitch/index.html). When both are running, there's a chance to encounter issues with various apps' behavior, even if they aren't filtered by AdGuard. This problem is directly caused by a bug in Big Sur, and we've already informed Apple about it. This leaves us to believe that this issue will get resolved in one of the next updates.

Needs to be said that this problem can't be solved by disabling connections monitoring in Little Snitch, because this action doesn't unload Little Snitch's extension from the system. We recommend to switch to [**Automatic Proxy**](#automatic-proxy) filtering mode when running AdGuard alongside with Little Snitch on Big Sur, at least until Apple fixes the bug.

<a id="alternatives"></a>

## Alternatives to using a Network Extension

It's impossible to foresee each and every possible problem that can pop up in Big Sur, there are countless various hardware/software and settings configurations. If you face any compatibility issues, please contact our support team, but feel free to try one of these workarounds first:

<a id="automatic-proxy"></a>

### Using "Automatic proxy" filtering mode

If you face problems in Big Sur which can't be resolved by any of the methods above, you can try switching AdGuard to _Automatic proxy_ mode.

1. Open AdGuard's menu.
2. Select _Preferences..._.
3. Switch to the _Network_ tab.
4. Click the _Select Mode..._ button.
5. Select _Automatic Proxy_.

<img src="https://cdn.adguard.com/public/Adguard/kb/BigSur/problems/automatic-proxy_en.png" style="max-width: 650px;">

Now AdGuard has automatically added a **.pac** file to your Mac's network settings, so that the system will consider AdGuard a proxy and try to send all traffic through AdGuard.

> Take into account that some apps may ignore this system setting and their traffic will not be filtered.

<a id="kernel-extension"></a>

### Enabling Kernel Extension in Big Sur

By default AdGuard uses Network Extension framework in Big Sur as the old Kernel Extension framework is disabled there. This can cause some compatibility problems, but to enable Kernel Extension back, you need to disable System Integrity Protection (SIP) first. To disable SIP, follow this instruction:

1. Click the _Apple symbol_ in the Menu bar.
2. Click _Restart…_
3. Hold down _Command-R_ to reboot into Recovery Mode.
4. Click _Utilities_.
5. Select _Terminal_.
6. Type `csrutil disable`.
7. Press _Return_ or _Enter_ on your keyboard.
8. Click the _Apple symbol_ in the Menu bar.
9. Click _Restart…_

Now that SIP is disabled, this is how you enable Kernel Extension:

<img src="https://cdn.adguard.com/public/Adguard/kb/BigSur/problems/kernel_en.png" style="max-width: 650px;">

1. Open AdGuard's menu.
2. Select _Preferences..._.
3. Switch to the _Network_ tab.
4. Click the _Select Mode..._ button.
5. Select _Kernel Extension_.
6. Confirm that you want to switch to Kernel Extension.

> However, we only recommend using this method if everything else fails, as this may lead to unexpected issues.
