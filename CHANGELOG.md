# JupyterLab Changelog

## [v0.33.0](https://github.com/jupyterlab/jupyterlab/releases/tag/v0.33.0)

#### July 26, 2018

See the [JupyterLab 0.33.0](https://github.com/jupyterlab/jupyterlab/milestone/12?closed=1) milestone on GitHub for the full list of pull requests and issues closed.

#### Key Features:

* [No longer in beta](#no-longer-in-beta)
* [Workspaces](#workspaces)
* [Menu items](#menu-items)
* [Keyboard shortcuts](#keyboard-shorcuts)
* [Command palette items](#command-palette-items)
* [Settings](#settings)
* [Larger file uploads](#larger-size-uploads)
* [Extension management and installation](#extension-manager)
* [Interface changes](#interface-changes)
* [Renderers](#renderers)
* [Changes for developers](#changes-for-developers)
* [Other fixes](#other-fixes)

#### No longer in beta

In JupyterLab 0.33, we removed the "Beta" label to better signal that JupyterLab is ready for users to use on a daily basis. The extension developer API is still being stabilized. See the release blog post for details. ([#4898](https://github.com/jupyterlab/jupyterlab/issues/4898), [#4920](https://github.com/jupyterlab/jupyterlab/pull/4920))

#### Workspaces

We added new workspace support, which enables you to have multiple saved layouts, including in different browser windows. See the [workspace documentation](https://jupyterlab.readthedocs.io/en/stable/user/urls.html) for more details. ([#4502](https://github.com/jupyterlab/jupyterlab/issues/4502), [#4708](https://github.com/jupyterlab/jupyterlab/pull/4708), [#4088](https://github.com/jupyterlab/jupyterlab/issues/4088), [#4041](https://github.com/jupyterlab/jupyterlab/pull/4041) [#3673](https://github.com/jupyterlab/jupyterlab/issues/3673), [#4780](https://github.com/jupyterlab/jupyterlab/pull/4780))

#### Menu items

* "Activate Previously Used Tab" added to the Tab menu (`Ctrl/Cmd Shift '`) to toggle between the previously active tabs in the main area. ([#4296](https://github.com/jupyterlab/jupyterlab/pull/4296))
* "Reload From Disk" added to the File menu to reload an open file from the state saved on disk. ([#4615](https://github.com/jupyterlab/jupyterlab/pull/4615))
* "Save Notebook with View State" added to the File menu to persist the notebook collapsed and scrolled cell state. We now read the `collapsed`, `scrolled`, `jupyter.source_hidden` and `jupyter.outputs_hidden` notebook cell metadata when opening. `collapsed` and `jupyter.outputs_hidden` are redundant and the initial collapsed state is the union of both of them. When the state is persisted, if an output is collapsed, both will be written with the value `true`, and if it is not, both will not be written. ([#3981](https://github.com/jupyterlab/jupyterlab/pull/3981))
* "Increase/Decrease Font Size" added to the text editor settings menu. ([#4811](https://github.com/jupyterlab/jupyterlab/pull/4811))
* "Show in File Browser" added to a document tab's context menu. ([#4500](https://github.com/jupyterlab/jupyterlab/pull/4500))
* "Open in New Browser Tab" added to the file browser context menu. ([#4315](https://github.com/jupyterlab/jupyterlab/pull/4315))
* "Copy Path" added to file browser context menu to copy the document's path to the clipboard. ([#4582](https://github.com/jupyterlab/jupyterlab/pull/4582))
* "Show Left Area" has been renamed to "Show Left Sidebar" for consistency (same for right sidebar). ([#3818](https://github.com/jupyterlab/jupyterlab/pull/3818))

#### Keyboard shortcuts

* "Save As..." given the keyboard shortcut `Ctrl/Cmd Shift S`. ([#4560](https://github.com/jupyterlab/jupyterlab/pull/4560))
* "Run All Cells" given the keyboard shortcut `Ctrl/Cmd Shift Enter`. ([#4558](https://github.com/jupyterlab/jupyterlab/pull/4558))
* "notebook:change-to-cell-heading-X" keyboard shortcuts (and commands) renamed to "notebook:change-cell-to-heading-X" for X=1...6. This fixes the notebook command-mode keyboard shortcuts for changing headings. ([#4430](https://github.com/jupyterlab/jupyterlab/pull/4430))
* The console execute shortcut can now be set to either `Enter` or `Shift Enter` as a Console setting. ([#4054](https://github.com/jupyterlab/jupyterlab/pull/4054))

#### Command palette items

* "Notebook" added to the command palette to open a new notebook. ([#4812](https://github.com/jupyterlab/jupyterlab/pull/4812))
* "Run Selected Text or Current Line in Console" added to the command palette to run the selected text or current line from a notebook in a console. A default keyboard shortcut for this command is not yet provided, but can be added by users with the `notebook:run-in-console` command. ([#3453](https://github.com/jupyterlab/jupyterlab/issues/3453), [#4206](https://github.com/jupyterlab/jupyterlab/issues/4206), [#4330](https://github.com/jupyterlab/jupyterlab/pull/4330))
* The command palette now renders labels, toggled state, and keyboard shortcuts in a more consistent and correct way. ([#4533](https://github.com/jupyterlab/jupyterlab/pull/4533), [#4510](https://github.com/jupyterlab/jupyterlab/pull/4510))

#### Settings

* "fontFamily", "fontSize", and "lineHeight" settings added to the text editor advanced settings. ([#4673](https://github.com/jupyterlab/jupyterlab/pull/4673))
* Solarized dark and light text editor themes from CodeMirror. ([#4445](https://github.com/jupyterlab/jupyterlab/pull/4445))

#### Larger file uploads

* Support for larger file uploads (>15MB) when using Jupyter notebook server version >= 5.1. ([#4224](https://github.com/jupyterlab/jupyterlab/pull/4224))

#### Extension management and installation

* New extension manager for installing JupyterLab extensions from npm within the JupyterLab UI. You can enable this from the Advanced Settings interface. ([#4682](https://github.com/jupyterlab/jupyterlab/pull/4682), [#4925](https://github.com/jupyterlab/jupyterlab/pull/4925))
* Please note that to install extensions in JupyterLab, you must use NodeJS version 9 or earlier (i.e., not NodeJS version 10). We will upgrade yarn, with NodeJS version 10 support, when a [bug in yarn](https://github.com/yarnpkg/yarn/issues/5935) is fixed. ([#4804](https://github.com/jupyterlab/jupyterlab/pull/4804))

#### Interface changes

* Wider tabs in the main working area to show longer filenames. ([#4801](https://github.com/jupyterlab/jupyterlab/pull/4801))
* Initial kernel selection for a notebook or console can no longer be canceled: the user must select a kernel. ([#4596](https://github.com/jupyterlab/jupyterlab/pull/4596))
* Consoles now do not display output from other clients by default. A new "Show All Kernel Activity" console context menu item has been added to show all activity from a kernel in the console. ([#4503](https://github.com/jupyterlab/jupyterlab/pull/4503))
* The favicon now shows the busy status of the kernels in JupyterLab. ([#4361](https://github.com/jupyterlab/jupyterlab/pull/4361), [#3957](https://github.com/jupyterlab/jupyterlab/issues/3957), [#4966](https://github.com/jupyterlab/jupyterlab/pull/4966))

#### Renderers

* JupyterLab now ships with a Vega4 renderer by default (upgraded from Vega3). ([#4806](https://github.com/jupyterlab/jupyterlab/pull/4806))
* The HTML sanitizer now allows some extra tags in rendered HTML, including `kbd`, `sup`, and `sub`. ([#4618](https://github.com/jupyterlab/jupyterlab/pull/4618))
* JupyterLab now recognizes the `.tsv` file extension as tab-separated files. ([#4684](https://github.com/jupyterlab/jupyterlab/pull/4684))
* Javascript execution in notebook cells has been re-enabled. ([#4515](https://github.com/jupyterlab/jupyterlab/pull/4682))

#### Changes for developers

* A new signal for observing application dirty status state changes. ([#4840](https://github.com/jupyterlab/jupyterlab/issues/4840))
* A new signal for observing notebook cell execution. ([#4740](https://github.com/jupyterlab/jupyterlab/issues/4740), [#4744](https://github.com/jupyterlab/jupyterlab/pull/4744))
* A new `anyMessage` signal for observing any message a kernel sends or receives. ([#4437](https://github.com/jupyterlab/jupyterlab/pull/4437))
* A generic way for different widgets to register a "Save with extras" command that appears in the File menu under save. ([#3981](https://github.com/jupyterlab/jupyterlab/pull/3981))
* A new API for removing groups from a JupyterLab menu. `addGroup` now returns an `IDisposable` which can be used to remove the group. `removeGroup` has been removed. ([#4890](https://github.com/jupyterlab/jupyterlab/pull/4890))
* The `Launcher` now uses commands from the application `CommandRegistry` to launch new activities. Extension authors that add items to the launcher will need to update them to use commands. ([#4757](https://github.com/jupyterlab/jupyterlab/pull/4757))
* There is now a top-level `addToBottomArea` function in the application, allowing extension authors to add bottom panel items like status bars. ([#4752](https://github.com/jupyterlab/jupyterlab/pull/4752))
* Rendermime extensions can now indicate that they are the default rendered widget factory for a file-type. For instance, the default widget for a markdown file is a text editor, but the default rendered widget is the markdown viewer. ([#4692](https://github.com/jupyterlab/jupyterlab/pull/4692))
* Add new workspace REST endpoints to `jupyterlab_launcher` and make them available in `@jupyterlab/services`. ([#4841](https://github.com/jupyterlab/jupyterlab/pull/4841))
* Documents created with a mimerenderer extension can now be accessed using an `IInstanceTracker` which tracks them. Include the token `IMimeDocumentTracker` in your plugin to access this. The `IInstanceTracker` interface has also gained convenience functions `find` and `filter` to simplify iterating over instances. ([#4762](https://github.com/jupyterlab/jupyterlab/pull/4762))
* RenderMime render errors are now displayed to the user. ([#4465](https://github.com/jupyterlab/jupyterlab/pull/4465))
* `getNotebookVersion` is added to the `PageConfig` object. ([#4224](https://github.com/jupyterlab/jupyterlab/pull/4224))
* The session `kernelChanged` signal now contains both the old kernel and the new kernel to make it easy to unregister things from the old kernel. ([#4834](https://github.com/jupyterlab/jupyterlab/pull/4834))
* The `connectTo` functions for connecting to kernels and sessions are now synchronous (returning a connection immediately rather than a promise). The DefaultSession `clone` and `update` methods are also synchronous now. ([#4725](https://github.com/jupyterlab/jupyterlab/pull/4725))
* Kernel message processing is now asynchronous, which guarantees the order of processing even if a handler is asynchronous. If a kernel message handler returns a promise, kernel message processing is paused until the promise resolves. The kernel's `anyMessage` signal is emitted synchronously when a message is received before asynchronous message handling, and the `iopubMessage` and `unhandledMessage` signals are emitted during asynchronous message handling. These changes mean that the comm `onMsg` and `onClose` handlers and the kernel future `onReply`, `onIOPub`, and `onStdin` handlers, as well as the comm target and message hook handlers, may be asynchronous and return promises. ([#4697](https://github.com/jupyterlab/jupyterlab/pull/4697))
* Kernel comm targets and message hooks now are unregistered with `removeCommTarget` and `removeMessageHook`, instead of using disposables. The corresponding `registerCommTarget` and `registerMessageHook` functions now return nothing. ([#4697](https://github.com/jupyterlab/jupyterlab/pull/4697))
* The kernel `connectToComm` function is synchronous, and now returns the comm rather than a promise to the comm. ([#4697](https://github.com/jupyterlab/jupyterlab/pull/4697))
* The `KernelFutureHandler` class `expectShell` constructor argument is renamed to `expectReply`. ([#4697](https://github.com/jupyterlab/jupyterlab/pull/4697))
* The kernel future `done` returned promise now resolves to undefined if there is no reply message. ([#4697](https://github.com/jupyterlab/jupyterlab/pull/4697))
* The `IDisplayDataMsg` is updated to have the optional `transient` key, and a new `IUpdateDisplayDataMsg` type was added for update display messages. ([#4697](https://github.com/jupyterlab/jupyterlab/pull/4697))
* The `uuid` function from `@jupyterlab/coreutils` is removed. Instead import `UUID` from `@phosphor/coreutils` and use `UUID.uuid4()` . ([#4604](https://github.com/jupyterlab/jupyterlab/pull/4604))
* Main area widgets like the launcher and console inherit from a common `MainAreaWidget` class which provides a content area (`.content`) and a toolbar (`.toolbar`), consistent focus handling and activation behavior, and a spinner displayed until the given `reveal` promise is resolved. Document widgets, like the notebook and text editor and other documents opened from the document manager, implement the `IDocumentWidget` interface (instead of `DocumentRegistry.IReadyWidget`), which builds on `MainAreaWidget` and adds a `.context` attribute for the document context and makes dirty handling consistent. Extension authors may consider inheriting from the `MainAreaWidget` or `DocumentWidget` class for consistency. Several effects from these changes are noted below. ([#3499](https://github.com/jupyterlab/jupyterlab/pull/3499), [#4453](https://github.com/jupyterlab/jupyterlab/pull/4453))
  * The notebook panel `.notebook` attribute is renamed to `.content`.
  * The text editor is now the `.content` of a `DocumentWidget`, so the top-level editor widget has a toolbar and the editor itself is `widget.content.editor` rather than just `widget.editor`.
  * Mime documents use a `MimeContent` widget embedded inside of a `DocumentWidget` now.
  * Main area widgets and document widgets now have a `revealed` promise which resolves when the widget has been revealed (i.e., the spinner has been removed). This should be used instead of the `ready` promise.

Changes in the JupyterLab code infrastructure include:

* The JupyterLab TypeScript codebase is now compiled to ES2015 (ES6) using TypeScript 2.9. We also turned on the TypeScript `esModuleInterop` flag to enable more natural imports from non-es2015 JavaScript modules. With the update to ES2015 output, code generated from async/await syntax became much more manageable, so we have started to use async/await liberally throughout the codebase, especially in tests. Because we use Typedoc for API documentation, we still use syntax compatible with TypeScript 2.7 where Typedoc is used. Extension authors may have some minor compatibility updates to make. If you are writing an extension in TypeScript, we recommend updating to TypeScript 2.9 and targeting ES2015 output as well. ([#4462](https://github.com/jupyterlab/jupyterlab/pull/4462), [#4675](https://github.com/jupyterlab/jupyterlab/pull/4675), [#4714](https://github.com/jupyterlab/jupyterlab/pull/4714), [#4797](https://github.com/jupyterlab/jupyterlab/pull/4797))
* The JupyterLab codebase is now formatted using [Prettier](https://github.com/prettier/prettier). By default the development environment installs a pre-commit hook that formats your staged changes. ([#4090](https://github.com/jupyterlab/jupyterlab/pull/4090))
* Updated build infrastructure using webpack 4 and better typing. ([#4702](https://github.com/jupyterlab/jupyterlab/pull/4702), [#4698](https://github.com/jupyterlab/jupyterlab/pull/4698))
* Upgraded yarn to version 1.6. Please note that you must use NodeJS version 9 or earlier with JupyterLab (i.e., not NodeJS version 10). We will upgrade yarn, with NodeJS version 10 support, when a [bug in yarn](https://github.com/yarnpkg/yarn/issues/5935) is fixed. ([#4804](https://github.com/jupyterlab/jupyterlab/pull/4804))
* Various process utilities were moved to `jupyterlab_launcher`. ([#4696](https://github.com/jupyterlab/jupyterlab/pull/4696))

#### Other fixes

* Fixed a rendering bug with the Launcher in single-document mode. ([#4805](https://github.com/jupyterlab/jupyterlab/pull/4805))
* Fixed a bug where the native context menu could not be triggered in a notebook cell in Chrome. ([#4720](https://github.com/jupyterlab/jupyterlab/pull/4720))
* Fixed a bug where the cursor would not show up in the dark theme. ([#4699](https://github.com/jupyterlab/jupyterlab/pull/4699))
* Fixed a bug preventing relative links from working correctly in alternate `IDrive`s. ([#4613](https://github.com/jupyterlab/jupyterlab/pull/4613))
* Fixed a bug breaking the image viewer upon saving the image. ([#4602](https://github.com/jupyterlab/jupyterlab/pull/4602))
* Fixed the font size for code blocks in notebook Markdown headers. ([#4617](https://github.com/jupyterlab/jupyterlab/pull/4617))
* Prevented a memory leak when repeatedly rendering a Vega chart. ([#4904](https://github.com/jupyterlab/jupyterlab/pull/4904))
* Support dropped terminal connection re-connecting. ([#4763](https://github.com/jupyterlab/jupyterlab/issues/4763), [#4802](https://github.com/jupyterlab/jupyterlab/pull/4802))
* Use `require.ensure` in `vega4-extension` to lazily load `vega-embed` and its dependencies on first render. ([#4706](https://github.com/jupyterlab/jupyterlab/pull/4706))
* Relative links to documents that include anchor tags will now correctly scroll the document to the right place. ([#4692](https://github.com/jupyterlab/jupyterlab/pull/4692))
* Fix default settings JSON in setting editor. ([#4591](https://github.com/jupyterlab/jupyterlab/issues/4591), [#4595](https://github.com/jupyterlab/jupyterlab/pull/4595))
* Fix setting editor pane layout's stretch factor. ([#2971](https://github.com/jupyterlab/jupyterlab/issues/2971), [#4772](https://github.com/jupyterlab/jupyterlab/pull/4772))
* Programmatically set settings are now output with nicer formatting. ([#4870](https://github.com/jupyterlab/jupyterlab/pull/4870))
* Fixed a bug in displaying one-line CSV files. ([#4795](https://github.com/jupyterlab/jupyterlab/issues/4795), [#4796](https://github.com/jupyterlab/jupyterlab/pull/4796))
* Fixed a bug where JSON arrays in rich outputs were collapsed into strings. ([#4480](https://github.com/jupyterlab/jupyterlab/pull/4480))

## [Beta 2 (v0.32.0)](https://github.com/jupyterlab/jupyterlab/releases/tag/v0.32.0)

#### Apr 16, 2018

This is the second in the JupyterLab Beta series of releases. It contains many enhancements, bugfixes, and refinements, including:

* Better handling of a corrupted or invalid state database. ([#3619](https://github.com/jupyterlab/jupyterlab/issues/3619), [#3622](https://github.com/jupyterlab/jupyterlab/issues/3622), [#3687](https://github.com/jupyterlab/jupyterlab/issues/3687), [#4114](https://github.com/jupyterlab/jupyterlab/issues/4114)).
* Fixing file dirty status indicator. ([#3652](https://github.com/jupyterlab/jupyterlab/issues/3652)).
* New option for whether to autosave documents. ([#3734](https://github.com/jupyterlab/jupyterlab/issues/3734)).
* More commands in the notebook context menu. ([#3770](https://github.com/jupyterlab/jupyterlab/issues/3770), [#3909](https://github.com/jupyterlab/jupyterlab/issues/3909))
* Defensively checking for completion metadata from kernels. ([#3888](https://github.com/jupyterlab/jupyterlab/issues/3888))
* New "Shutdown all" button in the Running panel. ([#3764](https://github.com/jupyterlab/jupyterlab/issues/3764))
* Performance improvements wherein non-focused documents poll the server less. ([#3931](https://github.com/jupyterlab/jupyterlab/issues/3931))
* Changing the keyboard shortcut for singled-document-mode to something less easy to trigger. ([#3889](https://github.com/jupyterlab/jupyterlab/issues/3889))
* Performance improvements for rendering text streams, especially around progress bars. ([#4045](https://github.com/jupyterlab/jupyterlab/issues/4045)).
* Canceling a "Restart Kernel" now functions correctly. ([#3703](https://github.com/jupyterlab/jupyterlab/issues/3703)).
* Defer loading file contents until after the application has been restored. ([#4087](https://github.com/jupyterlab/jupyterlab/issues/4087)).
* Ability to rotate, flip, and invert images in the image viewer. ([#4000](https://github.com/jupyterlab/jupyterlab/issues/4000))
* Major performance improvements for large CSV viewing. ([#3997](https://github.com/jupyterlab/jupyterlab/issues/3997)).
* Always show the context menu in the file browser, even for an empty directory. ([#4264](https://github.com/jupyterlab/jupyterlab/issues/4264)).
* Handle asynchronous comm messages in the services library more correctly (Note: this means `@jupyterlab/services` is now at version 2.0!) ([[#4115](https://github.com/jupyterlab/jupyterlab/issues/4115)](https://github.com/jupyterlab/jupyterlab/pull/4115)).
* Display the kernel banner in the console when a kernel is restarted to mark the restart ([[#3663](https://github.com/jupyterlab/jupyterlab/issues/3663)](https://github.com/jupyterlab/jupyterlab/pull/3663)).
* Many tweaks to the UI, as well as better error handling.

## [Beta 1 (v0.31.0)](https://github.com/jupyterlab/jupyterlab/releases/tag/v0.31.0)

#### Jan 11, 2018

* Add a `/tree` handler and `Copy Shareable Link` to file listing right click menu: https://github.com/jupyterlab/jupyterlab/pull/3396
* Experimental support for saved workspaces: [#3490](https://github.com/jupyterlab/jupyterlab/issues/3490), [#3586](https://github.com/jupyterlab/jupyterlab/issues/3586)
* Added types information to the completer: [#3508](https://github.com/jupyterlab/jupyterlab/issues/3508)
* More improvements to the top level menus: https://github.com/jupyterlab/jupyterlab/pull/3344
* Editor settings for notebook cells: https://github.com/jupyterlab/jupyterlab/pull/3441
* Simplification of theme extensions: https://github.com/jupyterlab/jupyterlab/pull/3423
* New CSS variable naming scheme: https://github.com/jupyterlab/jupyterlab/pull/3403
* Improvements to cell selection and dragging: https://github.com/jupyterlab/jupyterlab/pull/3414
* Style and typography improvements: https://github.com/jupyterlab/jupyterlab/pull/3468 https://github.com/jupyterlab/jupyterlab/pull/3457 https://github.com/jupyterlab/jupyterlab/pull/3445 https://github.com/jupyterlab/jupyterlab/pull/3431 https://github.com/jupyterlab/jupyterlab/pull/3428 https://github.com/jupyterlab/jupyterlab/pull/3408 https://github.com/jupyterlab/jupyterlab/pull/3418

## [v0.30.0](https://github.com/jupyterlab/jupyterlab/releases/tag/v0.30.0)

#### Dec 05, 2017

* Semantic menus: https://github.com/jupyterlab/jupyterlab/pull/3182
* Settings editor now allows comments and provides setting validation: https://github.com/jupyterlab/jupyterlab/pull/3167
* Switch to Yarn as the package manager: https://github.com/jupyterlab/jupyterlab/pull/3182
* Support for carriage return in outputs: [#2761](https://github.com/jupyterlab/jupyterlab/issues/2761)
* Upgrade to TypeScript 2.6: https://github.com/jupyterlab/jupyterlab/pull/3288
* Cleanup of the build, packaging, and extension systems. `jupyter labextension install` is now the recommended way to install a local directory. Local directories are considered linked to the application. cf https://github.com/jupyterlab/jupyterlab/pull/3182
* `--core-mode` and `--dev-mode` are now semantically different. `--core-mode` is a version of JupyterLab using released JavaScript packages and is what we ship in the Python package. `--dev-mode` is for unreleased JavaScript and shows the red banner at the top of the page. https://github.com/jupyterlab/jupyterlab/pull/3270

## [v0.29.2](https://github.com/jupyterlab/jupyterlab/releases/tag/v0.29.2)

#### Nov 17, 2017

Bug fix for file browser right click handling. https://github.com/jupyterlab/jupyterlab/issues/3019

## [v0.29.0](https://github.com/jupyterlab/jupyterlab/releases/tag/v0.29.0)

#### Nov 09, 2017

* Create new view of cell in cell context menu. [#3159](https://github.com/jupyterlab/jupyterlab/issues/3159)
* New Renderers for VDOM and JSON mime types and files. [#3157](https://github.com/jupyterlab/jupyterlab/issues/3157)
* Switch to React for our VDOM implementation. Affects the `VDomRenderer` class. [#3133](https://github.com/jupyterlab/jupyterlab/issues/3133)
* Standalone Cell Example. [#3155](https://github.com/jupyterlab/jupyterlab/issues/3155)

## [v0.28.0](https://github.com/jupyterlab/jupyterlab/releases/tag/v0.28.0)

#### Oct 16, 2017

This release generally focuses on developer and extension author enhancements and general bug fixes.

* Plugin id and schema file conventions change. https://github.com/jupyterlab/jupyterlab/pull/2936.
* Theme authoring conventions change. [#3061](https://github.com/jupyterlab/jupyterlab/issues/3061)
* Enhancements to enabling and disabling of extensions. [#3078](https://github.com/jupyterlab/jupyterlab/issues/3078)
* Mime extensions API change (`name` -> `id` and new naming convention). [#3078](https://github.com/jupyterlab/jupyterlab/issues/3078)
* Added a `jupyter lab --watch` mode for extension authors. [#3077](https://github.com/jupyterlab/jupyterlab/issues/3077)
* New comprehensive extension authoring tutorial. [#2921](https://github.com/jupyterlab/jupyterlab/issues/2921)
* Added the ability to use an alternate LaTeX renderer. [#2974](https://github.com/jupyterlab/jupyterlab/issues/2974)
* Numerous bug fixes and style enhancements.

## [v0.27.0](https://github.com/jupyterlab/jupyterlab/releases/tag/v0.27.0)

#### Aug 23, 2017

* Added support for dynamic theme loading. https://github.com/jupyterlab/jupyterlab/pull/2759
* Added an application splash screen. https://github.com/jupyterlab/jupyterlab/pull/2899
* Enhancements to the settings editor. https://github.com/jupyterlab/jupyterlab/pull/2784
* Added a PDF viewer. [#2867](https://github.com/jupyterlab/jupyterlab/issues/2867)
* Numerous bug fixes and style improvements.

## [v0.26.0](https://github.com/jupyterlab/jupyterlab/releases/tag/v0.26.0)

#### Jul 21, 2017

* Implemented server side handling of users settings: https://github.com/jupyterlab/jupyterlab/pull/2585
* Revamped the handling of file types in the application - affects document and mime renderers: https://github.com/jupyterlab/jupyterlab/pull/2701
* Updated dialog API - uses virtual DOM instead of raw DOM nodes and better use of the widget lifecycle: https://github.com/jupyterlab/jupyterlab/pull/2661

## [v0.25.0](https://github.com/jupyterlab/jupyterlab/releases/tag/v0.25.0)

#### Jul 07, 2017

* Added a new extension type for mime renderers, with the `vega2-extension` as a built-in example. Also overhauled the rendermime interfaces.
  https://github.com/jupyterlab/jupyterlab/pull/2488
  https://github.com/jupyterlab/jupyterlab/pull/2555
  https://github.com/jupyterlab/jupyterlab/pull/2595
* Finished JSON-schema based settings system, using client-side storage for now.
  https://github.com/jupyterlab/jupyterlab/pull/2411
* Overhauled the launcher design.
  https://github.com/jupyterlab/jupyterlab/pull/2506
  https://github.com/jupyterlab/jupyterlab/pull/2580
* Numerous bug fixes and style updates.

## [v0.24.0](https://github.com/jupyterlab/jupyterlab/releases/tag/v0.24.0)

#### Jun 16, 2017

* Overhaul of the launcher. [#2380](https://github.com/jupyterlab/jupyterlab/issues/2380)
* Initial implementation of client-side settings system. [#2157](https://github.com/jupyterlab/jupyterlab/issues/2157)
* Updatable outputs. [#2439](https://github.com/jupyterlab/jupyterlab/issues/2439)
* Use new Phosphor Datagrid for CSV viewer. [#2433](https://github.com/jupyterlab/jupyterlab/issues/2433)
* Added ability to enable/disable extensions without rebuilding. [#2409](https://github.com/jupyterlab/jupyterlab/issues/2409)
* Added language and tab settings for the file viewer. [#2406](https://github.com/jupyterlab/jupyterlab/issues/2406)
* Improvements to real time collaboration experience. [#2387](https://github.com/jupyterlab/jupyterlab/issues/2387) [#2333](https://github.com/jupyterlab/jupyterlab/issues/2333)
* Compatibility checking for extensions. [#2410](https://github.com/jupyterlab/jupyterlab/issues/2410)
* Numerous bug fixes and style improvements.

## [v0.23.0](https://github.com/jupyterlab/jupyterlab/releases/tag/v0.23.0)

#### Jun 02, 2017

* Chat box feature. https://github.com/jupyterlab/jupyterlab/pull/2118
* Collaborative cursors. https://github.com/jupyterlab/jupyterlab/pull/2139
* Added concept of Drive to ContentsManager. https://github.com/jupyterlab/jupyterlab/pull/2248
* Refactored to enable switching the theme. https://github.com/jupyterlab/jupyterlab/pull/2283
* Clean up the APIs around kernel execution. https://github.com/jupyterlab/jupyterlab/pull/2266
* Various bug fixes and style improvements.

## [0.22.0 (v0.22.0)](https://github.com/jupyterlab/jupyterlab/releases/tag/v0.22.0)

#### May 18, 2017

* Export To... for notebooks. https://github.com/jupyterlab/jupyterlab/pull/2200
* Change kernel by clicking on the kernel name in the notebook. https://github.com/jupyterlab/jupyterlab/pull/2195
* Improved handling of running code in text editors. https://github.com/jupyterlab/jupyterlab/pull/2191
* Can select file in file browser by typing: https://github.com/jupyterlab/jupyterlab/pull/2190
* Ability to open a console for a notebook. https://github.com/jupyterlab/jupyterlab/pull/2189
* Upgrade to Phosphor 1.2 with Command Palette fuzzy matching improvements. [#1182](https://github.com/jupyterlab/jupyterlab/issues/1182)
* Rename of widgets that had `Widget` in the name and associated package names. https://github.com/jupyterlab/jupyterlab/pull/2177
* New `jupyter labhub` command to launch JupyterLab on JupyterHub: https://github.com/jupyterlab/jupyterlab/pull/2222
* Removed the `utils` from `@jupyterlab/services` in favor of `PageConfig` and `ServerConnection`. https://github.com/jupyterlab/jupyterlab/pull/2173 https://github.com/jupyterlab/jupyterlab/pull/2185
* Cleanup, bug fixes, and style updates.

## [0.20.0 (v0.20.0)](https://github.com/jupyterlab/jupyterlab/releases/tag/v0.20.0)

#### Apr 21, 2017

Release Notes:

* Overhaul of extension handling, see updated docs for [users](https://github.com/jupyterlab/jupyterlab/blob/dd83a2e4be8bf23c610c163afe4b480215514764/tutorial/extensions_user.md) and [developers](https://github.com/jupyterlab/jupyterlab/blob/dd83a2e4be8bf23c610c163afe4b480215514764/tutorial/extensions_dev.md). https://github.com/jupyterlab/jupyterlab/pull/2023
* Added single document mode and a `Tabs` sidebar. https://github.com/jupyterlab/jupyterlab/pull/2037
* More work toward real time collaboration - implemented a model database interface that can be in-memory by real time backends. https://github.com/jupyterlab/jupyterlab/pull/2039

Numerous bug fixes and improvements.

## [Release 0.19 (v0.19.0)](https://github.com/jupyterlab/jupyterlab/releases/tag/v0.19.0)

#### Apr 04, 2017

Mainly backend-focused release with compatibility with Phosphor 1.0 and a big refactor of session handling (the ClientSession class) that provides a simpler object for classes like notebooks, consoles, inspectors, etc. to use to communicate with the API. Also includes improvements to the development workflow of JupyterLab itself after the big split.

https://github.com/jupyterlab/jupyterlab/pull/1984
https://github.com/jupyterlab/jupyterlab/pull/1927

## [Version 0.18 (v0.18.0)](https://github.com/jupyterlab/jupyterlab/releases/tag/v0.18.0)

#### Mar 21, 2017

* Split the repository into multiple packages that are managed using the
  lerna build tool. https://github.com/jupyterlab/jupyterlab/issues/1773
* Added restoration of main area layout on refresh. https://github.com/jupyterlab/jupyterlab/pull/1880
* Numerous bug fixes and style updates.

## [0.17.0 (v0.17.0)](https://github.com/jupyterlab/jupyterlab/releases/tag/v0.17.0)

#### Mar 01, 2017

* Upgrade to new `@phosphor` packages - brings a new Command Palette interaction that should be more intuitive, and restores the ability to drag to dock panel edges https://github.com/jupyterlab/jupyterlab/pull/1762.
* Refactor of `RenderMime` and associated renders to use live models. See https://github.com/jupyterlab/jupyterlab/pull/1709 and https://github.com/jupyterlab/jupyterlab/issues/1763.
* Improvements and bug fixes for the completer widget: https://github.com/jupyterlab/jupyterlab/pull/1778
* Upgrade CodeMirror to 5.23: https://github.com/jupyterlab/jupyterlab/pull/1764
* Numerous style updates and bug fixes.

## [Version 16 (v0.16.0)](https://github.com/jupyterlab/jupyterlab/releases/tag/v0.16.0)

#### Feb 09, 2017

* Adds a Cell Tools sidebar that allows you to edit notebook cell metadata. [#1586](https://github.com/jupyterlab/jupyterlab/issues/1586).
* Adds keyboard shortcuts to switch between tabs (Cmd/Ctrl LeftArrow and Cmd/Ctrl RightArrow). [#1647](https://github.com/jupyterlab/jupyterlab/issues/1647)
* Upgrades to xterm.js 2.3. [#1664](https://github.com/jupyterlab/jupyterlab/issues/1664)
* Fixes a bug in application config, but lab extensions will need to be re-enabled. [#1607](https://github.com/jupyterlab/jupyterlab/issues/1607)
* Numerous other bug fixes and style improvements.
