<div align="center">

# Simple-App

### Simple App is bringing complex web-style interfaces to native application development!
<br>

</div>

Leverage a UI that uses web technologies (html, css, javascript, ie static site generation) to drive native C++ applications without internet connection or external dependencies.

This is accomplished by filling the native UI Window with a Microsoft WebView2 component, and navigating the WebView to an embedded webserver.

Additionally, by injecting webui's javascript websocket server into the WebView, a new layer of local application interactions becomes available that cannot exist on a typical website.


<div align="center">

# Setup

</div>

## Development environment
* Install Microsoft Visual Studio (https://visualstudio.microsoft.com/downloads/)

## *Optional* Asset embedding environment
* Install msys2 (https://www.msys2.org/)
* Current installer: https://github.com/msys2/msys2-installer/releases/download/2024-05-07/msys2-x86_64-20240507.exe
* Launch ``msys2`` terminal
 >ie using the default path: ``C:\msys64\ucrt64.exe``
* In the msys2 terminal, run the following command to install binutils: 
 >pacman -S binutils
 * Exit the terminal
 
<div align="center">

# Build

</div>

## Building with embedded assets
* Clone this repository
 >git clone https://github.com/nater0000/simple-app.git
* Open the Visual Studio solution (scripts/simple-app.sln)
* Build the ``c-embed`` project
* Run ``c-embed.exe`` with your Interface directory as a parameter
 >c-embed.exe "C:\website"
* Open the ``Project Properties`` for ``simple-app``
* Navigate to ``C/C++``->``Preprocessor``
* Within ``Preprocessor Definitions`` update ``EMBEDDED_ROOT_DIR`` with your Interface directory
 >ie ``EMBEDDED_ROOT_DIR="C:\website"``

> [!CAUTION]
> The ``c-embed.exe`` parameter and ``EMBEDDED_ROOT_DIR`` are *case-sensitive* and *must* match
* Build the ``simple-app`` project
* Run ``simple-app.exe``
> [!NOTE]
> No need for external assets!!

## Optionally, building *without* embedded assets
* Clone this repository
 >git clone https://github.com/nater0000/simple-app.git
* Open the Visual Studio solution (scripts/simple-app.sln)
* Open the ``Project Properties`` for ``simple-app``
* Navigate to ``C/C++``->``Preprocessor``
* Within ``Preprocessor Definitions`` remove ``USE_CEMBED``
* Build the ``simple-app`` project
* Copy or move the simple-app.exe output file into your Interface directory (ie ``C:\website\``)
* Run ``simple-app.exe``
> [!WARNING]
> ``index.html`` must exist in the same directory as ``simple-app.exe``

<div align="center">

# Run

</div>

## Running simple-app
> [!WARNING]
> Make sure all ``.html`` files include ``webui.js`` for proper functionality
> <script src="webui.js"></script>
* If the assets have been embedded, ``simple-app.exe`` is portable and stand-alone
* If the assets are not embedded, a file named ``index.html`` must be in the same directory as ``simple-app.exe``

<div align="center">

# Additional Information

</div>

## Notes
This app is based on the Microsoft Visual Studio C++ template.

Updated to a flashy demo GUI by @JadeZaher (https://github.com/JadeZaher/NathanCDudeHelp)

Updated with webui C++ wrapper and a busy loop invoking a javascript function to interact with the site.

Updated with c-embed to package interface assets directly into the application

Using civetweb (via webui), we can run an entire website from a local directory (or more elaborate backend features with additional effort).

Updated with a Webview (https://github.com/webview/webview) front end component. This may get removed or replaced.

Updated with a Microsoft Webview2 (https://developer.microsoft.com/en-us/microsoft-edge/webview2) which is wrapped by Webview on Windows, but can also be used directly.

Updated with more web gui visuals

Verified with BeeNum and pure javascript Calculator

Verified with svelte project using adapter-static

Note that Webview2 dll is not required for redistributing on most Win10+ systems

Note that one expectation for this project is to make it work cross-platform via gcc+gtk


## TODO
- [ ] Modify c-embed to ignore the path prefix (ie "C:\my-files\")
- [ ] Fix window initialization code to be closer to the original template
- [ ] Refactor initialization into an interface
- [ ] Refactor Windows Resource into platform-specific feature
- [ ] Integrate with forked version of webui
- [ ] Integrate with forked version of c-embed
- [ ] [Feature] Add 'Press any key': C++ input handler
- [ ] [Feature] Add 'Press any key': next.html
- [ ] Refactor msys2-ucrt invocations to use a Preprocessor Definition
- [ ] Update README with instructions for non-default msys2 installation location
- [x] Update webui to use version 2.5-beta
- [x] Add pre-build steps to invoke c-embed
- [x] Integrate webui build into project
- [x] Fix current build issues due to external dependencies
- [x] Impl write index (+subdir) to appdata [bin2cpp] [using c-embed instead]
- [x] Compile index (+subdir) into binary [bin2cpp] [using c-embed instead]
- [x] Make a prettier gui
- [x] Push to git
- [x] Separate webserver API from window API
- [x] Integrate refactored webui [depends on webui fork+modify]
- [x] Integrate webview (chromium) [using MS Webview2 instead]
- [x] Modify webui build scripts
- [x] Refactor .sln,.vcproj into ./scripts/
- [x] Refactor ./src/website/* into ./website/*


### Possible ports
- [ ] Add gcc implementation
- [ ] Add Windows Resource feature usage into gcc implementation


### Possible additions
- [ ] Build civetweb with Duktape support
- [ ] Integrate local file IO
- [ ] Add gradle or cmake or similar
- [ ] Create a new project for MSI packaging


### Fork webui
- [ ] Raise PR with additional APIs
- [ ] Raise PR with msvc fixes
- [ ] Raise PR with c-embed support
- [ ] Raise PR with renamed 'window'
- [x] Refactor civetweb into ./vendor
- [x] Refactor .html and ./src/.html into ./website/
- [x] Refactor .sln,.vcproj into ./scripts/
- [x] Support Microsoft Visual Studio (MSVC)

### Fork civetweb
- [ ] Raise PR with msvc fixes
- [ ] Raise PR with c-embed support
- [x] Support Microsoft Visual Studio (MSVC)

### Forked c-embed
- [ ] Raise PR with msvc fixes
- [x] Support Microsoft Visual Studio (MSVC)


[![Stargazers repo roster for @nater0000/simple-app](https://reporoster.com/stars/nater0000/simple-app)](https://github.com/nater0000/simple-app/stargazers)
