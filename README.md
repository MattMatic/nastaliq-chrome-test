# Nastaliq Test on Chrome

This repo was created to simplify testing of Noto Nastaliq Urdu on Chrome.

_Fonts have been downloaded from Google Fonts and renamed appropriately._

## Background

Specifically, it seems that some Chrome versions running on Android will freeze when Noto Nastaliq Urdu v3.007 enters the rendering pipeline.

If a font is dynamically loaded into the document, but not invoked (i.e. no text), this is fine.
But as soon as the text needs to be rendered, Android can freeze for minutes or indefinitely.

So far, Chrome on Windows and macOS work perfectly.

You may need to install Chrome Beta from the Google Play store to create the freeze.

## Usage
- Access the live page: https://mattmatic.github.io/nastaliq-chrome-test/index.html
- Try "Noto Nastaliq v4.000" should work
- Try "Gulzar 1.002" should work
- Try "TitanOne" should work
    - This is interesting, because various platforms behave differently. Windows will render Naskh text by default, but will fallback to one of the previously loaded Nastaliq fonts (so it's holding onto the fonts that were loaded!)
    - macOS does render with Nastaliq by default
    - Note that the Nastaliq text positioning will change fractionally once TitanOne is loaded - even when it's using a fallback Nastaliq font. (This implies there's some metrics being taken from TitanOne... maybe?!)
- The "Clear Fonts" button will empty the loaded fonts so you can try the TitanOne etc.

When Chrome/Android freezes, you cannot refresh the page, nor click any button.
Your only action will be to close the tab.

**WARNING**: If you're running this test on a phone, it may get very hot as it appears the CPU is being thrashed!!

## Various Results
- Phone
	- Android v13 build 00WW_3_530_SP15
	- FREEZE: Chrome 132.0.6834.165 (standard Chrome that was installed)
- BlueStacks on macOS
	- Android 13
	- OK: Chrome - 103.0.5060.71
	- FREEZE: Chrome Beta - 134.0.6998.4
- BlueStacks on Windows
	- Android 9; SM-S908E Build/TP1A.220624.014
	- OK: Chrome 129.0.6668.70
	- FREEZE: Chrome Beta 134.0.6998.4
- Chromebook
	- Chrome Dev version 134.0.6986.0 (from Google Play, Android app)
	- OK: Chrome 132.0.6834.190(Official Build) (64bit)
	- FREEZE: Google ChromeOS version 132.0.6834.190 (official build 64bit)
- Ubuntu Desktop 24.10 (under VirtualBox)
	- FREEZE: **Chromium** 133.0.6943.35 (Official Build) snap (64-bit)
	- FREEZE: **Chromium** 133.0.6943.53 (Official Build) snap (64-bit) - release candidate
	- DELAY: Firefox - v3.007 is a few hundred milliseconds slower at loading.

