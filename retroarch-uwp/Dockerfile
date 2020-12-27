# escape=`

# Articles that helped me with the below:
# - https://devblogs.microsoft.com/setup/no-container-image-for-build-tools-for-visual-studio-2017/
# - https://docs.microsoft.com/en-us/visualstudio/install/advanced-build-tools-container?view=vs-2017

# Command reference: https://docs.microsoft.com/en-us/visualstudio/install/command-line-parameter-examples?view=vs-2017
# Component/workload IDs: https://docs.microsoft.com/en-us/visualstudio/install/workload-and-component-ids?view=vs-2017


FROM mcr.microsoft.com/windows/servercore:ltsc2019

# Restore the default Windows shell for correct batch processing.
SHELL ["cmd", "/S", "/C"]

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Confusingly, vs/15 is actually Visual Studio 2017
# Download the Build Tools bootstrapper.
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --add Microsoft.VisualStudio.Workload.MSBuildTools `
    --add Microsoft.VisualStudio.Workload.UniversalBuildTools `
    --add Microsoft.VisualStudio.Component.Windows10SDK.17763 `
    --add Microsoft.VisualStudio.Workload.VCTools `
    --add Microsoft.Component.VC.Runtime.UCRTSDK

RUN SETX /M Path "%Path%;C:\\BuildTools\MSBuild\15.0\Bin"

# Possibilities if this doesn't work:
# --includeRecommended `

# For future use consider:
# --add Microsoft.VisualStudio.Component.VC.Tools.ARM `
# --add Microsoft.VisualStudio.Component.VC.Tools.ARM64 `
