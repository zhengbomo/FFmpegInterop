# FFmpegInterop
FFmpegInterop build for nuget

# Build on 2016.12.11

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
  
