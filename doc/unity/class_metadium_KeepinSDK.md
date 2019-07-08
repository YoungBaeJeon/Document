# KeepinSDK Class Reference

Authentication()
--------------------------------------------------------
void Authentication([CallbackDelegete](./namespace_metadium.md#CallbackDelegete) callback,string nonce,bool autoRegister = `false`,string expectMetaId = `null` )  
  
Request authentication of the service in Keepin App.  

Parameters  
  * callback : Callback delegate to receive response to authentication  
  * nonce : Data to sign with the service key  
  * autoRegister : If service is not registered and this value is true, request to register.  
  * expectMetaId : Expect Keepin's Meta ID to match the given Meta ID. If IDs are not same, error code reponse with NotMatchedMetaID(2)  

Initialize()
----------------------------------------------------
static [KeepinSDK](./class_metadium_KeepinSDK.md) Initialize(string serviceId)

SDK initializing

Parameters
  * serviceId : Service ID assigned by Metadium

Returns
  * SDK instance
  
  
  
  
Install()
-------------------------------------------------
void Install()  

Launch store to download Keepin app

IsInstalled()
-----------------------------------------------------
bool IsInstalled()  

Check to installed Keepin App.

Returns
  * if installed keepin app, return true


OnError()
-------------------------------------------------
void OnError(string message)  
  
On response error  
  
Parameters  
  * message : error message

OnResult()
--------------------------------------------------
void OnResult(string message)  
  
On response data  
  
Parameters  
  * message : uri for iOS, json for android. If platform is iOS, this function call error response.  

Register()
--------------------------------------------------
void Register([CallbackDelegete](./namespace_metadium.md#CallbackDelegete) callback,string nonce)  
  
Request registration of the service in Keepin App.  
  
Parameters  
  * callback : Callback delegate to receive response to register  
  * nonce : Data to sign with the service key


