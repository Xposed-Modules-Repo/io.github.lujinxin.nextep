<p align="center">
  <img src="https://raw.githubusercontent.com/lujinxin/NeXtep/main/assets/nextep-logo.png" alt="NeXtep icon" width="220">
</p>

<h2 align="center">NeXtep — A Tribute to and Continuation of OneStep</h2>

<p align="center">
  <a href="#english">English</a> / <a href="#中文">中文</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Android-16%2B-3DDC84?style=flat&logo=android&logoColor=white" alt="Android 16+">
  <img src="https://img.shields.io/github/v/release/Xposed-Modules-Repo/io.github.lujinxin.nextep?display_name=release" alt="Latest release">
  <img src="https://img.shields.io/badge/status-stable-2EA44F?style=flat" alt="Status: stable">
  <img src="https://img.shields.io/badge/Root-Required-C62828?style=flat" alt="Root required">
  <img src="https://img.shields.io/badge/license-Apache--2.0-4C1?style=flat" alt="Apache License 2.0">
  <img src="https://img.shields.io/badge/LSPosed-Module-3F51B5?style=flat" alt="LSPosed module">
  <img src="https://img.shields.io/badge/Kotlin-Source-7F52FF?style=flat&logo=kotlin&logoColor=white" alt="Kotlin source">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/lujinxin/NeXtep/main/assets/screenshots/workspace-overview.jpg" alt="NeXtep workspace overview" width="17%">&nbsp;
  <img src="https://raw.githubusercontent.com/lujinxin/NeXtep/main/assets/screenshots/quick-settings.jpg" alt="NeXtep Quick Settings workspace" width="17%">&nbsp;
  <img src="https://raw.githubusercontent.com/lujinxin/NeXtep/main/assets/screenshots/widgets-workspace.jpg" alt="NeXtep widgets workspace" width="17%">&nbsp;
  <img src="https://raw.githubusercontent.com/lujinxin/NeXtep/main/assets/screenshots/app-settings.jpg" alt="NeXtep app settings" width="17%">&nbsp;
  <img src="https://raw.githubusercontent.com/lujinxin/NeXtep/main/assets/screenshots/multitasking.jpg" alt="NeXtep multitasking workspace" width="17%">
</p>

## English

**NeXtep** is an **LSPosed module** that adds a **native side workspace** to ColorOS 16 / 17 while keeping the **stock launcher**. It provides **one main window and three live task slots**, with task switching, drag-and-drop, media controls, and customizable app shortcuts integrated into SystemUI.

The project primarily targets **OnePlus PLK110**, previously verified on **Android 16 / ColorOS 16**. Recent feature and compatibility testing is based on **Android 17 / ColorOS 17**. It relies on private Android and ColorOS behavior, so **other devices, ROM versions, and vendor launchers require adaptation**.

