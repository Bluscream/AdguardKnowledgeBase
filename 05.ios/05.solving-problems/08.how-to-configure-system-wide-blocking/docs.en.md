---
title: "How to configure system-wide blocking with AdGuard for iOS?"
taxonomy:
  category:
    - docs
---

- [About system-wide blocking](#system-wide)
- [How to add a DNS filter/hosts file](#filters)

<a name="system-wide"></a>
System-wide blocking means blocking ads and trackers beyond the Safari browser, i.e. in other apps and browsers. This article will tell you how to set it up on your iOS device.

On iOS, the only way to block ads and trackers system-wide is to use [DNS filtering](https://kb.adguard.com/en/general/dns-filtering). First, you have to enable DNS protection. To do so, open _AdGuard for iOS settings_ —> _DNS protection_ and switch it on.

<img src="https://cdn.adguard.com/public/Adguard/Blog/ios_dns_protection.PNG" style="border: 1px solid #efefef; max-width: 350px; padding: 2px;">

Now, if your purpose is to block ads and trackers system-wide, you have two options:

1. Enable AdGuard DNS server (_Settings_ —> _DNS protection_ —> _DNS server_ —> _AdGuard DNS_).
2. Add a DNS filter/hosts file that will block ad and tracking domains, e.g. AdGuard DNS filter.

The second option takes a bit more time to set up but has several advantages:

- You can use any DNS server at your discretion and you are not tied up to a specific blocking server.
- You can add multiple DNS filters and/or hosts files at the same time, but you can't use multiple DNS servers at once.

<img src="https://cdn.adguard.com/public/Adguard/kb/DNS_filtering/how_dns_filtering_works_en.png" style="border: 1px solid #efefef; max-width: 350px; padding: 2px;">
<p align="center"><i>How DNS filtering works</i></p>

<a name="filters"></a>

### How to add a DNS filter/hosts file

You can add any DNS filter or hosts file, the instruction will be the same for all of them. For the sake of the example, let's add [AdGuard DNS filter](https://github.com/AdguardTeam/AdguardSDNSFilter). It is composed of several other filters (AdGuard Base filter, Social Media filter, Tracking Protection filter, Mobile Ads filter, EasyList, EasyPrivacy, etc.) and it's simplified specifically to be better compatible with DNS-level ad blocking.

1. Open _AdGuard for iOS settings_ —> _General_.
2. Enable _Advanced mode_. The 'Advanced settings' tab will appear. Open it.

<div style="display:flex">
     <div style="flex:1;padding-right:5px;">
          <img src="https://cdn.adguard.com/public/Adguard/Release_notes/iOS/v4.0/advanced_mode_en.jpg" style="border: 1px solid #efefef; max-width: 350px; padding: 2px;">
     </div>
     <div style="flex:1;padding-left:5px;">
          <img src="https://cdn.adguard.com/public/Adguard/Blog/ios_advanced_settings.PNG" style="border: 1px solid #efefef; max-width: 350px; padding: 2px;">
     </div>
</div>

> Note: We don't recommend touching other settings you'll find inside the _Advanced settings_ tab, especially when it comes to _Low-level settings_. Some of them might break the Internet connection or compromise your privacy and security, so it's better to be careful. The text below describes the exact actions required to add AdGuard DNS filter.

3. Copy this link: `https://raw.githubusercontent.com/AdguardTeam/FiltersRegistry/master/filters/filter_15_DnsFilter/filter.txt`.
4. Open _AdGuard for iOS settings_ —> _DNS protection_ —> _DNS filtering_ (available while _Advanced mode_ is enabled) —> _DNS filters_.
5. *Click *Add a filter\* button, paste the link into the filter URL field, and click 'Next'.

<img src="https://cdn.adguard.com/public/Adguard/Blog/ios_adding_a_filter.PNG" style="border: 1px solid #efefef; max-width: 350px; padding: 2px;">

> Add any number of other DNS filters the same way by pasting a different URL at step 3. You can find various filters and links to them [here](https://filterlists.com).
