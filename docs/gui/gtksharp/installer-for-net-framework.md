---
title: Gtk-Sharp Installer for .NET Framework
redirect_from:
  - /Gtk-Sharp_Installer_for_.NET_Framework/
---

Introduction
============

The Gtk# installers for the .NET Framework 1.1 give .NET developers all of the pieces they need to build and run Gtk#-based applications, the same set of libraries that are used to build Unix applications on Mono.

Applications developed with Gtk# on .NET do not require Mono to run.

If the application is a 100% .NET, without using P/Invoke to call into Win32 functions or using some Windows-specific assemblies, the code will run out of the box on Unix and Linux systems with Mono.

The Gtk# installers for .NET come in two variations, SDK and Runtime (Redistributable). These can be downloaded from the [Downloads](/download/) page.

Gtk# Runtime/Redistributable Installer
---------------------------------------

The Gtk# Runtime Installer includes the components necessary to execute run applications on the .NET Framework that were created with Gtk#.

It contains the Gtk+ runtime and the Gtk# assemblies which get registered into Global Assembly Cache.

For example, companies like [Medsphere](http://www.medsphere.com) use the Gtk# Runtime Installer for the version of their main product that runs in Microsoft Windows. They use Mono on Linux with Gtk# and they use .NET on Windows with this installer for Gtk#.

The Gtk# SDK Installer for the .NET Framework
----------------------------------------------

The SDK installer contains all the tools required to develop applications with Gtk# on Windows, it includes:

-   The Glade GUI designer.
-   Gtk+ runtime.
-   Gtk# assemblies.
-   Registration of Gtk# assemblies for Visual Studio.NET 2003.
-   Visual Studio.NET 2003 template files (Gtk# and Glade# based applications).
-   pkg-config files (for those looking for adventure)

Once installed, when you create a new project from Visual Studio.NET 2003, this should appear:

[![Gtksharp-project-template.PNG](/archived/images/f/ff/Gtksharp-project-template.PNG)](/archived/images/f/ff/Gtksharp-project-template.PNG)

The templates contain sample programs that you can use as starting points for your application.

See the [Working_with_Mono_and_Visual_Studio](/archived/working_with_mono_and_visual_studio "Working with Mono and Visual Studio") page for more information on using Mono with Visual Studio.

Notes and Observations
======================

One mayor difference between the Gtk# installers for .NET and the Mono Combined Installer for Windows is that the Gtk# installers perform libary installations into the Microsoft .NET Global Assembly Cache (GAC). Mono has its own GAC that is independent of the Microsoft .NET GAC.

Obtaining the Installers
========================

The runtime and sdk installers for Gtk# are available on the Windows platform section of the [Downloads](/download/) page.

