# Eldoir's notes:
To use AssetStudio:
- Download the project and open the solution with VS.
- Read the **Build** section of this Readme to build properly.
- You will find the FBX SDK at: [Autodesk website link](https://www.autodesk.com/developer-network/platform-technologies/fbx-sdk-2020-0). You should choose the **FBX SDK 2020.0.1 VS2017** version as stated in the **Build** section.
- **Very important**: install the FBX SDK on your disk **C:** !!! I tried on disk D: and lost a lot of time dealing with stupid linking errors when building.
- The **Build** section says to "_change include directory and library directory to point to the FBX SDK directory_". That means:
  * Right-clicking on the _AssetStudioFBXNative_ project in the solution, then going to _Properties_ -> _VC++ Directories_ and editing the _Include Directories_ to add a path to _C:\Program Files\Autodesk\FBX\FBX SDK\2020.0.1\include_
  * Also editing the _Library Directories_ to add a path to _C:\Program Files\Autodesk\FBX\FBX SDK\2020.0.1\lib\vs2017\x86_.
  * Then hit Apply and try to build.
- Once the build has succeeded, you can launch **AssetStudio** in _AssetStudio\AssetStudioGUI\bin\Debug\AssetStudioGUI.exe_.
- Enjoy! You can now open files with extension _*.assets_ like _resources.assets_, _sharedassets0.assets_, and also level files like _level0_, _level1_... from any Unity app.

# AssetStudio
[![Build status](https://ci.appveyor.com/api/projects/status/rnu7l90422pdewx4?svg=true)](https://ci.appveyor.com/project/Perfare/assetstudio/branch/master/artifacts)

**None of the repo, the tool, nor the repo owner is affiliated with, or sponsored or authorized by, Unity Technologies or its affiliates.**

AssetStudio is a tool for exploring, extracting and exporting assets and assetbundles.

## Features
* Support version:
  * 2.5 - 2020.2
* Support asset types:
  * **Texture2D** : convert to png, tga, jpeg, bmp
  * **Sprite** : crop Texture2D to png, tga, jpeg, bmp
  * **AudioClip** : mp3, ogg, wav, m4a, fsb. support convert FSB file to WAV(PCM)
  * **Font** : ttf, otf
  * **Mesh** : obj
  * **TextAsset**
  * **Shader**
  * **MovieTexture**
  * **VideoClip**
  * **MonoBehaviour** : json
  * **Animator** : export to FBX file with bound AnimationClip

## Requirements

- [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)

## Usage

### Load Assets/AssetBundles

Use **File-Load file** or **File-Load folder**.

When AssetStudio loads AssetBundles, it decompresses and reads it directly in memory, which may cause a large amount of memory to be used. You can use **File-Extract file** or **File-Extract folder** to extract AssetBundles to another folder, and then read.

### Extract/Decompress AssetBundles

Use **File-Extract file** or **File-Extract folder**.

### Export Assets

use **Export** menu.

### Export Model

Export model from "Scene Hierarchy" using the **Model** menu.

Export Animator from "Asset List" using the **Export** menu.

#### With AnimationClip

Select model from "Scene Hierarchy" then select the AnimationClip from "Asset List", using **Model-Export selected objects with AnimationClip** to export.

Export Animator will export bound AnimationClip or use **Ctrl** to select Animator and AnimationClip from "Asset List", using **Export-Export Animator with selected AnimationClip** to export.

### Export MonoBehaviour

When you select an asset of the MonoBehaviour type for the first time, AssetStudio will ask you the directory where the assembly is located, please select the directory where the assembly is located, such as the `Managed` folder.

#### For Il2Cpp

First, use my other program [Il2CppDumper](https://github.com/Perfare/Il2CppDumper) to generate dummy dll, then when using AssetStudio to select the assembly directory, select the dummy dll folder.

## Build

* Visual Studio 2019 or newer
* **AssetStudioFBXNative** uses FBX SDK 2020.0.1 VS2017, before building, you need to install the FBX SDK and modify the project file, change include directory and library directory to point to the FBX SDK directory

## Open source libraries used

### Texture2DDecoder
* [Ishotihadus/mikunyan](https://github.com/Ishotihadus/mikunyan)
* [BinomialLLC/crunch](https://github.com/BinomialLLC/crunch)
* [Unity-Technologies/crunch](https://github.com/Unity-Technologies/crunch/tree/unity)
