Win + R
cmd.exe
Ctrl + shift + enter
Yes
reagentc /disable
DISM.EXE /Export-Image /SourceImageFile:%SYSTEMROOT%\System32\WinRE.wim /SourceIndex:1 /DestinationImageFile:C:\ wherever you want the path to be at /CheckIntegrity
also if the destination has spaces in the text use "
for example
DISM.EXE /export-image /sourceimagefile:%SYSTEMROOT%\System32\WinRE.wim /sourceindex:1 /destinationImageFile:"C:\Windows RE\Backup\WinRE.wim" /CheckIntegrity
use these to keep your winre image safe
reagentc /disable is important, or else export image wouldn't work.
