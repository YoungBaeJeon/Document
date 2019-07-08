# Getting Start

### Unity
Download and import [KeepinSDK](http://u3d.as/1zHk) from Asset store.  
Write the code referring to KeepinSDK/Example inside the Asset.  (Asset 안에 KeepinSDK/Example 을 참고하여 코드를 작성합니다.)  
  
##### Setting Service ID
Initialize the SDK with the [registered service ID](service_registry.md).  
```C#
KeepinSDK keepinSDK = KeepinSDK.Initialize("service id");
```
##### Request register service
Keepin 앱에 인증을 사용하기 위한 권한을 요청하는 예제입니다.  
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
Callback 받기 위한 함수를 정의 합니다.
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
준비중

### iOS
준비중

