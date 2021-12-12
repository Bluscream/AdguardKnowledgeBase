---
title: How to collect HAR file
published: true
taxonomy:
  category:
    - docs
---

## Creating an HAR File

HAR files help our technical support teams troubleshoot complex issues. To create these files, we recommend using Chrome or Firefox. However, IE 11, Edge, and Safari also provide .har file generation and export capability.

[Google Chrome](#chrome)

[Edge](#edge)

[Firefox](#firefox)

[Internet Explorer 11](#ie11)

[Safari](#safari)

[Compressing an HAR file for Windows](#harwindows)

[Compressing an HAR file for Mac](#harmac)

## <a id="chrome"></a> Chrome

To create an HAR file in Chrome:

1. Go to the URL where the issue occurs. Do not reproduce the issue yet.

2. Open **_Developer Tools_**:

- From menu: **_Menu > More Tools > Developer Tools_**.
- Keyboard: **_Ctrl+Shift+C_**, or **_Ctrl+Alt+I_**, or **_⌥+⌘+I for Mac_**.

3. Click on the **_Network tab_**.

4. Locate the round button at the top left of the Network tab and confirm it is in red recording mode. If it's grey, click to turn red to start recording.

5. Use the **_clear_** button (the circle button with a line through it next to the record button) to clear all previous activity.

6. Select the **_Preserve log_** check box on the Network tab.

7. Reproduce the steps that create the issue.

8. Save session as a .har file by right clicking on the grid and selecting **_Save as HAR with content_**.

9. Forward to AdGuard support (support@adguard.com) with detailed explanation of issue. Supporting screenshots can be helpful, as well.

## <a id="edge"></a> Edge

To create an HAR file in Edge:

1. From the webpage experiencing the issue, press the **_F12_** key to open **_Developer Tools_**.

2. Select the **_Network_** tab.

3. Refresh the webpage to engage HTTP communications, and wait for one minute.

4. Click the **_Disk_** icon or press and hold **_CTRL+S_** to save a HAR file.

5. Complete saving by using **_Save As…_**

6. Forward to AdGuard support (support@adguard.com) with detailed explanation of issue. Supporting screenshots can be helpful, as well.

## <a id="firefox"></a> Firefox

To create an HAR file in Firefox:

1. Go to the URL where the issue occurs. Do not reproduce the issue yet.

2. Open Developer Tools in **_Network_** mode:

- From menu: **_Menu > Web Developer > Network_**.
- Keyboard: **_Ctrl+Shift+C_**, or **⌥+⌘+E (Mac)**.

3. Note the **_play/pause_** button at the top left of the Network tab.

- Button should be in play mode.

4. If any information is currently displayed in the grid, clear by clicking the **_delete trash can_** button next to the play/pause button.

5. Select the **_Persist Logs_** check box on the Network tab.

6. Reproduce the steps that create the issue.

7. Save session as a .har file by right clicking on the grid and selecting **_Save all as HAR_**.

8. Forward to AdGuard support (support@adguard.com) with detailed explanation of issue. Supporting screenshots can be helpful, as well.

## <a id="ie11"></a> Internet Explorer 11

To create an HAR file in Internet Explorer 11:

1. Go to the URL where the issue occurs. Do not reproduce the issue yet.

2. Open Developer Tools in **_Network_** mode:

- From Tools cog wheel menu: **_Developer Tools_** > **_Network tab_**.
- Keyboard: **_F12 > Network_** tab

3. Note the start profiling session **_Play_** button and stop profiling **_Stop_** button at top left of Network tab.

- Play button will be gray when recording and Stop button will be red. Put in **_Play_** mode.

4. Clear any session info appearing in the lower grid using the **_Clear session_** button on Network tab. Hover over icons to see names.

- **_Clear session_** button is a three line icon with an x on it.

5. Reproduce the steps that create the issue.

6. Save session as a .har file by clicking on the **_Save disk_** button (Export as HAR) on Network tab.

7. Forward to AdGuard support (support@adguard.com) with detailed explanation of issue. Supporting screenshots can be helpful, as well.

## <a id="safari"></a> Safari

To create an HAR file in Safari:

1. Check the Safari menu bar at the top of the screen for a **_Develop_** menu. Check the checkbox at the bottom next to **_Show Develop menu in menu bar_**.

- If not visible, turn it on by going to **_Safari > Preferences > Advanced_**.

2. Go to the URL where the issue occurs. Do not reproduce the issue yet.

3. Open **_Network_** tab in Web Inspector:

- From menu: **_Develop > Show Web Inspector > Network_**.
- Keyboard: **_⌥+⌘+I > Network_**

4. Check **_Preserve Log_** checkbox on right side of the Network tabs.

5. Clear current Network items by clicking the **_delete Trash_** icon at the far right of Network tabs.

6. Reproduce the steps that create the issue.

7. Save session as a .har file by clicking the **_Export_** icon next to **_Preserve Log_**.

8. Forward to AdGuard support (support@adguard.com) with detailed explanation of issue. Supporting screenshots can be helpful, as well.

## <a id="harmac"></a> Compressing an HAR file for Mac

To compress an HAR file for Mac:

1. Locate the HAR file that you want to compress.

2. Right click on the HAR file.

3. Choose **_Compress_** from the shortcut menu.

4. A compressed file will have the name of the original HAR file with a **_.zip_** extension.

## <a id="harwindows"></a> Compressing an HAR file for Windows

To compress an HAR file for Windows:

1. Locate the HAR file that you want to compress.

2. Right-click on the HAR file.

3. Choose **_Send to_**.

4. Select **_Compressed_** (zipped) folder.

5. A new zipped folder with the same name is created in the same location.
