# Server side 에서의 인증 처리
Server 쪽에서 인증 처리하기 위해 각 언어별 설정 및 샘플 코드를 설명합니다.  


### Java

[Web3j](https://github.com/web3j/web3j#getting-started) 추가. 아래 코드는 4.2.0 기준으로 코드가 작성되어 있음.  
Contract method 를 쉽게 호출하기 위해 generate 된 [IdentityRegistry](https://github.com/YoungBaeJeon/metadium_android_sdk/edit/master/app/src/main/java/com/metadium/metadiumsdk/IdentityRegistry.java), [ServiceKeyResolver](https://github.com/YoungBaeJeon/metadium_android_sdk/edit/master/app/src/main/java/com/metadium/metadiumsdk/IdentityRegistry.java) 소스 복사하여 프로젝트에 포함시킵니다.  

```java
// signature util method
public static Sign.SignatureData stringToSignatureData(String signature) {
    byte[] bytes = Numeric.hexStringToByteArray(signature);
    return new Sign.SignatureData(bytes[64], Arrays.copyOfRange(bytes, 0, 32), Arrays.copyOfRange(bytes, 32, 64));
}

final bool IS_TEST_NET = true;
final String OPEN_API_NODE_URL = IS_TEST_NET ? "https://api.metadium.com/dev" : "https://api.metadium.com/prod";
final String IDENTITY_REGISTRY_CONTRACT_ADDRESS = IS_TEST_NET ? "0xbe2bb3d7085ff04bde4b3f177a730a826f05cb70" : "0x42bbff659772231bb63c7c175a1021e080a4cf9d";

String sinature = "...";    // Cilent 에서 전달 받은 서명
String metaId = "...";      // Client 에서 전달 받은 Meta ID
String serviceId = "...";   // 발급받은 service id


// ec-recover를 통해 서명자의 주소 획득
SignatureData signatureData = stringToSignatureData(signature);
BigInteger publicKey;
try {
    publicKey = Sign.signedMessageToKey(nonce.getBytes(), signatureData);
}
catch (SignatureException e) {
    // invalid signature
    return;
}
String key = Numeric.prependHexPrefix(Keys.getAddress(publicKey));

// convert metaId to ein
BigInteger ein = Numeric.toBigInt(metaId);

// IdentityRegistry 에서 resolver address 획득
Web3j web3j = Web3j.build(new HttpService(OPEN_API_NODE_URL));
IdentityRegistry identityRegistry = IdentityRegistry.load(
        IDENTITY_REGISTRY_CONTRACT_ADDRESS,
        web3j,
        new ReadonlyTransactionManager(web3j, null),
        new StaticGasProvider(BigInteger.ZERO, BigInteger.ZERO)
);
String resolverAddress;
try {
    Tuple4<String, List<String>, List<String>, List<String>> identity = identityRegistry.getIdentity(ein).send();
    if (identity.getValue4().size() > 0) {
        resolverAddress = identity.getValue4().get(0);
    }
    else {
        // not exists resolver
    }
}
catch (Exception e) {
    // not found identity or call error
    return;
}

// 키가 등록되어 있는지 확인
ServiceKeyResolver serviceKeyResolver = ServiceKeyResolver.load(
        resolverAddress,
        web3j,
        new ReadonlyTransactionManager(web3j, null),
        new StaticGasProvider(BigInteger.ZERO, BigInteger.ZERO)
);
try {
    boolean hasForKey = serviceKeyResolver.isKeyFor(key, ein).send();
    String symbol = serviceKeyResolver.getSymbol(key).send();

    if (hasForKey) {
        if (serviceId.equalsIgnoreCase(symbol)) {
            // 키 등록되어 있음
        }
        else {
            // 키는 등록되어 있으나 제공 서비스가 아님
        }
    }
    else {
        // 해당키가 등록되어 있지 않음
    }
}
catch (Exception e) {
    // error
}
```
  
  
  
### JavaScript
```javascript
import Web3 from 'web3';

const IS_TESTNET = true;
const OPEN_API_NODE_URL = IS_TEST_NET ? 'https://api.metadium.com/dev' : 'https://api.metadium.com/prod';
const IDENTITY_REGISTRY_CONTRACT_ADDRESS = IS_TEST_NET ? '0xbe2bb3d7085ff04bde4b3f177a730a826f05cb70' : '0x42bbff659772231bb63c7c175a1021e080a4cf9d';

let nonce = '....';      // 서명 시 사용된 메세지
let sinature = '...';    // Cilent 에서 전달 받은 서명
let metaId = "...";     // Client 에서 전달 받은 Meta ID
let serviceId = "...";   // 발급받은 service id

// init web3
const web3 = new Web3();
web3.setProvider(new Web3.providers.HttpProvider(OPEN_API_NODE_URL));

// ec-recovery
const key = web3.accounts.recover(web3.utils.sha3(nonce), signature, true);

// IdentityRegistry 에서 resolver address 획득
const identityRegistryContract = web3.eth.Contract(ABI_CODE, IDENTITY_REGISTRY_CONTRACT_ADDRESS);
const identity = await identityRegistryContract.methods.getIdentity(ein).call();
const serviceKeyResolverAddress = identity.resolvers[0];

// 키가 등록되어 있는지 확인
const serviceKeyResolverContract = web3.eth.Contract(ABI_CODE, serviceKeyResolverAddress);
const hasKey = await serviceKeyResolverContract.methods.isKeyFor(key, ein).call();
const symbol = await serviceKeyResolverContract.methods.getSymbol(key).call();
if (hasKey) {
    if (symbol.equals(serviceId)) {
	    // 키 등록되어 있음
    }
    else {
        // 키는 등록되어 있으나 제공 서비스가 아님
    }
}
else {
	// 해당키가 등록되어 있지 않음
}
```
