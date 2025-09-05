#charp notes
dotnet sdk installation 
windows: 
download executable from (https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/sdk-8.0.413-windows-x64-installer)[here] and install sdk. this one is lts 8.0 however you may also find latest and older version here, 
latest as of now (9.0) : https://dotnet.microsoft.com/en-us/download
frameworks older ones: https://dotnet.microsoft.com/en-us/download/dotnet-framework .
trying to run dotnet projects in linux(arch based)
1.  install dotnet sdk
    sudo pacman -S dotnet-sdk
    or need version like .net9 or 6 use
    yay -S dotnet-sdk-6.0

to check if its installed
dotnet --version

to create new console project
dotnet new console -o <projectname>
cd <projectname>

to run app (inside project folder containing csproj file)

dotnet run

to build (auto mode / simple mode )
dotnet build

files will be in projectfolder/bin/debug/net9.0/

to create new winforms (not tried yet) (replace framework value to your liking)
dotnet new winforms -o <projectname> --framework net9.0
cd <projectname>
dotnet run
or
dotnet build

there are 3 modes which we can build project

1. compiles project and gives files considering machine have .net sdk installed
   dotnet publish -c Release -r linux-x64 -o publish/linux
   dotnet publish -c Release -r win-x64 -o publish/windows
   publish means building project into executable exe or bash, -c means type of final output Release/Debug, -r platform means which type of executable want according to it win=exe linux=bash. -o folder to where executables and dll files should be stored.

2. compiles project and gives bunch of files mostly .net runtime so user do not get runtime errors
   same as above but with --self-contained flag does gives extra dll and files which is dependency for .net runtime

3. compiles everthing into a bash or exe which is heavier but contains everything.
   same as above but with flag p:PublishSingleFile=true
   we can also use trin flag p:PublishTrimmed=true to reduce size.
