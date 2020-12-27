FROM microsoft/windowsservercore:ltsc2019

SHELL ["powershell"]

# Based on:
# - https://blog.alexellis.io/3-steps-to-msbuild-with-docker/
# - https://github.com/kohnakagawa/docker-msbuild
# - https://gist.github.com/giseongeom/285bbe1abff42a0282537f16e329b94e

# Confusingly, vs/15 is actually Visual Studio 2017
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\\Downloads\\vs_buildtools.exe

# Command reference: https://docs.microsoft.com/en-us/visualstudio/install/command-line-parameter-examples?view=vs-2017
# Component/workload IDs: https://docs.microsoft.com/en-us/visualstudio/install/workload-and-component-ids?view=vs-2017
RUN C:\\Downloads\\vs_buildtools.exe \
    --add Microsoft.VisualStudio.Workload.MSBuildTools \
    --add Microsoft.VisualStudio.Workload.UniversalBuildTools \
    --add Microsoft.VisualStudio.Component.Windows10SDK.17763 \
    --add Microsoft.VisualStudio.Workload.VCTools \
    --add Microsoft.Component.VC.Runtime.UCRTSDK \
    --wait \
    --passive \
    --norestart \
    --quiet

RUN SETX /M Path "%Path%;C:\\Program Files (x86)\\Microsoft Visual Studio\\2017\\BuildTools\\MSBuild\\15.0\\Bin"

# Possibilities if this doesn't work:
# --includeRecommended `

# For future use consider:
# --add Microsoft.VisualStudio.Component.VC.Tools.ARM \
# --add Microsoft.VisualStudio.Component.VC.Tools.ARM64 \
