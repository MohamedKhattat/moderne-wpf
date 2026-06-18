# Modern WPF UI

> Modern Fluent-style themes and controls for WPF applications.

![C#](https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=c-sharp&logoColor=white)
![.NET](https://img.shields.io/badge/.NET-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)
![WPF](https://img.shields.io/badge/WPF-0C54C2?style=for-the-badge&logo=windows&logoColor=white)
![XAML](https://img.shields.io/badge/XAML-0C54C2?style=for-the-badge&logo=xaml&logoColor=white)
![MahApps.Metro](https://img.shields.io/badge/MahApps.Metro-2D7D9A?style=for-the-badge&logo=windows&logoColor=white)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

## Overview

**Modern WPF UI** is a UI library that brings Fluent / Windows-UI styling to classic
WPF applications. It restyles the majority of the stock WPF controls and adds a set of
modern controls ported from the [Windows UI Library (WinUI)](https://github.com/microsoft/microsoft-ui-xaml),
so an existing WPF app can adopt a contemporary look with light, dark, and high-contrast
themes — without rewriting the app.

This repository contains the full source of the library, a companion MahApps.Metro
integration package, an interactive **Sample App** that demonstrates every control, plus
a set of standalone samples and a unit-test project.

> This is a fork/local copy of the open-source **ModernWpf** project
> (originally by Yimeng Wu, MIT-licensed). It is provided here as a working
> reference and study build of a modern WPF UI toolkit.

## Features

- **Restyled stock controls** — modern styles applied to the majority of built-in WPF
  controls (`Button`, `TextBox`, `ComboBox`, `CheckBox`, `Slider`, `Calendar`,
  `DatePicker`, `DataGrid`, `TreeView`, `TabControl`, `Menu`, `GroupBox`, `Expander`,
  `ListBox`, `ListView`, and more).
- **Light, dark, and high-contrast themes** — easily customizable accent colors and
  color palettes (`ThemeResources`, `ColorPaletteResources`).
- **Modern window styling** — borderless / custom title bar via `WindowHelper`.
- **Additional WinUI-ported controls**, including:
  - `NavigationView`, `SplitView`, `CommandBar`, `CommandBarFlyout`
  - `AutoSuggestBox`, `NumberBox`, `RatingControl`, `ToggleSwitch`
  - `PersonPicture`, `ProgressRing`, `SplitButton`, `DropDownButton`, `HyperlinkButton`
  - `ItemsRepeater` (with stack / flow / uniform-grid layouts), `RadioButtons`,
    `RadioMenuItem`, `ContentDialog`, `Flyout`, `MenuFlyout`, `SimpleStackPanel`
- **MahApps.Metro integration** — `ModernWpfUI.MahApps` provides styles to blend
  Modern WPF with MahApps.Metro windows.
- **Page transitions** and compact-sizing density support.

### Sample App

The included `ModernWpf.SampleApp` is a browsable gallery with a dedicated page for each
control (Buttons, ComboBox, DataGrid, NavigationView, NumberBox, ContentDialog, Calendar,
ItemsRepeater, ListView, the control palette / theming, and many more), letting you preview
behavior across light and dark themes.

## Tech Stack

| Area | Details |
| --- | --- |
| Language | C# (LangVersion 10.0) |
| UI Framework | WPF (`Microsoft.NET.Sdk.WindowsDesktop`, `UseWPF`) |
| Markup | XAML |
| Core library | `ModernWpf` — targets `net45`, `net462`, `netcoreapp3.0`, `net5.0-windows` |
| Controls library | `ModernWpf.Controls` — WinUI-ported additional controls |
| MahApps integration | `ModernWpf.MahApps` — depends on **MahApps.Metro 2.4.9** |
| Interop | CsWinRT / Windows SDK contracts for `Windows.UI` APIs |
| Tests | `ModernWpf.Test` (unit tests) + `ModernWpfTestApp` |

The library targets a broad range of runtimes — .NET Framework 4.5+, .NET Core 3.x,
and .NET 5/6+ — and runs on Windows Vista SP2 and above.

## Getting Started

### Prerequisites

- Windows
- [.NET SDK](https://dotnet.microsoft.com/download) (a version covering the target
  frameworks above) and/or Visual Studio 2019+ with the **.NET desktop development**
  workload.

### Build & run the Sample App

```bash
# From the repository root
dotnet build ModernWpf.sln

# Run the interactive control gallery
dotnet run --project ModernWpf.SampleApp
```

Or open `ModernWpf.sln` in Visual Studio, set **ModernWpf.SampleApp** as the startup
project, and press F5.

### Use it in your own app

Merge the library's resource dictionaries into `App.xaml`:

```xaml
<Application
    ...
    xmlns:ui="http://schemas.modernwpf.com/2019">
    <Application.Resources>
        <ResourceDictionary>
            <ResourceDictionary.MergedDictionaries>
                <ui:ThemeResources />
                <ui:XamlControlsResources />
            </ResourceDictionary.MergedDictionaries>
        </ResourceDictionary>
    </Application.Resources>
</Application>
```

Then enable the modern window style and start using the controls:

```xaml
<Window
    ...
    xmlns:ui="http://schemas.modernwpf.com/2019"
    ui:WindowHelper.UseModernWindowStyle="True">
    <ui:SimpleStackPanel Margin="12" Spacing="24">
        <TextBlock Text="My first Modern WPF app" Style="{StaticResource HeaderTextBlockStyle}" />
        <Button Content="I am a button" />
        <Button Content="I am an accent button" Style="{StaticResource AccentButtonStyle}" />
    </ui:SimpleStackPanel>
</Window>
```

## Notes

- **License:** MIT (see [`LICENSE`](LICENSE)). Copyright © 2019 Yimeng Wu.
- **Version in source:** `0.9.7-preview.2` (from `Directory.Build.props`).
- Screenshots of the controls live under [`docs/images/`](docs/images).
- Additional standalone integration samples (Dragablz, Fluent.Ribbon, FluentWPF,
  MahApps, multi-threading, PowerShell) are under [`samples/`](samples).
- This is a desktop UI library, **Windows-only** by nature of WPF.

---
<p align="center">Built by <b>Mohamed Habib Khattat</b> — <a href="https://github.com/MohamedKhattat">GitHub</a> · <a href="https://www.linkedin.com/in/mohamed-habib-khattat-2b206a173">LinkedIn</a></p>
