# FFmpegInterop
FFmpegInterop build for nuget

# Build on 2016.12.11

* FFmpegInterop [@67a29ba](https://github.com/Microsoft/FFmpegInterop/tree/67a29bab939303caf694d3d813ee18fe5ff717c9)
* ffmpeg [@12320c0](https://github.com/FFmpeg/FFmpeg/tree/12320c08221f0eecf6d9af3a6f12f42e656f0674)

> only for Win10 ARM/x86/x64

## Nuget
```
Install-Package FFmpegInterop.UWP
```
> https://www.nuget.org/packages/FFmpegInterop.UWP/

## Usage
### 1. xaml
```xaml
<MediaElement AutoPlay="True"
              x:Name="MediaElement"/>
```

### 2. cs
```cs
var folder = await Package.Current.InstalledLocation.GetFolderAsync("Assets");
folder = await folder.GetFolderAsync("Video");
var file = await folder.GetFileAsync("test.rmvb");

var fFmpegMss = FFmpegInteropMSS.CreateFFmpegInteropMSSFromUri(file.Path, true, true);
//or create from uri
//var fFmpegMss = FFmpegInteropMSS.CreateFFmpegInteropMSSFromUri("http://www.example.com/test.rmvb", true, true);

var mss = fFmpegMss?.GetMediaStreamSource();
if (mss != null)
{
    MediaElement.SetMediaStreamSource(mss);
}
```
  
