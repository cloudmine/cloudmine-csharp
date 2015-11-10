# Upload New File to Application

In addition to object data, you are also able to store files in CloudMine. A stream of the file contents, a file id, and an optional MIME content type are needed to create a CMFile. If no content type is specified, a default of "application/octet-stream" is used.

```csharp
using (FileStream fileStream = File.OpenRead(filePath))
{
    MemoryStream memStream = new MemoryStream();
    memStream.SetLength(fileStream.Length);
    fileStream.Read(memStream.GetBuffer(), 0, (int)fileStream.Length);

	Task<CMFileResponse> fileResponse = 
   		userService.Upload ("iej20...", fileStream, user);
	fileResponse.wait ();
}
```

{{warning "If the file id given already exists on the server, the existing file will be overwritten."}}
