Trying to follow instructions on https://stride3d.github.io/stride-community-toolkit/manual/code-only/create-project.html

Error visible from the Build log from Visual Studio

    MSB3073 The command ""C:\Users\xxx.nuget\packages\stride.core.assets.compilerapp\4.2.0.2122\buildTransitive..\lib\net8.0\Stride.Core.Assets.CompilerApp.exe" --disable-auto-compile --project-configuration "Debug" --platform=Windows --project-configuration=Debug --compile-property:StrideGraphicsApi=Direct3D11 --output-path="D:\repos\xxx\src\Console\bin\Debug\net8.0\data" --build-path="D:\repos\xxx\src\Console\obj\stride\assetbuild\data" --package-file="D:\repos\xxx\src\Console\Console.csproj" --msbuild-uptodatecheck-filebase="D:\repos\xxx\src\Console\obj\Debug\net8.0\stride\assetcompiler-uptodatecheck"" exited with code 1.

at

    C:\Users\xxx.nuget\packages\stride.core.assets.compilerapp\4.2.0.2122\buildTransitive\Stride.Core.Assets.CompilerApp.targets line 153

After manually running the failing underlying command in CLI, we get this error:

    Error restoring NuGet packages!
    Could not load file or assembly 'System.Security.Cryptography.Pkcs, Version=6.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'. The system cannot find the file specified.

Repro:

1. Install Microsoft Visual C++ 2015-2022 Redistributable , .NET 8 SDK
1. Create new console app with .NET 8.0
1. Add package Stride.CommunityToolkit 1.0.0-preview.38
1. Replace Program.cs with provided sample code
1. Try to build, either from VS or with `dotnet build`