**Stable channel: 2.1.0.** Development builds are maintained on [beta](https://github.com/lujinxin/NeXtep/tree/beta); published APKs are available from GitHub Releases.

[Download and release notes](https://github.com/Xposed-Modules-Repo/io.github.lujinxin.nextep/releases) · [Demo video on Bilibili](https://www.bilibili.com/video/BV1iKHj6fEtL)

[Features](#features) · [Energy monitoring](#energy-monitoring-and-resource-use) · [Requirements](#requirements) · [Installation](#installation) · [Workspace controls](#open-and-close-the-workspace) · [External commands](#external-commands) · [Behavior switches](#behavior-switches)

### Features

#### Workspace and layout

- **Stock launcher:** keeps the ColorOS launcher without registering a replacement HOME app, with adaptations for launcher shortcut menus, desktop search, and the assistant panel.
- **One main window and three live slots:** keep several app tasks visible together and move whole tasks between the main window and slots.
- **Left and right layouts:** switch the slot sidebar using the layout buttons in the control area.
- **Portrait and both landscape orientations:** keep the control area and three slots in their layout relative to the phone while the main app follows system rotation. The embedded video can follow the screen direction independently, without moving the control area or rebuilding the slot layout.
- **Navigation-button adaptation:** optionally fit the main window and slots around the system navigation bar. Enable it for three-button navigation and disable it for gesture navigation; after changing the system navigation mode, toggle the option again.
- **Task retention:** restore eligible slot tasks that remain in the system when closing and reopening the workspace. Locking pauses slot output; unlocking restores the workspace with its tasks.
- **System integration:** coexists with native floating windows above the workspace panels, and includes adaptations for keyboard focus, notification shade and Control Center interaction, brightness controls, and video-window sizing.

#### Task management

| Action | How to use it |
|--------|---------------|
| Put the main app in a slot | With a regular app in the main window, tap the **+** in an empty slot. |
| Add from Recents | Center the desired task card in system Recents, then tap an empty slot's **+**. Recents stays open so you can add more apps. Exit split screen before adding a grouped split-screen card. |
| Exchange a slot with the main window | Tap an occupied slot, or long-press it and drag it onto the main window. |
| Move or exchange slots | Long-press an occupied slot and drag it onto an empty slot to move, or another occupied slot to exchange. Drop targets are highlighted during dragging. |
| Open an app in the main window | Tap its icon in the app strip. |
| Add from the app strip | Long-press an app icon and drag it onto the target slot. |
| Move a slot app to the background | Swipe outward: left for left-side slots, right for right-side slots. No long press is needed. This gesture can be disabled in Settings. |
| Move to the background by dragging | Long-press a slot and drag it onto the control area; release when **Release to move to background** appears. This remains available when swipe dismissal is disabled. |

Moving a slot app to the background frees the slot while retaining its task and leaving the main window unchanged. Opening an app from the launcher when it already occupies a slot exchanges it with the main window.

The optional **Park the previous main app when switching** setting moves the previous main app into an empty slot when switching from the app strip. If no empty slot is available, the app switch proceeds normally. It is disabled by default.

#### App strip and cloned apps

- **Automatic ordering:** arrange app shortcuts by recent usage; this is the default mode.
- **Manual ordering:** choose up to **36 apps**, remove shortcuts, and long-press selected entries to reorder them.
- **System app clones:** show cloned apps in the app strip and manual selection list, with clone labels to distinguish them from the original apps.

#### Gestures and app exclusions

- **Four-finger gesture:** pinch four fingers together to enter the workspace and spread them apart to exit. It is enabled by default and can be switched independently of the status-bar gesture.
- **Game exclusion:** enabled by default. Four-finger gestures are suspended when a system-recognized game is in the foreground or any workspace slot.
- **App blacklist:** select apps by icon and name, with a checkbox on the right. Four-finger gestures are suspended while a selected app or its system clone is in the foreground or a slot. The list is empty by default.

These exclusions apply to the four-finger gesture. Other workspace entry points remain available.

#### Media controls

- Display track artwork, title, and artist information from the active system media session, with **previous**, **play/pause**, and **next** controls as supported by the playback app.
- Tap the artwork, title, or another area outside the playback buttons to open the playback app in the main window. If it occupies a slot, it exchanges with the main window.
- Use a soft gradient drawn from the track artwork, retaining the colors while paused. With no media session or usable artwork, the card falls back to frosted wallpaper.

#### Control-area video

The control area has a **Video** page alongside **Controls**. Supported floating video windows are detected and displayed automatically, with playback remaining in the source app. The supported sources are system picture-in-picture (PiP) and eligible app-provided floating video windows; OEM freeform windows and secure/protected video are not generally supported.

1. Start playback in the source app and enable system PiP or the app's own floating video window.
2. Open the workspace. A supported floating window automatically moves into the **Video** page.
3. Swipe left or right across the control area to switch between **Controls** and **Video**. If the window remains outside, use the video shortcut on **Controls** or tap **Show video here** on **Video**.

Tap the embedded video to show compact glass controls. They hide automatically after a short delay.

| Control | Behavior |
|---------|----------|
| Play / pause | Use the source app's media session or an available native player control. Availability depends on the player. |
| Show full picture / Fill area | Default to uniform scaling with the complete picture centered in both axes. Choose fill explicitly to crop the edges and cover the area. |
| Return to floating window | Restore the original native window. The return shortcut on **Controls** provides the same action. |
| Close | Request the source player's own close action when available. |

- **Independent orientation:** the control area stays in place while the picture follows the current system display direction. With the phone held sideways, the control region appears tall: a portrait picture can use that space, while a landscape picture remains upright and gets space above and below when needed. System rotation lock is respected.
- **Retained embedding:** a rotation keeps the same valid native window embedded, rather than returning it to a floating window and capturing it again. Rotation also keeps the selected full-picture/fill mode.
- **Frosted surrounding area:** unused space shows the panel's wallpaper and frost effect. Black bars already drawn by the source player remain part of its picture; they are not detected or removed automatically.

Locking the device or closing the workspace restores the native window. A manually returned window stays outside after unlocking until it is captured again.

#### Energy monitoring and resource use

Open **Advanced → Runtime and diagnostics → Energy monitor** to view live readings and copy a report.

| Readings | Included information |
|----------|----------------------|
| Device battery | Battery level, temperature and temperature change, charge state, voltage, current, estimated net battery power, average discharge power from unplugged samples, thermal status, and power-saving mode. |
| Workspace runtime | Workspace state, retained slot displays, aggregate slot frame updates, module task queries and preview captures, and overall SystemUI host CPU usage. |

Sampling runs every **5 seconds** while this page is visible and the device is unlocked. Leaving the page or locking the device stops sampling. Unsupported readings appear as **—**.

Battery readings describe the whole device; charging power is not the device's total consumption. CPU usage covers the entire shared SystemUI process, with 100% representing one CPU core. These readings cannot isolate NeXtep's own battery consumption.

The workspace reduces idle task polling, combines pending refreshes, and avoids redundant preview captures. Retained slot displays request **60 Hz** independently of the physical screen's refresh rate. Slot output and task polling are suspended while locked, and the retained workspace resumes after unlocking.

#### Appearance and text

The control area and slot backgrounds use the wallpaper, including adaptations for ColorOS live wallpaper. Frosting leaves app content sharp.

| Setting | Options and behavior |
|---------|----------------------|
| Top content | NeXtep icon, time, date and weekday, blank, or custom text. The default is the icon; mode changes take effect immediately. |
| Clock seconds | Optional, disabled by default; the switch appears beside the time option. |
| Custom text | The editor appears in custom-text mode. Drafts are remembered when switching modes; tap **Save text** to apply edits. |
| Looping text | Disabled by default. Enable continuous scrolling for both short and long text; otherwise text is centered and overflow is ellipsized. Scrolling pauses while the workspace is hidden. |
| Font | Search, preview, and select fonts installed on the device, or choose a generic font family. System default follows the device's font setting. |
| Text size and weight | **10–28 sp**, default **16 sp**, with optional bold styling and an input preview. |
| Frost strength | **0–100**, default **50**. Release the slider to save and apply the value to the control area and slot backgrounds. |
| Launcher icon | Choose default, spring, summer, autumn, winter, or dark artwork, or switch automatically with the season. System dark mode or power-saving mode temporarily uses the dark icon. Icon changes preserve its launcher position. |

#### Settings, languages, and updates

- **Settings / Advanced / About:** use bottom navigation to switch between workspace settings, runtime diagnostics and external-control commands, and project information. The settings interface follows the system's light or dark theme and uses a liquid-glass bottom navigation bar.
- **Advanced page groups:** separate **Runtime and diagnostics** from **Shell commands**, with energy monitoring, command prerequisites, copy buttons, and setup instructions in their respective sections.
- **Languages:** follow the system or select **Simplified Chinese, Traditional Chinese, English, Japanese, or Korean** for the app and workspace.
- **Settings shortcut:** tap the control area's gear button to open NeXtep settings while keeping workspace mode active.
- **About:** view the installed version, check for updates, open release and source pages, and read license information and acknowledgements.
- **Update download:** view available release notes and open the APK download in a browser. Downloaded updates are installed manually.

### Requirements

- **OnePlus PLK110**: previously verified on **Android 16 / API 36, ColorOS 16**; recent partial device testing uses **Android 17 / API 37, ColorOS 17**. The APK minimum is API 35, which does not imply compatibility with every device on that API level.
- A matching **ColorOS 16 / 17** build on an adapted device.
- **KernelSU** or another compatible root solution.
- **Zygisk and LSPosed** with modern libxposed API support.
- Enable the module for all applicable packages in the bundled [scope list](https://github.com/lujinxin/NeXtep/blob/main/app/src/main/resources/META-INF/xposed/scope.list), including SystemUI, system framework, launcher, app-clone service, and assistant panel.

This module modifies **SystemUI, Launcher, and system-server behavior**. **Keep a working recovery path**, and disable the module if the device enters a boot loop or core UI becomes unstable.

Testing has not covered every app or edge case. Other devices and ROMs require separate adaptation; untested configurations have no compatibility guarantee.

### Installation

1. Download the APK from [GitHub Releases](https://github.com/Xposed-Modules-Repo/io.github.lujinxin.nextep/releases), or build it using [docs/BUILDING.md](https://github.com/lujinxin/NeXtep/blob/main/docs/BUILDING.md).
2. Install it on the target device.
3. Enable NeXtep in LSPosed for all applicable packages in the bundled scope list.
4. Reboot the device.
5. Open NeXtep's **Settings** page to configure the workspace and add its Control Center tile.

### Open and close the workspace

After enabling the module and rebooting, unlock the device. Use any of these entry points:

- **Status-bar gesture:** swipe horizontally to the left from the top-right status-bar area. Swiping down still opens the system notification shade or Control Center. The gesture is enabled by default and can be disabled independently.
- **Four-finger gesture:** pinch to enter and spread to exit. The independent switch, game exclusion, and app blacklist are on the **Settings** page.
- **Control Center tile:** in NeXtep's Settings, tap **Add** in the **Control Center entry** row and confirm. Pull down Control Center and tap **NeXtep** to toggle the workspace. If adding it from the app fails, use Control Center's edit screen.
- **External commands:** copy commands from the **Advanced** page into a gesture, shortcut, automation, or terminal tool; see below.
- **Exit button:** tap the exit button in the workspace control area to return to fullscreen.

#### External commands

The **Advanced** page provides copy buttons for entering, exiting, and querying workspace mode. The module must be enabled and the device rebooted; run entry and exit commands with **Root privileges while the phone is unlocked**.

Enter the workspace:

```sh
am broadcast -n io.github.lujinxin.nextep/.trigger.WorkspaceControlBrokerReceiver -a io.github.lujinxin.nextep.action.HOST_SET_REQUEST --ez io.github.lujinxin.nextep.extra.REQUESTED_ACTIVE true
```

Exit the workspace:

```sh
am broadcast -n io.github.lujinxin.nextep/.trigger.WorkspaceControlBrokerReceiver -a io.github.lujinxin.nextep.action.HOST_SET_REQUEST --ez io.github.lujinxin.nextep.extra.REQUESTED_ACTIVE false
```

Query the current state:

```sh
settings get global nextep_workspace_active_v1
```

The state is `1` while the workspace layout is active and `0` when inactive. Lock-screen suspension also publishes an inactive state; query after unlocking when using it in an automation.

### Behavior switches

These switches are on the **Settings** page; appearance and app ordering are described in the feature sections above.

| Setting | Default | Behavior |
|---------|---------|----------|
| Status-bar gesture | On | Enable or disable the top-right horizontal gesture. The Control Center tile remains available. |
| Four-finger gesture | On | Pinch four fingers together to enter and spread them apart to exit. |
| Block gestures in games | On | Suspend four-finger gestures when a recognized game is in the foreground or a slot. App blacklist exclusions can be configured separately. |
| Swipe slot apps to the background | On | Enable or disable outward swipe dismissal. Dragging a slot to the control area remains available. |
| Park the previous main app when switching | Off | Move the previous main app into an empty slot when switching from the app strip; switch normally if none is available. |
| Navigation-button adaptation | Off | Enable for three-button navigation and disable for gesture navigation. Toggle again after changing the system navigation mode. |

### Architecture

The diagram shows how the regular APK coordinates with the LSPosed-injected SystemUI, stock launcher, assistant panel, app-clone service, and system_server. It separates main-window presentation from the three live slots and shows configuration reads, change notifications, and shared runtime state. Compatibility hooks are guarded individually and skip unavailable targets.

[Architecture details](https://github.com/lujinxin/NeXtep/blob/main/docs/ARCHITECTURE.md) · [Interactive diagram (download HTML to view)](https://github.com/lujinxin/NeXtep/blob/main/docs/architecture/nextep-architecture.html) · [Diagram source](https://github.com/lujinxin/NeXtep/blob/main/docs/architecture/nextep-architecture.json)

<p align="center">
  <a href="https://github.com/lujinxin/NeXtep/blob/main/assets/nextep-architecture.png">
    <img src="https://raw.githubusercontent.com/lujinxin/NeXtep/main/assets/nextep-architecture.png" alt="NeXtep architecture diagram" width="100%">
  </a>
</p>

### Feedback group

QQ group: **1128561895**

<p align="center">
  <img src="https://raw.githubusercontent.com/lujinxin/NeXtep/main/assets/qq-group-qrcode.jpg" alt="NeXtep QQ feedback group QR code" width="360">
</p>

### Acknowledgements

Special thanks to **Smartisan OS OneStep** for the product concept and interaction inspiration behind this project.

### License and attribution

NeXtep is licensed under the [Apache License 2.0](https://github.com/lujinxin/NeXtep/blob/main/LICENSE). See [THIRD_PARTY_NOTICES.md](https://github.com/lujinxin/NeXtep/blob/main/THIRD_PARTY_NOTICES.md) for third-party attribution and design provenance.

Copyright 2026 lujinxin.

---

## 中文

**NeXtep** 是一个 **LSPosed 模块**。它在保留 **ColorOS 16 / 17 原生桌面**的同时，为系统加入**原生侧边工作区**，提供**一个主窗口和三个实时小窗**，并将任务切换、拖动操作、媒体控制和自定义应用快捷方式集成到 SystemUI 中。

本项目主要适配**一加 PLK110**，此前已在 **Android 16 / ColorOS 16** 上验证，近期功能与兼容性验证基于 **Android 17 / ColorOS 17**。项目依赖 Android 和 ColorOS 的私有行为，因此**其他设备、系统版本和厂商桌面需要经过适配**。

**正式分支：2.1.0。** 测试版源码位于 [beta](https://github.com/lujinxin/NeXtep/tree/beta)，已发布的 APK 可从 GitHub Releases 获取。

[下载与更新记录](https://github.com/Xposed-Modules-Repo/io.github.lujinxin.nextep/releases) · [哔哩哔哩演示视频](https://www.bilibili.com/video/BV1iKHj6fEtL)

[功能](#功能) · [能耗监测](#能耗监测与运行开销) · [使用要求](#使用要求) · [安装](#安装) · [工作区入口](#打开与关闭工作区) · [外部命令](#外部调用命令) · [行为开关](#行为开关)

### 功能

#### 工作区与布局

- **保留原生桌面**：不将 NeXtep 注册为替代的主屏幕应用，并对桌面快捷菜单、桌面搜索和负一屏进行适配。
- **一个主窗口、三个实时小窗**：同时展示多个应用任务，可在主窗口与小窗之间移动整个任务。
- **左右侧布局**：通过控制区的布局按钮，将小窗侧栏切换到屏幕左侧或右侧。
- **竖屏与双向横屏**：控制区和三个小窗保持相对机身的原有布局，主窗口应用随系统方向旋转；控制区内的视频画面可独立跟随屏幕方向，无需移动控制区或重建小窗布局。
- **虚拟按键适配**：可根据系统导航栏边界调整主窗与小窗布局。三键导航时开启，手势导航时关闭；更改系统导航方式后，重新开关一次此选项。
- **任务保留与恢复**：关闭并重新打开工作区时，可恢复仍保留在系统中的符合条件的小窗任务；锁屏时暂停小窗输出，解锁后恢复工作区及原有任务。
- **系统交互适配**：支持与系统原生悬浮窗共存，原生悬浮窗位于工作区面板上方；同时适配输入法焦点、通知栏、控制中心、亮度控件和视频窗口尺寸。

#### 任务管理

| 操作 | 使用方法 |
|------|----------|
| 将主窗口应用加入小窗 | 主窗口为普通应用时，点击空小窗的 **＋**。 |
| 从多任务页添加 | 将目标后台卡片移到屏幕中间，点击空小窗的 **＋**。添加后保持多任务页打开，可连续添加；分屏组合卡片需先退出分屏。 |
| 主窗口与小窗交换 | 点击已有应用的小窗，或长按小窗后拖到主窗口。 |
| 小窗之间移动或交换 | 长按已有应用的小窗，拖到空小窗时移动，拖到已占用小窗时交换；拖动时高亮目标区域。 |
| 在主窗口打开应用 | 点击顶部 App 栏中的应用图标。 |
| 从 App 栏加入小窗 | 长按应用图标，拖到目标小窗后松手。 |
| 横滑移到后台 | 在小窗上直接向屏幕外侧滑动：左侧小窗向左滑，右侧小窗向右滑，无需长按；可在设置中关闭。 |
| 拖动移到后台 | 长按小窗并拖到控制区，看到**“松手移到后台”**后释放；关闭横滑退后台后仍可使用。 |

移到后台会释放小窗位置，同时保留应用任务，当前主窗口保持原样。从桌面再次打开已在小窗中的应用时，会与主窗口交换。

可选的**“顶栏切换时缩小原应用”**功能，会在点击顶部 App 栏切换应用时，将原主窗口应用放入空小窗；没有空位时正常切换。此功能默认关闭。

#### App 栏与系统分身

- **自动排序**：按最近使用情况排列应用快捷方式，默认使用此模式。
- **手动排序**：最多选择 **36 个应用**，支持移除快捷方式，并长按已选项目拖动调整顺序。
- **系统分身应用**：分身应用可出现在 App 栏和手动选择列表中，通过分身标记与原应用区分。

#### 手势与应用排除

- **四指手势**：四指捏合进入工作区，四指张开退出；默认开启，可独立于状态栏手势开关。
- **游戏屏蔽**：默认开启，系统识别的游戏处于前台或任一小窗中时，暂停四指手势。
- **应用黑名单**：通过应用图标和名称选择，右侧勾选；所选应用或其系统分身处于前台或小窗中时，暂停四指手势。黑名单默认为空。

这些排除设置仅影响四指手势，其他工作区入口仍可使用。

#### 媒体控制

- 从系统媒体会话中显示歌曲封面、标题和歌手信息，提供**上一首、播放/暂停、下一首**按钮，具体可用操作取决于播放应用。
- 点击封面、标题等非播放按钮区域，在主窗口打开播放应用；如果播放应用已在小窗中，则与主窗口交换。
- 有可用封面时，自动生成柔和的封面取色渐变，暂停时保留配色；没有媒体会话或可用封面时，回退到壁纸磨砂背景。

#### 控制区视频

控制区包含**“功能”**和**“视频”**两页，可自动识别并接入支持的悬浮视频小窗，播放仍由来源应用负责。接入来源包括系统画中画（PiP）和符合条件的应用自带视频悬浮窗；厂商自由小窗和安全/受保护视频不属于通用支持范围。

1. 先在来源应用中播放视频，并开启系统画中画或应用自己的悬浮小窗。
2. 打开工作区，支持的悬浮小窗会自动接入**“视频”**页。
3. 在控制区左右滑动，切换**“功能”**页与**“视频”**页。如果小窗仍在外部，可点击功能页的视频快捷按钮，或在视频页点击**“在此显示视频”**。

轻点已接入的视频可显示紧凑的玻璃控制按钮，短暂延迟后自动隐藏。

| 控件 | 行为 |
|------|------|
| 播放/暂停 | 使用来源应用的媒体会话或可用的原生播放控件，是否可用取决于播放器。 |
| 完整显示/铺满 | 默认等比缩放，在两个方向上居中显示完整画面；手动选择铺满时裁切边缘以覆盖播放区域。 |
| 返回原小窗 | 恢复原来的原生悬浮窗，功能页的返回快捷按钮提供相同操作。 |
| 关闭 | 在可用时，请求来源播放器自身执行关闭操作。 |

- **画面独立转向**：控制区保持原位，视频画面跟随系统当前屏幕方向。手机横拿后，控制区在视线上变成竖向区域，竖屏画面可利用这块区域；横屏画面保持正向，按需在上下留边，并遵守系统旋转锁定。
- **保持接入**：同一个有效的原生窗口在转屏时持续嵌入，不再先返回悬浮窗后重新捕获；转屏也会保留所选的完整显示/铺满模式。
- **磨砂留边**：画面外的空余区域继续使用面板壁纸和磨砂效果。来源播放器自身绘制的黑边仍属于原始画面，不会被自动识别和去除。

锁屏或退出工作区时，会归还原悬浮窗。手动返回的小窗在解锁后保持在外部，直到再次接入。

#### 能耗监测与运行开销

在**“高级 → 运行与诊断 → 能耗监测”**中查看实时读数，并可复制监测报告。

| 读数分组 | 包含信息 |
|----------|----------|
| 整机电池 | 电量、温度及温差、充放电状态、电压、电流、估算净功率、未插电采样的平均放电功率、系统热状态与省电模式。 |
| 小窗运行 | 工作区状态、保留的小窗显示数、小窗帧更新合计、模块任务查询与预览截图，以及 SystemUI 宿主整体 CPU 使用情况。 |

仅在页面可见且手机已解锁时，每 **5 秒**采样一次；离开页面或锁屏后停止。不支持的读数显示为 **—**。

电池读数反映整机情况，充电功率不等于整机功耗；CPU 读数包含共享 SystemUI 进程的全部工作，100% 表示占用一个 CPU 核心。这些读数不能单独计算 NeXtep 的耗电量。

工作区降低空闲时的任务轮询频率，合并待处理刷新，减少重复预览抓取。小窗虚拟显示独立请求 **60Hz**，主屏刷新率仍由系统设置决定；锁屏时暂停小窗输出与任务轮询，解锁后恢复保留的工作区。

#### 外观与文字

控制区和小窗背景使用壁纸，并对 ColorOS 动态壁纸进行适配。磨砂效果不影响应用内容的清晰度。

| 设置项 | 选项与行为 |
|--------|------------|
| 顶部内容 | NeXtep 图标、时间、日期＋星期、留空、自定义文本；默认显示图标，切换选项即时生效。 |
| 显示秒 | 默认关闭，开关位于时间选项右侧。 |
| 自定义文本 | 选择自定义文本时显示编辑框；切换模式会保留草稿，编辑后点击**“保存文本”**生效。 |
| 循环滚动文字 | 默认关闭；开启后短文本与长文本均循环滚动，关闭时居中显示，超长部分省略；工作区隐藏时暂停滚动。 |
| 字体 | 搜索、预览并选择本机已安装字体，也可使用通用字体；系统默认跟随手机的字体设置。 |
| 字号与粗体 | 字号范围 **10–28 sp**，默认 **16 sp**，支持粗体和输入预览。 |
| 磨砂强度 | 范围 **0–100**，默认 **50**；松开滑块后保存并应用到控制区和小窗背景。 |
| 桌面图标 | 可选择默认、春、夏、秋、冬、暗黑图案，或自动随季节切换；系统暗黑/省电模式下临时使用暗黑图标，更换时保留桌面上的图标位置。 |

#### 设置、语言与更新

- **设置/高级/关于**：通过底部导航切换工作区设置、运行诊断与外部调用命令、项目信息；设置界面跟随系统浅色/深色主题，底部导航提供液态玻璃效果。
- **高级页分组**：将**“运行与诊断”**和**“Shell 命令”**分开，分别提供能耗监测、命令使用前提、复制按钮及配置步骤。
- **语言选择**：应用与工作区可跟随系统，或手动选择**简体中文、繁体中文、英语、日语、韩语**。
- **设置快捷入口**：点击工作区控制区的齿轮按钮打开 NeXtep 设置，并保持小窗模式。
- **关于页面**：查看已安装版本、检查更新、打开发布页面和源码，以及查看开源协议与致谢名单。
- **更新下载**：查看可用版本的更新说明，通过浏览器下载 APK，下载后手动安装。

### 使用要求

- **一加 PLK110**：此前已在 **Android 16 / API 36、ColorOS 16** 上验证，近期部分真机验证使用 **Android 17 / API 37、ColorOS 17**。APK 最低安装版本为 API 35，不代表适配所有达到此 API 等级的设备。
- 与已适配设备相匹配的 **ColorOS 16 / 17** 系统版本。
- **KernelSU** 或其他兼容的 Root 方案。
- **Zygisk 和 LSPosed**，并支持新版 libxposed API。
- 在 LSPosed 中勾选内置[作用域列表](https://github.com/lujinxin/NeXtep/blob/main/app/src/main/resources/META-INF/xposed/scope.list)中适用于当前设备的全部项目，包括 SystemUI、系统框架、桌面、应用分身服务和负一屏。

本模块会修改 **SystemUI、桌面和 system server 的行为**。**请确保设备具备可用的恢复手段**；如果设备出现无法开机或核心界面不稳定等问题，请停用本模块。

真机验证尚未覆盖所有应用和边界场景，其他设备和 ROM 仍需单独适配，未经测试的环境不作兼容性保证。

### 安装

1. 从 [GitHub Releases](https://github.com/Xposed-Modules-Repo/io.github.lujinxin.nextep/releases) 下载 APK，或按照 [docs/BUILDING.md](https://github.com/lujinxin/NeXtep/blob/main/docs/BUILDING.md) 自行构建。
2. 将 APK 安装到目标设备。
3. 在 LSPosed 中为内置作用域列表中适用于当前设备的全部项目启用 NeXtep。
4. 重启设备。
5. 打开 NeXtep 的**“设置”**页，配置工作区并添加控制中心入口。

### 打开与关闭工作区

启用模块并重启设备后，在解锁状态下，可通过以下入口操作：

- **状态栏手势**：从屏幕右上角的状态栏区域水平向左滑动；向下滑动仍按系统原有方式打开通知栏或控制中心。此手势默认开启，可独立关闭。
- **四指手势**：捏合进入、张开退出；独立开关、游戏屏蔽与应用黑名单均可在**“设置”**页配置。
- **控制中心开关**：在 NeXtep 设置页的**“控制中心入口”**一行点击**“添加”**并确认，随后下拉控制中心，点击 **NeXtep** 开关切换工作区状态。应用内添加失败时，可在控制中心编辑页面手动添加。
- **外部命令**：在**“高级”**页复制命令，配置到手势、快捷操作、自动化或终端工具中，具体见下文。
- **退出按钮**：点击工作区控制区的退出按钮，返回全屏模式。

#### 外部调用命令

**“高级”**页提供进入、退出小窗模式及查询状态的命令和复制按钮。请先启用模块并重启设备；进入和退出命令需在**手机解锁后，以 Root 权限执行**。

进入小窗模式：

```sh
am broadcast -n io.github.lujinxin.nextep/.trigger.WorkspaceControlBrokerReceiver -a io.github.lujinxin.nextep.action.HOST_SET_REQUEST --ez io.github.lujinxin.nextep.extra.REQUESTED_ACTIVE true
```

退出小窗模式：

```sh
am broadcast -n io.github.lujinxin.nextep/.trigger.WorkspaceControlBrokerReceiver -a io.github.lujinxin.nextep.action.HOST_SET_REQUEST --ez io.github.lujinxin.nextep.extra.REQUESTED_ACTIVE false
```

查询当前状态：

```sh
settings get global nextep_workspace_active_v1
```

工作区布局处于开启状态时返回 `1`，未开启时返回 `0`。锁屏挂起期间也会记录为未开启，自动化场景请在解锁后查询。

### 行为开关

以下开关均位于**“设置”**页，外观和 App 排列选项见上方功能说明。

| 设置项 | 默认值 | 行为 |
|--------|--------|------|
| 状态栏触发手势 | 开启 | 控制右上角水平滑动手势；关闭后仍可使用控制中心开关。 |
| 四指手势 | 开启 | 四指捏合进入，四指张开退出。 |
| 游戏中屏蔽手势 | 开启 | 系统识别的游戏处于前台或小窗时暂停四指手势，应用黑名单可单独配置。 |
| 小窗 App 横滑退到后台 | 开启 | 控制向外侧滑动移入后台；关闭后仍可拖到控制区移入后台。 |
| 顶栏切换时缩小原应用 | 关闭 | 从顶栏切换应用时，将原主窗口应用移入空小窗；没有空位时正常切换。 |
| 虚拟按键适配 | 关闭 | 三键导航时开启，手势导航时关闭；更改系统导航方式后，重新开关一次。 |

### 项目架构

下图展示普通 APK 与经 LSPosed 接入的 SystemUI、原生桌面、负一屏、应用分身和 system_server 之间的协作。图中区分主窗口呈现与三个实时小窗，并标注配置读取、变更通知及共享状态链路。兼容性 Hook 分别进行保护，在目标不可用时跳过对应处理。

[架构说明](https://github.com/lujinxin/NeXtep/blob/main/docs/ARCHITECTURE.md) · [交互式架构图（下载 HTML 后打开）](https://github.com/lujinxin/NeXtep/blob/main/docs/architecture/nextep-architecture.html) · [图源 JSON](https://github.com/lujinxin/NeXtep/blob/main/docs/architecture/nextep-architecture.json)

<p align="center">
  <a href="https://github.com/lujinxin/NeXtep/blob/main/assets/nextep-architecture.png">
    <img src="https://raw.githubusercontent.com/lujinxin/NeXtep/main/assets/nextep-architecture.png" alt="NeXtep 项目架构图" width="100%">
  </a>
</p>

### 反馈交流群

QQ 群：**1128561895**

<p align="center">
  <img src="https://raw.githubusercontent.com/lujinxin/NeXtep/main/assets/qq-group-qrcode.jpg" alt="NeXtep QQ 反馈群二维码" width="360">
</p>

### 致谢

特别感谢锤子科技 **Smartisan OS OneStep**，为本项目提供了产品理念与交互设计灵感。

### 许可证与署名

NeXtep 使用 [Apache License 2.0](https://github.com/lujinxin/NeXtep/blob/main/LICENSE) 授权。第三方署名和设计来源请参阅 [THIRD_PARTY_NOTICES.md](https://github.com/lujinxin/NeXtep/blob/main/THIRD_PARTY_NOTICES.md)。

Copyright 2026 lujinxin.
