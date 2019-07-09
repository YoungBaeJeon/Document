# Getting Start

### Unity
Download and import [KeepinSDK](http://u3d.as/1zHk) from Asset store.  
Write the code referring to KeepinSDK/Example inside the Asset.  (Refer to KeepinSDK/Example in Asset for writing code.)  
  
##### Setting Service ID
Initialize the SDK with the [registered service ID](service_registry.md).  
```C#
KeepinSDK keepinSDK = KeepinSDK.Initialize("service id");
```
##### Request register service
Following are example showing request for service register to Keepin App. 
```C#
// Check install
if (keepinSDK.IsInstalled())
{
    // Request service register
    keepinSDK.Register(new CallbackDelegete(RegisterOnResult), "message");
}
else
{
    // Launch store
    keepinSDK.Install();
}
```
Define Callback function for response.
```C#
static void RegisterOnResult(Result result)
{
    if (result.IsSuccess())
    {
        // success register
        // result.metaID : user MetaID
        // result.sign   : signature message by user's private key
        // result.txID   : 
    }
    else
    {
        GameObject.Find("MetaID").GetComponent<Text>().text = "Register\nError=" + ((ErrorCode)result.code).ToString();
    }

}
```

### Android
Work In Progress

### iOS
Work In Progress

