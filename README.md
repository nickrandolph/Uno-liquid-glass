# Liquid Glass for Uno Platform

![Liquid Glass gallery sample page showing the macOS sidebar, glass cards, and button styles](docs/light_buttons.png)

A reusable **Liquid Glass** theme for Uno Platform, based on Apple's
[Liquid Glass design language](https://developer.apple.com/documentation/technologyoverviews/adopting-liquid-glass).
It follows the same resource-dictionary pattern as
[Uno.Themes](https://github.com/unoplatform/Uno.Themes), and includes a gallery that
demonstrates the complete control set in light and dark appearances.

## Supported operating systems and target frameworks

This project currently supports **macOS and iPadOS only**.

| Operating system | Gallery target framework | How it is used |
| --- | --- | --- |
| macOS | `net10.0-desktop` | Skia desktop gallery with real backdrop blur from Uno's `AcrylicBrush` rendering. |
| iPadOS | `net10.0-ios` | iPad app and simulator build; the simulator command uses `iossimulator-arm64`. |
| Build and tests only | `net10.0` | Shared .NET compilation and NUnit tests. This is not a separately supported operating-system target. |

The projects use **Uno Platform 6.5.36**, the **.NET 10** TFMs above, and the
`SkiaRenderer` Uno feature. Windows, Linux, Android, and browser/WebAssembly targets
are not part of the current supported or validated system.

| Package / project | Purpose |
| --- | --- |
| `LiquidGlass.Uno` | Reusable Liquid Glass styles for WinUI and Uno controls. |
| `LiquidGlass.CommunityToolkit` | Liquid Glass resources for the Windows Community Toolkit controls used by the gallery. |
| `DevWinUI.LiquidGlass` | Liquid Glass implementations of the DevWinUI-inspired controls used by the gallery. |
| `LiquidGlassGallery` | Sample application for macOS and iPadOS. |
| `LiquidGlassGallery.Tests` | NUnit tests for the theme dictionaries, styles, and design invariants. |

## What the theme changes

The theme supplies matching light and dark resource dictionaries and applies the
styles implicitly, so standard controls change without setting a style on every
instance. The design system uses:

- translucent `AcrylicBrush` materials with renderer-safe fallback colors
- specular top highlights and gradient rim lighting on glass surfaces
- rounded, concentric geometry and 44-point minimum touch targets
- capsule controls and Apple system colors for primary, selected, success, and destructive states
- monochrome glass for normal actions, reserving color for selection and primary actions
- hover, pressed, focused, selected, disabled, light, and dark visual states

### Uno and WinUI controls

| Controls | Liquid Glass treatment |
| --- | --- |
| `Button`, `ToggleButton`, `RepeatButton`, `HyperlinkButton` | Rebuilt as 44-point glass capsules with rim light, hover/press states, and separate prominent and destructive variants. The framework `AccentButtonStyle` maps to the prominent glass button. |
| `TextBox`, `PasswordBox` | Fully retemplated as rounded translucent fields with glass fill, subtle border, placeholder treatment, selection colors, and a tinted focus state. |
| `AutoSuggestBox` | Rebuilt with the glass text field, preserved query button, and a glass suggestions surface. |
| `NumberBox` | Uses the glass input field with integrated capsule spin buttons and a matching popup surface. |
| `CheckBox`, `RadioButton` | Restyled with Apple-like indicators, tint-colored checked states, and theme-aware hover, pressed, and disabled states. |
| `ToggleSwitch` | Rebuilt as a 51-by-31 Apple-style switch with a white thumb and system-green on state. |
| `Slider` | Uses a translucent system-gray track, Apple-tint value track, and round white glass thumb. |
| `ComboBox`, `ComboBoxItem` | Rounded glass field plus a glass dropdown; items receive tint selection and readable hover/selected states. |
| `ListViewItem`, `ListBoxItem` | Rounded selection rows with translucent hover feedback and an Apple-tint selected state. |
| `ProgressBar` | Recolored to a quiet glass track with an Apple-tint progress indicator. |
| `RatingControl` | Applies the Apple tint and theme-aware neutral/disabled rating colors. |
| `DatePicker`, `TimePicker` | Fully retemplated as segmented glass fields while preserving WinUI template-part names and culture-based field ordering. |
| `DatePickerFlyoutPresenter`, `TimePickerFlyoutPresenter` | Rebuilt as heavier glass picker-wheel popups with an iOS-style rounded selection band and glass command buttons. |
| `CalendarDatePicker` | Uses the rounded glass input surface, tint focus treatment, and theme-aware calendar chrome. |
| `DropDownButton`, `SplitButton`, `ToggleSplitButton` | Capsule command surfaces with glass separators, chevrons, primary/secondary regions, and checked-state tint. |
| `MenuBar`, `MenuBarItem` | Clear command chrome at rest with rounded glass hover/open states. |
| `MenuFlyoutPresenter`, `MenuFlyoutItem`, `MenuFlyoutSubItem`, `MenuFlyoutSeparator` | Heavier glass menu surface, macOS-style rows, tint hover/selection, readable selected text, submenu chevrons, and glass separators. |
| `CommandBar`, `CommandBarOverflowPresenter` | Glass command surface and overflow menu with matching rounded geometry and spacing. |
| `AppBarButton`, `AppBarToggleButton`, `AppBarSeparator` | Chromeless toolbar actions that gain rounded glass feedback; toggled actions use the tint and separators use the glass hairline. |
| `FlyoutPresenter` | Gives normal flyouts a rounded, elevated glass surface. |
| `ContentDialog` | Rebuilt as a rounded glass window with capsule command buttons; the default action is prominent glass. |
| `ToolTip` | Compact dark/light glass callout with rounded corners and readable label colors. |
| `InfoBar` | Glass notification surface with semantic accent, rounded rim, and matching close/action buttons. |
| `InfoBadge` | Capsule/circle badge geometry with Apple tint and high-contrast text. |
| `PersonPicture` | Glass-backed avatar treatment with tint-colored initials and presence/badge integration. |
| `TabViewItem` | Tabs become an Apple-style segmented control; the selected tab is a raised glass pill and the close button uses glass feedback. |
| `NavigationViewItem` | Sidebar rows lose the Fluent indicator bar and use a rounded frosted selection pill; hierarchical indentation and animated chevrons are preserved. |
| `NavigationView` pane | The `LiquidGlassNavigation.GlassPane` attached helper turns the pane into an inset floating acrylic sidebar with rim lighting and content extending beneath the blur. |
| `Expander` | Rounded glass header, rotating chevron, and clear-glass expanded content area. |
| `TreeViewItem` | Glass hover/selection rows with preserved depth indentation, expander behavior, and drag/drop states. |
| `BreadcrumbBarItem` | Rounded glass breadcrumb segments, tint interaction states, and matching overflow flyout. |
| `PipsPager` | Translucent inactive pips, a tint selected pip, and glass previous/next buttons. |
| `FlipView` | Keeps the content unobstructed and replaces navigation arrows with floating glass buttons. |
| `SplitView` | Uses clear content with a floating glass pane and glass-aware overlay treatment. |
| `Border` opt-in styles | `LiquidGlassCardBorderStyle` and `LiquidGlassSurfaceBorderStyle` provide reusable card and elevated-surface containers. |

### Windows Community Toolkit controls

| Controls | Liquid Glass treatment |
| --- | --- |
| `SettingsCard`, `SettingsExpander` | Stock templates are reskinned with acrylic card/header fills, gradient rims, rounded content, glass chevrons, and correct runtime light/dark switching. |
| `Segmented`, `SegmentedItem` | iOS-style translucent track and a raised selected glass pill; pivot and detached-button variants use Apple tint appropriately. |
| `TokenizingTextBox` | The entry field inherits the glass text treatment; tokens become translucent chips and selected tokens use Apple tint with white text. |
| `RangeSelector` | Matches the Liquid Glass slider with a gray outer track, tint range band, and two round white thumbs. |
| `ColorPicker` | Keeps the toolkit layout, gives channel sliders white round thumbs, and turns NumberBox popups into glass surfaces. |
| `GridSplitter`, `ContentSizer`, `PropertySizer`, `SizerBase` | Clear glass splitter track with a capsule separator grip and glass hover/pressed feedback. |
| `HeaderedContentControl`, `HeaderedItemsControl` | These layout-only toolkit controls expose no theme resources, so the gallery applies Liquid Glass typography to headers and places their content in glass tiles without replacing the stock templates. |
| `MetadataControl` | Supplies a safe template and secondary-label typography for metadata, separators, wrapping, and links. |
| `DataGrid` | Transparent cells on a glass card, hairline grid separators, quiet headers, translucent row hover, Apple-tint selection, and glass-aware text, combo, and autosuggest editors. |

### DevWinUI-inspired controls

| Controls | Liquid Glass treatment |
| --- | --- |
| `Card` | Acrylic card with specular rim, concentric corners, and hover/pressed overlays. |
| `Divider` | Theme-aware Apple separator with horizontal/vertical layout support and optional label content. |
| `SettingsCard`, `SettingsExpander`, `SettingsGroup` | Glass settings surfaces with clear nested rows, separators, rounded group geometry, and expandable content. |
| `PinBox` | Individual glass digit fields with Apple-tint focus borders and password/PIN behavior. |
| `KeyVisual`, `Shortcut` | Rounded glass keyboard keycaps with a subtle lower edge and compact shortcut layout. |
| `StepBar` | Tint-colored progress markers and connectors with clear current/completed step states. |
| `Timeline` | Glass-aware timeline content with tint markers and separator connectors. |
| `LoadingIndicator` | Animated Apple-tint ring that remains readable in light and dark appearances. |
| `Growl`, `GrowlItem` | Floating rounded glass notification cards with semantic icon/color treatment and a glass close action. |
| `MessageBox`, `GlassWindowHelper` | Glass dialog/window treatment with capsule actions and theme-aware hosting behavior. |
| `UniformGrid` | Responsive equal-cell layout used to present controls consistently in the sample gallery. |

## Using the theme in your own app

Reference the libraries you need and merge their theme dictionaries in `App.xaml`:

```xml
<Application.Resources>
  <ResourceDictionary>
    <ResourceDictionary.MergedDictionaries>
      <XamlControlsResources xmlns="using:Microsoft.UI.Xaml.Controls" />
      <LiquidGlassTheme xmlns="using:Uno.Themes.LiquidGlass" />
      <CommunityToolkitGlassTheme xmlns="using:CommunityToolkit.LiquidGlass" />
      <DevWinUIGlassTheme xmlns="using:DevWinUI.LiquidGlass" />
    </ResourceDictionary.MergedDictionaries>
  </ResourceDictionary>
</Application.Resources>
```

Standard controls pick up Liquid Glass implicitly. Opt-in variants use explicit styles:

```xml
<Button Content="Buy" Style="{StaticResource LiquidGlassProminentButtonStyle}" />
<Button Content="Delete" Style="{StaticResource LiquidGlassDestructiveButtonStyle}" />
<Border Style="{StaticResource LiquidGlassCardBorderStyle}">…</Border>
```

Rebrand without forking the theme:

```xml
<LiquidGlassTheme xmlns="using:Uno.Themes.LiquidGlass"
                  ColorOverrideSource="ms-appx:///MyApp/Styles/LiquidGlassColorsOverride.xaml" />
```

See [Uno.Themes.LiquidGlass/README.md](Uno.Themes.LiquidGlass/README.md) for the
design tokens, explicit style keys, and implementation details.

## NuGet packages

After a release has been published, install the core theme, then add either extension
package when the application uses those controls:

```bash
dotnet add package LiquidGlass.Uno
dotnet add package LiquidGlass.CommunityToolkit
dotnet add package DevWinUI.LiquidGlass
```

The Community Toolkit and DevWinUI packages declare `LiquidGlass.Uno` as a
dependency, so installing either extension also restores the core theme. Each package
contains assemblies for `net10.0`, `net10.0-desktop`, and `net10.0-ios`, a NuGet
README, MIT license metadata, repository/source metadata, and a portable-symbol
`.snupkg`.

### Publishing a release

The [NuGet packages workflow](.github/workflows/nuget.yml) builds and validates all
three packages on pull requests and pushes to `main`. A manual workflow run accepts a
NuGet version, uploads the exact `.nupkg` and `.snupkg` files as a reviewable GitHub
artifact, and then waits for approval before publishing those same files to NuGet.org.

One-time repository setup:

1. In GitHub, create an environment named `nuget.org`, add the required reviewer or
   reviewers, restrict deployment to `main`, and add an environment variable named
   `NUGET_USER` containing the NuGet.org profile name.
2. In NuGet.org **Trusted Publishing**, add a GitHub policy with repository owner
   `cconner100`, repository `Uno-liquid-glass`, workflow file `nuget.yml`, and
   environment `nuget.org`.
3. In GitHub Actions, run **NuGet packages**, enter the new version, review the
   generated package artifact, and approve the `nuget.org` deployment. The publish job
   obtains a short-lived NuGet credential through GitHub OIDC; no long-lived API key is
   stored in GitHub.

## Running the gallery

```bash
# macOS
dotnet run --project LiquidGlassGallery/LiquidGlassGallery.csproj -f net10.0-desktop

# iPad simulator (requires full Xcode installed and selected)
dotnet build LiquidGlassGallery/LiquidGlassGallery.csproj \
  -f net10.0-ios -t:Run -p:RuntimeIdentifier=iossimulator-arm64
```

The **Dark appearance** switch changes the whole gallery between the matching light
and dark glass palettes at runtime.

### Screenshot automation

The macOS gallery can walk every sample page in both appearances, save each bitmap,
and exit:

```bash
LG_SCREENSHOT_DIR=/tmp/lg-shots \
  dotnet run --project LiquidGlassGallery/LiquidGlassGallery.csproj -f net10.0-desktop
```

## Tests

```bash
dotnet test LiquidGlassGallery.Tests/LiquidGlassGallery.Tests.csproj
```

The tests parse the theme XAML and verify, among other things:

- light and dark dictionaries define identical key sets
- glass fills use translucent acrylic tints and translucent fallbacks
- specular highlights fade to fully transparent
- buttons keep the 44-point capsule geometry
- the palette matches Apple system colors
- every implicit control style is based on a public `LiquidGlass*` explicit style
